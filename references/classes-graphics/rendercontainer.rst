
.. _class_RenderContainer:

RenderContainer
===============

RenderContainer, as the name says,  is a container for data that is prepared to render.

It contains only getter methods and one friend class, which is :ref:`RenderPipeline<class_RenderPipeline>` . Other classes, such as :ref:`RendererBatch<class_RendererBatch>`
must use getter methods. I want to give ability to modify RenderContainers only to :ref:`RenderPipeline<class_RenderPipeline>` .

It contains some typedefs in order to make it clear what is its purpose :

.. _class_RenderContainer_typedefs:

* std::pair<int32_t, :ref:`maths::vec3<class_marmaths_vec3>` > is a ``ColorPair``
* std::pair<int32_t, :ref:`maths::vec3<class_marmaths_vec3>` > is a ``TexturePair``
* std::pair<:ref:`maths::vec3<class_marmaths_vec3>` , :ref:`ecs::LightComponent<class_LightComponent>` > is a ``LightPair``
* std::vector< :ref:`Vertex<class_Vertex>` > is a ``VertexVector``
* std::vector<uint32_t> is a ``IndicesVector``
* std::vector< :ref:`maths::mat4<class_marmaths_mat4>` > is a ``Mat4Vector``
* std::vector<ColorPair> is a ``ColorVector``
* std::vector<TexturePair> is a ``TextureVector``
* std::vector<LightPair> is a ``LightVector``
* std::vector<float> is a ``FloatVector``

Public Methods
--------------

.. _class_method_RenderContainer_reset:

+-----------------+
| void reset()    |
+-----------------+

Provides whole cleanup for container, clears whole storage.

Getters
-------

.. _class_method_RenderContainer_getVertices:

+------------------------------------------------------------------------------------------------------------+
| const :ref:`VertexVector<class_RenderContainer_typedefs>` & getVertices() const                            |
+------------------------------------------------------------------------------------------------------------+

Returns const reference to :ref:`m_vertices<class_member_RenderContainer_m_vertices>` .

.. _class_method_RenderContainer_getIndices:

+------------------------------------------------------------------------------------+
| const :ref:`IndicesVector<class_RenderContainer_typedefs>` & getIndices() const    |
+------------------------------------------------------------------------------------+

Returns const reference to :ref:`m_indices<class_member_RenderContainer_m_indices>` .

.. _class_method_RenderContainer_getTransforms:

+------------------------------------------------------------------------------------+
| const :ref:`Mat4Vector<class_RenderContainer_typedefs>` & getTransforms() const    |
+------------------------------------------------------------------------------------+

Returns const reference to :ref:`m_transforms<class_member_RenderContainer_m_transforms>` .

.. _class_method_RenderContainer_getColors:

+---------------------------------------------------------------------------------+
| const :ref:`ColorVector<class_RenderContainer_typedefs>` & getColors() const    |
+---------------------------------------------------------------------------------+

Returns const reference to :ref:`m_colors<class_member_RenderContainer_m_colors>` .

.. _class_method_RenderContainer_getTexture2D:

+--------------------------------------------------------------------------------------+
| const :ref:`TextureVector<class_RenderContainer_typedefs>` & getTexture2D() const    |
+--------------------------------------------------------------------------------------+

Returns const reference to :ref:`m_tex2D<class_member_RenderContainer_m_tex2D>` .

.. _class_method_RenderContainer_getTextureCubemap:

+-------------------------------------------------------------------------------------------+
| const :ref:`TextureVector<class_RenderContainer_typedefs>` & getTextureCubemap() const    |
+-------------------------------------------------------------------------------------------+

Returns const reference to :ref:`m_cubes<class_member_RenderContainer_m_cubes>` .

.. _class_method_RenderContainer_getLights:

+--------------------------------------------------------------------------------+
| const :ref:`LightVector<class_RenderContainer_typedefs>` & getLights() const   |
+--------------------------------------------------------------------------------+

