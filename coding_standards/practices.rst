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


Example of optimization
-----------------------

.. code-block:: cpp

    #include <iostream>
    using namespace std;

    int main() {
        int length;
        string greet1 = "Hello";
        string greet2 = ", World!";
        string greet3 = greet1 + greet2;

        length = greet3.size();
    }

.. code-block:: cpp

    #include <string>

    int main() {
        const std::string greet1 = "Hello";
        const std::string greet2 = ", World!";
        const auto greet3 = greet1 + greet2;
        const auto length = greet3.size();
        return length;
    }


Example of optimization #2
--------------------------

.. code-block:: cpp

    #include <iostream>

    int main() {
        int i, n, fact = 1;
        std::cout << "Enter: ";
        std::cin >> n;
        
        for(i = 1; i <= n; i++) { fact *= i; }

        std::cout << "Factorial: " << fact << std::endl; 
    }


Everything is calculated at compile-time below:

.. code-block:: cpp

    #include <iostream>

    template<typename T>
    T read_input() {
        T obj;
        std::cin >> obj;
        return obj;
    }

    constexpr int32_t factorial(int32_t value) {
        int32_t result = 1;
        while(value > 0) {
            result *= value;
            --value;
        }
        return result;
    }

    int main() {
        std::cout << "Enter: ";
        const auto n = read_input<int32_t>();
        const auto fact = factorial(n);
        std::cout << "Factorial: " << fact << std::endl; 
    }


Example of optimization #3
--------------------------

.. code-block:: cpp

    #include <vector>
    #include <limits>

    int range(std::vector<int>& values)  {
        int min = std::numeric_limits<int>::max();
        int max = std::numeric_limits<int>::min();

        for(int i = 0; i < values.size(); i++) {
            if(values[i] < min) { min = values[i]; }
            if(values[i] > max) { max = values[i]; } 
        }

        return max - min;
    }


A more cleaner way to do it:

.. code-block:: cpp

    #include <algorithm>

    template<typename Itr>
    auto range(const Itr begin, const Itr end) {
        const auto [min_elem, max_elem] = std::minmax_element(begin, end);
        return *max_elem - *min_elem;
    }

