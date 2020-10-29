Coding Standards
================

.. seealso::

    This page describes the C++ coding standards used in MAREngine. If you are going to contribute to MAREngine, please read this.


Naming conventions
------------------

How to choose name?
~~~~~~~~~~~~~~~~~~~

.. code-block:: cpp

    // namespaces can be made up of one word, only lower case letters
    namespace example {

        // all variables are starting from lower letter, any other word is starting from capital letter
        float someVariable;
        float someLongNameForVariable;

        // all functions are starting from lower letter, any other word is starting from capital letter
        void someFunction();
        void someLongNameForMethod();

        // all classes are starting from capital letter, any other word is starting from capital letter
        class SomeClass;
        class SomeOtherClass;

    }

    // examples, that I don't use and are considered as BAD
    namespace BadExample {      // change name to "example" or "bad", find any other namespace name
        namespace Bad {         // change to "bad"
            class badClass;     // change to "BadClass"
        }

        void Some_Bad_Function();   // change to someBadFunction();
        void other_bad_Function();  // change to otherBadFunction();

        int32_t __someVariable;     // change to someVariable
        float other_Example;        // change to otherExample
    }

How to name local / static / global variables?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: cpp

    int32_t localVariable;      // for local variables we don't need any prefix
    int32_t s_staticVariable;   // for static variables add s_ prefix
    int32_t g_globalVariable;   // for global variables add g_ prefix

How to name variables in class?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: cpp

    float m_member;     // private member, add m_ prefix
    float s_member;     // static member, add s_ prefix
    float p_member;     // protected member, add p_ prefix
    float member;       // public member, we don't need any prefix

Functions
---------

Follow Single-Responsibility-Principle
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`Read this <https://en.wikipedia.org/wiki/Single-responsibility_principle>`_

Define small functions inline
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Small functions are 3-5 lines long.

Lambdas
-------

Avoid [&] or [=]
~~~~~~~~~~~~~~~~

Default capture-modes can catch more than you can expect! Capture variables explicitly.

.. code-block:: cpp

    void SomeClass::foo() {
        m_member = 0; // class member
        int32_t local = 100;

        auto bad_lambda = [=]{ /* do some stuff */ };
        auto bad_lambda2 = [&]{ /* do some stuff */ };

        auto good_lambda = [&memberData = m_member, local]() {
            // do some stuff
        };

        auto good_lambda2 = [this]() {
            // do some stuff
        };

        // do something
    }

Consider capturing as const reference
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: cpp

    void foo() {
        auto someLargObject;

        auto good = [LargeConstRef = std::cref(someLargObject)]() {
            LargeConstRef.constAction();
        };

        auto goodCpp17 = [&LargeConstRef = std::as_const(someLargObject)]() { // only with C++17
            LargeConstRef.constAction();        
        };
    }

OOP
---

How classes should look like
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

* friend declarations
* private nested types
* public nested types
* constructors
* destructors
* public member functions
* public member variables
* protected member functions
* protected member variables
* private member functions
* private member variables

.. code-block:: cpp

    class SomeClass {
        friend class SomeFriendClass;
        typedef int32_t MyInt;
    
    public:
        typedef std::vector<std::pair<int32_t, float>> PairVector;

        SomeClass();
        virtual ~SomeClass();

        void public_method();

        int32_t member;

    protected:

        void protected_method();

        int32_t p_member;

    private:

        void private_method();

        int32_t m_member;
    };

Prefer in-class members initialization
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: cpp

    class SomeClass {
    public:
        SomeClass() : // old-style constructor initialization
            a(0),
            b(0.0),
        {}

    private:
        int32_t a;
        double b;
    };

It is better to it this way:

.. code-block:: cpp

    class SomeClass {
    public:
        SomeClass() = default;

    private:
        int32_t a{ 0 };
        double b{ 0.0 };
    };

Do not use virtual destructor
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Remember that move construction and move assignment are disabled if you use virtual destructor!
Use it wisely.

Namespaces
----------

Increase readability with nested namespaces
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: cpp

    // This is considered as bad
    namespace first {
        namespace second {
            class SomeClass;
        }
    }

    // This one definitely increase readability
    namespace first::second {
        class SomeClass;
    }

Header Files
------------

Forward declarations
~~~~~~~~~~~~~~~~~~~~

Prefer forward declaration in .h file, include in cpp file if possible. This can speed up compilation time.

.. code-block:: cpp

    // MyClass.h

    namespace example {
        class SomeOtherClass;
        
        class MyClass {
            void foo(SomeOtherClass* soc);
        };
    }

    // MyClass.cpp

    #include "MyClass.h"
    #include "SomeOtherClass.h"

    namespace example {
        void MyClass::foo(SomeOtherClass* soc) {
            // do stuff
        }
    }

Memory Management
-----------------

Initialize pointers with nullptr
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Do not use NULL or 0 to initialize pointers!

Never use memcpy or memset
~~~~~~~~~~~~~~~~~~~~~~~~~~

Always use copy constructors and assignment operators to copy from one object to another. Use std::copy() instead of memcpy().
Alawys use std::fill() or std::fill_n() to assign a specified value to elements of sequence, never use memset().


