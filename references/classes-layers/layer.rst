
.. _class_Layer:

Layer
=====

Layer is a abstraction class for MAREngine's workflow. This is base class for other layers, for instance :ref:`EntityLayer<class_EntityLayer>` is a derived one.
It provides virtual methods ``initialize``, ``update`` and ``close`` .

Constructors / Destructors
--------------------------

.. _class_method_Layer_constructor:

+-----------------------------------------------------+
| Layer(const char* name)                             |
+-----------------------------------------------------+

Constructors sets :ref:`p_debugName<class_member_Layer_p_debugName>` variable with ``name`` argument.

Virtual Methods
---------------

.. _class_method_Layer_initialize:

+----------------------------------------------------------+
| virtual void initialize() { }                            |
+----------------------------------------------------------+

Virtual implementation of ``initialize`` method for other layers.

.. _class_method_Layer_update:

+------------------------------------------------------+
| virtual void update() { }                            |
+------------------------------------------------------+

Virtual implementation of ``update`` method for other layers.

.. _class_method_Layer_closeLayer:

+----------------------------------------------------------+
| virtual void closeLayer() { }                            |
+----------------------------------------------------------+

Virtual implementation of ``closeLayer`` method for other layers.

Protected Members
-----------------

.. _class_member_Layer_p_debugName:

+------------------------------+-------------------------------------+
| const char* p_debugName      |   { "Default_Debug_Name" }          |
+------------------------------+-------------------------------------+

As the name says, it is a debug name for layer. Protected, because I want to all derived layers to have this member.