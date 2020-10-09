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
    foo change_foo(foo x, foo y) { return test ? move(x) : move(y); }
    foo change_foo(foo x, foo y) { if (test) return x; else return y; }

