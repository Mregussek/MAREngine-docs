
.. _class_LayerStack:

LayerStack
==========

LayerStack is just a stack for the layers. It contains ``initialize``, ``update`` and ``close`` methods, where it iterates over all layers and calls 
and its implementation of those methods.

Public Methods
--------------

+----------------------------------------------+
| void initialize()                            |
+----------------------------------------------+

Method iterates over all layers in vector and calls its ``initialize`` method.

+-----------------------------------------+
| void close()                            |
+-----------------------------------------+

Method iterates over all layers in vector and calls its ``closeLayer`` method, afterwards layer is being deleted.

+------------------------------------------+
| void update()                            |
+------------------------------------------+

Method iterates over all layers in vector and calls its ``update`` method.

+------------------------------------------------------+
| void pushLayer(:ref:`Layer<class_Layer>` * layer)    |
+------------------------------------------------------+

Method pushes ``layer`` to the stack.

+------------------------------------------------------+
| void popLayer(:ref:`Layer<class_Layer>` * layer)     |
+------------------------------------------------------+

Method pops ``layer`` from the stack.

+---------------------------------------------------------+
| void pushOverlay(:ref:`Layer<class_Layer>` * overlay)   |
+---------------------------------------------------------+

Method pushes ``overlay`` to the end of the stack.

+--------------------------------------------------------+
| void popOverlay(:ref:`Layer<class_Layer>` * overlay)   |
+--------------------------------------------------------+

Method pops ``overlay`` from the end of the stack.

Operators
---------

+--------------------------------------------------------------+
| :ref:`Layer<class_Layer>` * operator[](uint32_t index)       |
+--------------------------------------------------------------+

Method returns layer from the selected ``index``.

Members
-------

+------------------------------------------------------+
| std::vector< :ref:`Layer*<class_Layer>` > m_layers   |
+------------------------------------------------------+

Vector containing all of the layers.

+-------------------------+----------------------------+
| uint32_t m_layerInsert  |     { 0 }                  |
+-------------------------+----------------------------+

Helper for inserting overlays.

