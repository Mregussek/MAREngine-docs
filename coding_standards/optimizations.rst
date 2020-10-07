Optimizations
=============

.. seealso::

    This page describes the C++ some optimizations used in MAREngine. It makes code a bit cleaner.


Variables
---------

Stack
~~~~~

The stack is the most efficient memory space to store data in because the same range of memory addresses is reused again and again. It is almost certain that this part of the memory is mirrored in the level-1 data cache if there are no big arrays.

Static memory
~~~~~~~~~~~~~

The static memory is also used for variables declared with the static keyword, for floating point constants, string constants, array initializer lists, switch statement jump tables, and virtual function tables.
The advantage of static data is that it can be initialized to desired values before the program starts. The disadvantage is that the memory space is occupied throughout the whole program execution, even if the variable is only used in a small part of the program. This makes data caching less efficient because the memory space cannot be reused for another purpose.

Heap Allocations
~~~~~~~~~~~~~~~~

* Heap allocations are the most expensive things we
commonly do
* Deallocations are the second most expensive
* So reduce them as much as possible, ideally to zero
    * Count your allocations
* Most of the Standard containers and almost any use
of new (or smart pointers) uses the heap

Integer Operations
~~~~~~~~~~~~~~~~~~

Integer operations are generally very fast. Simple integer operations such as addition, subtraction, comparison, bit operations and shift operations take only one clock cycle on most microprocessors.
Multiplication and division take longer time. Integer multiplication takes 11 clock cycles on Pentium 4 processors, and 3 - 4 clock cycles on most other microprocessors. Integer division takes 40 - 80 clock cycles, depending on the microprocessor.

Enums
~~~~~

An enum is simply an integer in disguise. Enums are exactly as efficient as integers


Functions
---------

The function call makes the microprocessor jump to a different code address and back again. This may take up to 4 clock cycles. In most cases the microprocessor is able to overlap the call and return operations with other calculations to save time.

Avoid unnecessary functions
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Some programming textbooks recommend that every function that is longer than a few lines should be split up into multiple functions. I disagree with this rule. Splitting up a function into multiple smaller functions only makes the program less efficient. Splitting up a function just because it is long does not make the program more clear unless the function is doing multiple logically distinct tasks. A critical innermost loop should preferably be kept entirely inside one function, if possible.

Use templates instead of macros
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: cpp

    #define MAX(a,b) (a > b ? a : b) y = MAX(f(x), g(x)); // f(x) and g(x) are calculated twice

    template <typename T>
    static inline T MAX(T const& a, T const& b) {
        return a > b ? a : b;   // calculated once, when passing argument
    }


Use fastcall and vectorcall
~~~~~~~~~~~~~~~~~~~~~~~~~~~

The keyword ``__fastcall`` changes the function calling method in 32-bit mode so that the first two integer parameters are transferred in registers rather than on the stack. This can improve the speed of functions with integer parameters.
The keyword ``__vectorcall`` changes the function calling method in Windows systems for floating point and vector operands so that parameters are passed and returned in vector registers.

Make functions local
~~~~~~~~~~~~~~~~~~~~

A function that is used only within the same module (i.e. the current .cpp file) should be made local. This makes it easier for the compiler to inline the function and to optimize across function calls.
    * Add the keyword static to the function declaration. This is the simplest method, but it does not work with class member functions, where static has a different meaning.
    * Put the function or class into an anonymous namespace.


Classes
-------

Data Allignment
~~~~~~~~~~~~~~~

.. code-block:: cpp

    struct S1 {
        short int a;    // 2 bytes. first byte at 0, last byte at 1
                        // 6 unused bytes
        double b;       // 8 bytes. first byte at 8, last byte at 15
        int d;          // 4 bytes. first byte at 16, last byte at 19
                        // 4 unused bytes
    };

    struct S1 {
        double b;       // 8 bytes. first byte at 0, last byte at 7
        int d;          // 4 bytes. first byte at 8, last byte at 11
        short int a;    // 2 bytes. first byte at 12, last byte at 13
                        // 2 unused bytes
    };


This reordering has made the structure 8 bytes smaller and the array 800 bytes smaller.

Virtual member functions
~~~~~~~~~~~~~~~~~~~~~~~~

Each instance of a polymorphic class has a pointer to a table of pointers to the different versions of the virtual functions. This so-called virtual table is used for finding the right version of the virtual function at runtime.
Polymorphism is one of the main reasons why object oriented programs can be less efficient than non-object oriented programs. If you can avoid virtual functions then you can obtain most of the advantages of object oriented programming without paying the performance costs.
The time it takes to call a virtual member function is a few clock cycles more than it takes to call a non-virtual member function, provided that the function call statement always calls the same version of the virtual function. If the version changes then you may get a misprediction penalty of 10 - 20 clock cycles.

Good practices
--------------

Passing arguments
~~~~~~~~~~~~~~~~~

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
~~~~~~~~~~~~~~~~~~~~~~~

* Avoid std::move in your return it will inhibit RVO (RVO is better than a move, since nothing happens)
* Function return type must be the same as the type you are returning

.. code-block:: cpp

    foo make_foo() { foo x; return x; }
    foo change_foo(foo x) { return x; }
    foo change_foo(foo x, foo y) { return test ? move(x) : move(y); }
    foo change_foo(foo x, foo y) { if (test) return x; else return y; }