Returns const reference to :ref:`m_lights<class_member_RenderContainer_m_lights>` .

.. _class_method_RenderContainer_getSamplerTypes:

+---------------------------------------------------------------------------------------+
| const :ref:`FloatVector<class_RenderContainer_typedefs>` & getSamplerTypes() const    |
+---------------------------------------------------------------------------------------+

Returns const reference to :ref:`m_samplerTypes<class_member_RenderContainer_m_samplerTypes>` .

.. _class_method_RenderContainer_getStride:

+--------------------------------+
| static uint32_t getStride()    |
+--------------------------------+

Returns :ref:`m_vertices<class_member_RenderContainer_m_vertices>` .

Members
-------

.. _class_member_RenderContainer_m_vertices:

+-------------------------------------------------------------------+
| :ref:`VertexVector<class_RenderContainer_typedefs>` m_vertices    |
+-------------------------------------------------------------------+

Contains all batched vertices that can be rendered.

.. _class_member_RenderContainer_m_indices:

+-------------------------------------------------------------------+
| :ref:`IndicesVector<class_RenderContainer_typedefs>` m_indices    |
+-------------------------------------------------------------------+

Contains all batched indices that can be rendered.

.. _class_member_RenderContainer_m_shapeID:

+--------------------+--------------+
| float m_shapeID    |  { 0.f }     |
+--------------------+--------------+

This is a iterator for defining shape ID for batch renderer during submitting :ref:`RenderableComponent<class_RenderableComponent>` to :ref:`RenderPipeline<class_RenderPipeline>` .

.. _class_member_RenderContainer_m_indicesMax:

+--------------------------+------------+
| uint32_t m_indicesMax    | { 0 }      |
+--------------------------+------------+

This is a helper for calculating maximum indices value for current vertices and indices. This value is used during 
submitting :ref:`RenderableComponent<class_RenderableComponent>` to :ref:`RenderPipeline<class_RenderPipeline>` .

.. _class_member_RenderContainer_m_stride:

+-----------------------------------+-----------------------+
| static const uint32_t m_stride    | { 3 + 3 + 2 + 1 }     |
+-----------------------------------+-----------------------+

This value contains information about how many floats are needed to create :ref:`Vertex<class_Vertex>` .
position - 3 floats, lightsNormal - 3 floats, textureCoordinates - 2 floats, shapeID - 1 float.

.. _class_member_RenderContainer_m_transforms:

+-------------------------------------------------------------------+
| :ref:`Mat4Vector<class_RenderContainer_typedefs>` m_transforms    |
+-------------------------------------------------------------------+

Storage for all transform matrices.

.. _class_member_RenderContainer_m_colors:

+----------------------------------------------------------------+
| :ref:`ColorVector<class_RenderContainer_typedefs>` m_colors    |
+----------------------------------------------------------------+

Storage for all colors.

.. _class_member_RenderContainer_m_tex2D:

+-----------------------------------------------------------------+
| :ref:`TextureVector<class_RenderContainer_typedefs>` m_tex2D    |
+-----------------------------------------------------------------+

Storage for all textures 2D.

.. _class_member_RenderContainer_m_cubes:

+-----------------------------------------------------------------+
| :ref:`TextureVector<class_RenderContainer_typedefs>` m_cubes    |
+-----------------------------------------------------------------+

Storage for all cubemap textures.

.. _class_member_RenderContainer_m_samplerTypes:

+----------------------------------------------------------------------+
| :ref:`FloatVector<class_RenderContainer_typedefs>` m_samplerTypes    |
+----------------------------------------------------------------------+

Vector, which defines which color / texture should be loaded into some part of batched vertices && indices.
0 for color, 1 one for texture 2D, 2 for cubemap, other values are considered as errors.

.. _class_member_RenderContainer_m_lights:

+----------------------------------------------------------------+
| :ref:`LightVector<class_RenderContainer_typedefs>` m_lights    |
+----------------------------------------------------------------+

Storage for lights position and :ref:`LightComponents<class_LightComponent>` .
