
.. _class_MeshCreator:

MeshCreator
===========

MeshCreator is a class, that can fill :ref:`RenderableComponent<class_RenderableComponent>` with polygons (vertices, indices and its name). 

It has 4 nested structures, which are basic types that MAREngine can render, also it has :ref:`loadOBJ<class_method_MeshCreator_loadOBJ>` which
can get your external file loaded.

Nested Structures
-----------------

.. _class_MeshCreator_Cube:

Cube
~~~~

Static Methods
``````````````

.. _class_MeshCreator_Cube_getID:

+-----------------------------------------+
| static std::string getID()              |
+-----------------------------------------+

Returns "Cube".

.. _class_MeshCreator_Cube_getVertices:

+------------------------------------------------------------------------------+
| static std::vector< :ref:`Vertex<class_Vertex>` > getVertices()              |
+------------------------------------------------------------------------------+

Returns vertices with which MAREngine can render Cube.

.. _class_MeshCreator_Cube_getIndices:

+--------------------------------------------------------+
| static std::vector<uint32_t> getIndices()              |
+--------------------------------------------------------+

Returns indices with which MAREngine can render Cube.

.. _class_MeshCreator_Pyramid:

Pyramid
~~~~~~~

Static Methods
``````````````

.. _class_MeshCreator_Pyramid_getID:

+-----------------------------------------+
| static std::string getID()              |
+-----------------------------------------+

Returns "Pyramid".

.. _class_MeshCreator_Pyramid_getVertices:

+------------------------------------------------------------------------------+
| static std::vector< :ref:`Vertex<class_Vertex>` > getVertices()              |
+------------------------------------------------------------------------------+

Returns vertices with which MAREngine can render Pyramid.

.. _class_MeshCreator_Pyramid_getIndices:

+--------------------------------------------------------+
| static std::vector<uint32_t> getIndices()              |
+--------------------------------------------------------+

Returns indices with which MAREngine can render Pyramid.

.. _class_MeshCreator_Wall:

Wall
~~~~

Static Methods
``````````````

.. _class_MeshCreator_Wall_getID:

+-----------------------------------------+
| static std::string getID()              |
+-----------------------------------------+

Returns "Wall".

.. _class_MeshCreator_Wall_getVertices:

+------------------------------------------------------------------------------+
| static std::vector< :ref:`Vertex<class_Vertex>` > getVertices()              |
+------------------------------------------------------------------------------+

Returns vertices with which MAREngine can render Wall.

.. _class_MeshCreator_Wall_getIndices:

+--------------------------------------------------------+
| static std::vector<uint32_t> getIndices()              |
+--------------------------------------------------------+

Returns indices with which MAREngine can render Wall.

.. _class_MeshCreator_Surface:

Surface
~~~~~~~

Static Methods
``````````````

.. _class_MeshCreator_Surface_getID:

+-----------------------------------------+
| static std::string getID()              |
+-----------------------------------------+

Returns "Surface".

.. _class_MeshCreator_Surface_getVertices:

+------------------------------------------------------------------------------+
| static std::vector< :ref:`Vertex<class_Vertex>` > getVertices()              |
+------------------------------------------------------------------------------+

Returns vertices with which MAREngine can render Surface.

.. _class_MeshCreator_Surface_getIndices:

+--------------------------------------------------------+
| static std::vector<uint32_t> getIndices()              |
+--------------------------------------------------------+

Returns indices with which MAREngine can render Surface.

Static Public Methods
---------------------

.. _class_method_MeshCreator_loadOBJ:

+---------------------------------------------------------------------------------------------------------------------------------------------------+
| static void loadOBJ(std::string filename, std::string path, const :ref:`ecs::EntityCollection<class_EntityCollection>` & collection)              |
+---------------------------------------------------------------------------------------------------------------------------------------------------+

Method loads external .obj file from given ``path`` into ``collection``, which is :ref:`EntityCollection<class_EntityCollection>` instance. 
``filename`` argument is passed only for  assigning :ref:`TagComponent<class_TagComponent>` and :ref:`RenderableComponent's<class_RenderableComponent>` ID variable.