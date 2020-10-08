Coding Standards
================

.. seealso::

    This page describes the C++ coding standards in MAREngine.

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
        member = 0; // class member
        int32_t local = 100;

        auto lambda = [&memberData = member, local]() {
            // do some stuff
        };

        auto second_lambda = [this]() {
            // do some stuff
        };

        lambda();
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


