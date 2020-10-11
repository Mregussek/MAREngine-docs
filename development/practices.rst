Good Practices
==============

.. seealso::

    This page describes the C++ good practices used in MAREngine.


Construction Separate From Assignment
-------------------------------------

.. code-block:: cpp

    std::string str;
    // do some stuff
    str = "Hello World";
    // work with str

Faster solution:

.. code-block:: cpp

    // do some stuff
    const std::string str = "Hello World";
    // work with str

Raw Loops
---------

.. code-block:: cpp

    void process_data(const std::vector<double>& values) {
        bool in_range = true;
        for(const auto& v : values) {
            if(v < 5.0 || v > 100.0) {
                in_range = false;
                break;
            }
        }

        if(in_range) { process_more(values); }
    }

Much cleaner way to do it:

.. code-block:: cpp

    void process_data(const std::vector<double>& values) {
        const auto in_range = [](const double d) {
            return d >= 5.0 && d <= 100.0;
        }

        const bool all_in_range = std::all_of(values.begin(), values.end(), in_range); // we can read it in one sentence

        if(all_in_range) { process_more(values); }
    }

Non-Cannonical Operators
------------------------

.. code-block:: cpp

    struct Vec2 {
        int32_t x; int32_t y;

        bool operator==(Vec2& rhs) {
            return x == rhs.x && y == rhs.y;
        }
    };

Optimized way to do == operator:

.. code-block:: cpp

    bool operator==(const Vec2& rhs) const { 
        return x == rhs.x && y == rhs.y;
    }

Slowpatch removal
-----------------

Avoid this:

.. code-block:: cpp

    if(checkForErrorA()) { handleErrorA(); }
    else if(checkForErrorB()) { handleErrorB(); }
    else if(checkForErrorC()) { handleErrorC(); }
    else { doSomething(); }

Aim for this:

.. code-block:: cpp

    int64_t errorFlags;

    if(!errorFlags) { doSomething(); }
    else { handleError(); }

Use IIFE
--------

.. code-block:: cpp

    const int32_t i = std::rand();
    std::string s;
    switch(i % 2) {
    case 0: 
        s = "mod 0"; 
        break;
    case 1: 
        s = "mod 1"; 
        break;
    case 2: 
        s = "mod 2"; 
        break;
    }

The IIFE acronym stands for “Immediately-invoked function expression”. It is ~31% more efficient than example above.

.. code-block:: cpp

    const int32_t i = std::rand();
    const std::string s = [i]() {
        switch(i % 2) {
        case 0: 
            return "mod 0"; 
        case 1: 
            return "mod 1"; 
        case 2: 
            return "mod 2"; 
        }
    };


Prefer templates to branches
----------------------------

Branching approach:

.. code-block:: cpp

    enum class Side { Buy, Sell };

    void run(Side side) {
        const float orderPrice = CalcPrice(side, fairValue, credit);
        checkRiskLimit(side, orderPrice);
        sendOrder(side, orderPrice);
    }

    float calcPrice(Side side, float value, float credit) {
        return side == Side::Buy ? value - credit : value + credit;
    }

Templated approach:

.. code-block:: cpp

    template<Side T>
    void Strategy<T>::run() {
        const float orderPrice = CalcPrice(side, fairValue, credit);
        checkRiskLimit(side, orderPrice);
        sendOrder(side, orderPrice);
    }

    template<>
    float Strategy<Side::Buy>::calcPrice(float value, float credit) {
        return value - credit;
    }

    template<>
    float Strategy<Side::Sell>::calcPrice(float value, float credit) {
        return value + credit;
    }

But don't remove every if, because it will end up to slow down the code.

Prefer return std::unique_ptr<>
-------------------------------

std::shared_ptr<> is a huge beast, try to avoid it every time.

.. code-block:: cpp

    template<typename T> std::unique_ptr<BaseClass> d_factory() {
        return std::make_unique<DerivedClass<T>>();
    }

1.30s compile, 30k exe, 149796k compile RAM

.. code-block:: cpp

    template<typename T> std::shared_ptr<BaseClass> d_factory() {
        return std::make_shared<DerivedClass<T>>();
    }

2.24s compile, 70k exe, 164808k compile RAM

.. code-block:: cpp

    template<typename T> std::shared_ptr<BaseClass> d_factory() {
        return std::make_unique<DerivedClass<T>>();
    }

2.43s compile, 91k exe, 190044k compile RAM

Avoid std::endl
---------------

.. code-block:: cpp

    void print(std::ostream& os, const std::string& str) {
        // Those 2 lines below are exactly the same!
        os << str << std::endl; 
        os << str << "\n" << std::flush;

        // Use just "\n"
        os << str << "\n";
    }

You can expect that flush can cost you at least 9x overhead in your IO.

Passing arguments
-----------------

* Pass simple things by value
    * Built in types (size_t, uint32_t, float)
    * Maybe your simple types (16 bytes)
    * But remember, you are making a copy
* Pass things by value when you need to modify a copy
    * There is no point in taking a const& parameter, if you are immediately going to make a copy anyway
* Do not pass object by non-const reference, it makes it more clear for the reader what is happening if you use pointer.

Examples:

.. code-block:: cpp

    std::vector<int32_t> load_numbers(std::vector<int32_t>&& v) {
        // no constructor! size 0, capacity 1000
        for(int32_t i = 1; i <= 1000; i++) { v.push_back(i); } // 0 allocations!
        return v; // copy constructor
    }

    int main() {
        std::vector<int32_t> v;
        for(size_t i = 0; i < 9; i++) { // size 1000, capacity 1000
            v.clear();                  // size 0   , capacity 1000
            v = load_numbers(std::move(v)); // move assignment
        }
    }

Return practises (GOOD)
-----------------------

* Avoid std::move in your return it will inhibit RVO (RVO is better than a move, since nothing happens)
* Function return type must be the same as the type you are returning

.. code-block:: cpp

    foo make_foo() { foo x; return x; }
    foo change_foo(foo x) { return x; }
    foo change_foo(foo x, foo y) { return test ? std::move(x) : std::move(y); }
    foo change_foo(foo x, foo y) { if (test) return x; else return y; }

Avoid copying if it is not neccessary
-------------------------------------

.. code-block:: cpp

    struct S {
        S(std::string arg_s) : m_s(arg_s) {}
        std::string m_s;
    }

    int main() {
        for(size_t i = 0; i < 100000; i++) {
            std::string s = std::string("short string: ") + "b";
            S o(s);
        }
    }

Example below is more efficient:

.. code-block:: cpp

    struct S {
        S(std::string arg_s) : m_s(std::move(arg_s)) {}
        std::string m_s;
    }

    int main() {
        for(size_t i = 0; i < 100000; i++) {
            S o(std::string("short string: ") + "b");
        }
    }