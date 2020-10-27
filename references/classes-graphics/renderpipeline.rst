.. _class_RenderPipeline:

RenderPipeline
==============

Static Public Methods
---------------------

.. _class_method_RenderPipeline_Instance:

+----------------------------------------------------------------------+
| static :ref:`RenderPipeline<class_RenderPipeline>` & Instance()      |
+----------------------------------------------------------------------+

Returns :ref:`s_instance<class_member_RenderPipeline_s_instance>` .

Public Methods
--------------

.. _class_method_RenderPipeline_initialize:

+------------------------+
| void initialize()      |
+------------------------+

Method initializes RenderPipeline, calls :ref:`setCurrentPipeline<class_method_RenderPipeline_setCurrentPipeline>` and creates free container for incoming data.

.. _class_method_RenderPipeline_reset:

+-------------------+
| void reset()      |
+-------------------+

Method resets whole RenderPipeline. Iterates over all :ref:`m_containers<class_member_RenderPipeline_m_containers>` and clears them. Also it calls
:ref:`initialize<class_method_RenderPipeline_initialize>` method for created new available container.

.. _class_method_RenderPipeline_submitEntity:

+-------------------------------------------------------------------------+
| void submitEntity(const :ref:`ecs::Entity<class_Entity>` & entity)      |
+-------------------------------------------------------------------------+

Method submits ``entity`` to RenderPipeline. Checks its components (if it can be renderer for instance) and then pushes its data into some container.

.. _class_method_RenderPipeline_submitCamera:

+-----------------------------------------------------------------------+
| void submitCamera(:ref:`RenderCamera<class_RenderCamera>` * cam)      |
+-----------------------------------------------------------------------+

Method sets ``cam`` to :ref:`m_camera<class_member_RenderPipeline_m_camera>` member.

.. _class_method_RenderPipeline_modifyTransform:

+------------------------------------------------------------------------------------------------------------------------------------------------+
| void modifyTransform(const :ref:`ecs::TransformComponent<class_TransformComponent>` & tran, size_t containerIndex, size_t transformIndex)      |
+------------------------------------------------------------------------------------------------------------------------------------------------+

Method replaces current :ref:`TransformComponent<class_TransformComponent>` at ``containerIndex`` and ``transformIndex`` with ``tran``.

.. _class_method_RenderPipeline_modifyLight:

+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| void modifyLight(const :ref:`maths::vec3<class_marmaths_vec3>` & position, const :ref:`ecs::LightComponent<class_LightComponent>` & light, size_t containerIndex, size_t lightIndex)      |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Method replaces current :ref:`LightComponent<class_LightComponent>` at ``containerIndex`` and ``lightIndex`` with new ``position`` and ``light`` data.

.. _class_method_RenderPipeline_modifyColor:

+-------------------------------------------------------------------------------------------------------------------------------+
| void modifyColor(const :ref:`ecs::ColorComponent<class_ColorComponent>` & color, size_t containerIndex, size_t colorIndex)    |
+-------------------------------------------------------------------------------------------------------------------------------+

Method replaces current :ref:`ColorComponent<class_ColorComponent>` at ``containerIndex`` and ``transformIndex`` with new ``color``.

.. _class_method_RenderPipeline_clearStatistics:

+-----------------------------+
| void clearStatistics()      |
+-----------------------------+

Method resets statistics to its default values.

Getters
~~~~~~~

.. _class_method_RenderPipeline_getStatistics:

+--------------------------------------------------------------------------+
| :ref:`RenderStatistics<class_RendererStatistics>` & getStatistics()      |
+--------------------------------------------------------------------------+

Method returns reference to :ref:`m_statistics<class_member_RenderPipeline_m_statistics>` . 
Non-const, because we want to in GUI Editor we want to calculate some things in original variable.

.. _class_method_RenderPipeline_getContainers:

+-------------------------------------------------------------------------------------------------+
| const std::vector< :ref:`RenderContainer<class_RenderContainer>` >& getContainers() const       |
+-------------------------------------------------------------------------------------------------+

Method returns const reference to :ref:`m_containers<class_member_RenderPipeline_m_containers>` .

.. _class_method_RenderPipeline_getCamera:

+------------------------------------------------------------------------+
| const :ref:`RenderCamera<class_RenderCamera>` * getCamera() const      |
+------------------------------------------------------------------------+

Method returns const pointer to :ref:`m_camera<class_member_RenderPipeline_m_camera>` .

Setters
~~~~~~~

.. _class_method_RenderPipeline_setCurrentPipeline:

+--------------------------------+
| void setCurrentPipeline()      |
+--------------------------------+

Methos sets ``this`` RenderPipeline to :ref:`s_instance<class_member_RenderPipeline_s_instance>` .

Private Methods
---------------

.. _class_method_RenderPipeline_submitRenderable:

+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| size_t submitRenderable(const :ref:`ecs::RenderableComponent<class_RenderableComponent>` & renderable, const :ref:`ecs::TransformComponent<class_TransformComponent>` & transform)   |
+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Method submits :ref:`RenderableComponent<class_RenderableComponent>` and its :ref:`TransformComponent<class_TransformComponent>` to RenderPipeline. It pushes vertices to
container after changing its ID in order to batch render, also it increases values of indices for batch rendering and pushes it to container. Returns ``transformIndex`` that
must be assigned to entity's :ref:`RenderPipelineComponent<class_RenderPipelineComponent>` .

.. _class_method_RenderPipeline_submitColor:

