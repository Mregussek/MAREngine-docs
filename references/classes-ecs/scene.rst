.. _class_Scene:

Scene
=====

Scene has two friend classes: 

* :ref:`mar::ecs::Entity<class_Entity>`
* :ref:`mar::ecs::EntityCollection<class_EntityCollection>`

Constructors / Destructors
--------------------------

.. _class_constructor_Scene_stdstring:

+----------------------------------------+
| Scene(std::string name)                |
+----------------------------------------+

Static Public Methods
---------------------

.. _class_method_Scene_createEmptyScene:

+------------------------------------------------------------------------------------------------+
| static :ref:`mar::ecs::Scene<class_Scene>` * createEmptyScene(std::string name)                |
+------------------------------------------------------------------------------------------------+

createEmptyScene description

Public Methods
--------------

.. _class_method_Scene_shutdown:

+--------------------------------+
| void shutdown()                |
+--------------------------------+

shutdown description

.. _class_method_Scene_createEntity:

+-----------------------------------------------------------------------------+
| const :ref:`mar::ecs::Entity<class_Entity>` & createEntity()                |
+-----------------------------------------------------------------------------+

createEntity

.. _class_method_Scene_destroyEntity:

+--------------------------------------------------+
| void destroyEntity(int32_t index)                |
+--------------------------------------------------+

destroyEntity

.. _class_method_Scene_createCollection:

+-----------------------------------------------------------------------------------------------------+
| const :ref:`mar::ecs::EntityCollection<class_EntityCollection>` & createCollection()                |
+-----------------------------------------------------------------------------------------------------+

createCollection

.. _class_method_Scene_destroyCollection:

+------------------------------------------------------------------------------------------------+
| void destroyCollection(int32_t index)                                                          |
+------------------------------------------------------------------------------------------------+

destroyCollection

.. _class_method_Scene_destroyEntityAtCollection:

+------------------------------------------------------------------------------------------------+
| void destroyEntityAtCollection(int32_t collection_index, int32_t entity_index)                 |
+------------------------------------------------------------------------------------------------+

destroyEntityAtCollection

Setters
-------

.. _class_method_Scene_setName:

+------------------------------------------------+
| void setName(std::string name)                 |
+------------------------------------------------+

setName

.. _class_method_Scene_setBackground:

+---------------------------------------------------------------------+
| void setBackground( :ref:`maths::vec3<class_marmaths_vec3>` v)      |
+---------------------------------------------------------------------+

setBackground

Getters
-------

.. _class_method_Scene_getName:

+-----------------------------------------------+
| const std::string& getName() const            |
+-----------------------------------------------+

getName

.. _class_method_Scene_getBackground:

+----------------------------------------------------------------------+
| :ref:`maths::vec3<class_marmaths_vec3>` & getBackground()            |
+----------------------------------------------------------------------+

getBackground

.. _class_method_Scene_getEntities:

+--------------------------------------------------------------------------------------------+
| const std::vector< :ref:`mar::ecs::Entity<class_Entity>` >& getEntities() const            |
+--------------------------------------------------------------------------------------------+

getEntities

.. _class_method_Scene_getCollections:

+-------------------------------------------------------------------------------------------------------------------+
| const std::vector< :ref:`mar::ecs::EntityCollection<class_EntityCollection>` >& getCollections() const            |
+-------------------------------------------------------------------------------------------------------------------+

getCollections

.. _class_method_Scene_getView:

+------------------------------------------------+
| template<typename T> auto getView()            |
+------------------------------------------------+

getView

.. _class_method_Scene_getComponent:

+-----------------------------------------------------------------------------------------------+
| template<typename T> T& getComponent(:ref:`entt::entity<class_entt_entity>` entity)           |
+-----------------------------------------------------------------------------------------------+

getComponent

Members
-------

.. _class_member_Scene_m_name:

+------------------------------------+-------------------------+
| std::string m_name                 | ``"Empty Scene"``       |
+------------------------------------+-------------------------+

m_name description

.. _class_member_Scene_m_sceneRegistry:

+-------------------------------------------------------------------+
| :ref:`SceneRegistry<class_SceneRegistry>` m_sceneRegistry         |
+-------------------------------------------------------------------+

m_sceneRegistry description

.. _class_member_Scene_m_container:

+-----------------------------------------------------------------------+
| :ref:`EntityContainer<class_EntityContainer>` m_container             |
+-----------------------------------------------------------------------+

m_container description

.. _class_member_Scene_m_sceneCamera:

+----------------------------------------------------------------------------+
| :ref:`graphics::RenderCamera<class_RenderCamera>` m_sceneCamera            |
+----------------------------------------------------------------------------+

m_sceneCamera description

.. _class_member_Scene_m_backgroundColor:

+-----------------------------------------------------------------+-----------------------------------------+
| :ref:`maths::vec3<class_marmaths_vec3>` m_backgroundColor       | ``{ 0.22f, 0.69f, 0.87f }``             |
+-----------------------------------------------------------------+-----------------------------------------+

m_backgroundColor description
