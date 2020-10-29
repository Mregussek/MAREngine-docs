
.. _class_EntityLayer:

EntityLayer
===========

EntityLayer is a layer containing its :ref:`SceneManager<class_SceneManager>` , :ref:`RenderPipeline<class_RenderPipeline>` and :ref:`RendererBatch<class_RendererBatch>` .
It can initialize renderers and scene, and then updates the whole scene during one frame.

Overrided Methods
-----------------

.. _class_method_EntityLayer_initialize:

+------------------------------------------------------+
| void initialize() override                           |
+------------------------------------------------------+

Method is responsible for initialize its all members.

.. _class_method_EntityLayer_update:

+---------------------------------------------------+
| void update() override                            |
+---------------------------------------------------+

Method firstly updates SceneManager, then data which RenderPipeline gets from the SceneManager is pushed to RendererBatch for draw call.

.. _class_method_EntityLayer_closeLayer:

+-------------------------------------------------------+
| void closeLayer() override                            |
+-------------------------------------------------------+

Method is closing all of its components.

Public Methods
--------------

.. _class_method_EntityLayer_passSceneToManager:

+-------------------------------------------------------------------------------+
| void passSceneToManager(:ref:`ecs::Scene<class_Scene>` * scene)               |
+-------------------------------------------------------------------------------+

Method sets a ``scene``, which must be managed in SceneManager.

.. _class_method_EntityLayer_getSceneManager:

+--------------------------------------------------------------------------------------+
| :ref:`ecs::SceneManager<class_SceneManager>` * getSceneManager()                     |
+--------------------------------------------------------------------------------------+

Method returns pointer to SceneManager.

Members
-------

.. _class_member_EntityLayer_m_sceneManager:

+------------------------------------------------------------------+
| :ref:`ecs::SceneManager<class_SceneManager>` m_sceneManager      |
+------------------------------------------------------------------+

Manager for the scene.

.. _class_member_EntityLayer_m_renderer:

+---------------------------------------------------------------------+
| :ref:`graphics::RendererBatch<class_RendererBatch>` m_renderer      |
+---------------------------------------------------------------------+

Renderer for scene, that SceneManager is providing.

.. _class_member_EntityLayer_m_renderPipeline:

+---------------------------------------------------------------------------+
| :ref:`graphics::RenderPipeline<class_RenderPipeline>` m_renderPipeline    |
+---------------------------------------------------------------------------+

Pipeline for the renderer, contains all the prepared data for rendering.