+--------------------------------------------------------------------------------------------------------------+
| size_t submitColor(int32_t entityIndex, const :ref:`ecs::ColorComponent<class_ColorComponent>` & color)      |
+--------------------------------------------------------------------------------------------------------------+

Method submits :ref:`ColorComponent<class_ColorComponent>` to RenderPipeline. ``entityIndex`` is a value returned by :ref:`submitRenderable<class_method_RenderPipeline_submitRenderable>` .
It also pushes 0 to sampler types, which means we have submitted color.  Returns ``colorIndex`` that must be assigned 
to entity's :ref:`RenderPipelineComponent<class_RenderPipelineComponent>` .

.. _class_method_RenderPipeline_submitTexture2D:

+----------------------------------------------------------------------------------------------------------------------------+
| size_t submitTexture2D(int32_t entityIndex, const :ref:`ecs::Texture2DComponent<class_Texture2DComponent>` & texture)      |
+----------------------------------------------------------------------------------------------------------------------------+

Method submits :ref:`Texture2DComponent<class_Texture2DComponent>` to RenderPipeline. ``entityIndex`` is a value returned by :ref:`submitRenderable<class_method_RenderPipeline_submitRenderable>` .
It also pushes 1 to sampler types, which means we have submitted texture 2D. Returns ``colorIndex`` that must be assigned 
to entity's :ref:`RenderPipelineComponent<class_RenderPipelineComponent>` .

.. _class_method_RenderPipeline_submitCubemap:

+------------------------------------------------------------------------------------------------------------------------------------+
| size_t submitCubemap(int32_t entityIndex, const :ref:`ecs::TextureCubemapComponent<class_TextureCubemapComponent>` & cubemap)      |
+------------------------------------------------------------------------------------------------------------------------------------+

Method submits :ref:`TextureCubemapComponent<class_TextureCubemapComponent>` to RenderPipeline. ``entityIndex`` is a value returned 
by :ref:`submitRenderable<class_method_RenderPipeline_submitRenderable>` . It also pushes 0 to sampler types, which means we have submitted color.
Returns ``colorIndex`` that must be assigned to entity's :ref:`RenderPipelineComponent<class_RenderPipelineComponent>` .

.. _class_method_RenderPipeline_submitLight:

+---------------------------------------------------------------------------------------------------------------------------------------------------+
| size_t submitLight(const :ref:`maths::vec3<class_marmaths_vec3>` & position, const :ref:`ecs::LightComponent<class_LightComponent>` & light)      |
+---------------------------------------------------------------------------------------------------------------------------------------------------+

Method submits :ref:`LightComponent<class_LightComponent>` and its ``position`` to RenderPipeline. 
Returns ``lightIndex`` that must be assigned to entity's :ref:`RenderPipelineComponent<class_RenderPipelineComponent>` .

Setters
~~~~~~~

.. _class_method_RenderPipeline_setAvailableContainerRenderable:

+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| void setAvailableContainerRenderable(:ref:`ecs::RenderPipelineComponent<class_RenderPipelineComponent>` & rpc, size_t verticesToPush, size_t indicesToPush)      |
+------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Method is looking for available container for rendering data and saves this information to :ref:`m_availableContainerIndex<class_member_RenderPipeline_m_availableContainerIndex>` .
``rpc`` is entity's :ref:`RenderPipelineComponent<class_RenderPipelineComponent>` , ``verticesToPush`` is a number of vertices that is going to be pushed during 
next submit, ``indicesToPush`` is the same but for indices.

.. _class_method_RenderPipeline_setAvailableContainerLight:

+----------------------------------------------------------------------------------------------------------------+
| void setAvailableContainerLight(:ref:`ecs::RenderPipelineComponent<class_RenderPipelineComponent>` & rpc)      |
+----------------------------------------------------------------------------------------------------------------+

Method is looking for available container for light data and saves this information to :ref:`m_availableContainerIndex<class_member_RenderPipeline_m_availableContainerIndex>` .
``rpc`` is entity's :ref:`RenderPipelineComponent<class_RenderPipelineComponent>`

Static Members
--------------

.. _class_member_RenderPipeline_s_instance:

+----------------------------------------------------------------------+
| static :ref:`RenderPipeline<class_RenderPipeline>` * s_instance      |
+----------------------------------------------------------------------+

Because we can have multiple RenderPipelines we want to have access to them from any other place in MAREngine. This is why this variable is static, its value is set to ``this``.

Members
-------

.. _class_member_RenderPipeline_m_statistics:

+---------------------------------------------------------------------+
| :ref:`RenderStatistics<class_RendererStatistics>` m_statistics      |
+---------------------------------------------------------------------+

Member that contains information about RenderPipeline's draw calls, count of vertices, etc...

.. _class_member_RenderPipeline_m_containers:

+--------------------------------------------------------------------------------+
| std::vector< :ref:`RenderContainer<class_RenderContainer>` > m_containers      |
+--------------------------------------------------------------------------------+

Vector of containers, to which data can be pushes.

.. _class_member_RenderPipeline_m_availableContainerIndex:

+--------------------------------------+-------------+
| size_t m_availableContainerIndex     |  { 0 }      |
+--------------------------------------+-------------+

Index of container, to which RenderPipeline can push data.

.. _class_member_RenderPipeline_m_camera:

+--------------------------------------------------------+-------------+
| :ref:`RenderCamera<class_RenderCamera>` * m_camera     | { nullptr } |
+--------------------------------------------------------+-------------+

Pointer to some RenderCamera instance, as we don't need to copy it.