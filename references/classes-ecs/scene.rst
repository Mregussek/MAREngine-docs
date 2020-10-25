.. _class_Scene:

Scene
=====

Scene is some kind of game itself. It has information about all entities and collections, can create all new entities and destroy them.

Scene has two friend classes: 

* :ref:`mar::ecs::Entity<class_Entity>`
* :ref:`mar::ecs::EntityCollection<class_EntityCollection>`

Constructors / Destructors
--------------------------

.. _class_constructor_Scene_stdstring:

+----------------------------------------+
| Scene(std::string name)                |
+----------------------------------------+

It is default constructor for Scene class, it assigns scene's name and creates new :ref:`SceneRegistry<class_SceneRegistry>` .

Static Public Methods
---------------------

.. _class_method_Scene_createEmptyScene:

+------------------------------------------------------------------------------------------------+
| static :ref:`mar::ecs::Scene<class_Scene>` * createEmptyScene(std::string name)                |
+------------------------------------------------------------------------------------------------+

Method for creating empty scene. Used, when new project, new game is being created. ``name`` argument is a new scene's name.

Public Methods
--------------

.. _class_method_Scene_shutdown:

+--------------------------------+
| void shutdown()                |
+--------------------------------+

Method is responsible for whole cleanup. It destroys all entities, all collections and registry itself.

.. _class_method_Scene_createEntity:

+-----------------------------------------------------------------------------+
| const :ref:`mar::ecs::Entity<class_Entity>` & createEntity()                |
+-----------------------------------------------------------------------------+

Method's responsibility is to create new :ref:`mar::ecs::Entity<class_Entity>` instance and attach default components to it, which are 
:ref:`TagComponent<class_TagComponent>`, :ref:`TransformComponent<class_TransformComponent>` and :ref:`EngineOnlyComponents<ecs_EngineOnlyComponent>`.

.. _class_method_Scene_destroyEntity:

+--------------------------------------------------+
| void destroyEntity(int32_t index)                |
+--------------------------------------------------+

To be refactored...

.. _class_method_Scene_createCollection:

+-----------------------------------------------------------------------------------------------------+
| const :ref:`mar::ecs::EntityCollection<class_EntityCollection>` & createCollection()                |
+-----------------------------------------------------------------------------------------------------+

Method's responsibility is to create new :ref:`mar::ecs::EntityCollection<class_EntityCollection>` instance and attach default components to it, which are
:ref:`TagComponent<class_TagComponent>`, :ref:`TransformComponent<class_TransformComponent>` and :ref:`EntityCollectionComponent><class_EntityCollectionComponent>`.

.. _class_method_Scene_destroyCollection:

+------------------------------------------------------------------------------------------------+
| void destroyCollection(int32_t index)                                                          |
+------------------------------------------------------------------------------------------------+

To be refactored...

.. _class_method_Scene_destroyEntityAtCollection:

+------------------------------------------------------------------------------------------------+
| void destroyEntityAtCollection(int32_t collection_index, int32_t entity_index)                 |
+------------------------------------------------------------------------------------------------+

To be refactored...

Setters
-------

.. _class_method_Scene_setName:

+------------------------------------------------+
| void setName(std::string name)                 |
+------------------------------------------------+

Method sets new scene name. Pass as a argument new name.

.. _class_method_Scene_setBackground:

+---------------------------------------------------------------------+
| void setBackground( :ref:`maths::vec3<class_marmaths_vec3>` v)      |
+---------------------------------------------------------------------+

Method sets new background color for scene. Pass as a argument new color.

Getters
-------

.. _class_method_Scene_getName:

+-----------------------------------------------+
| const std::string& getName() const            |
+-----------------------------------------------+

Method returns const reference to name. We don't want it to be modified with any other way than :ref:`setName<class_method_Scene_setName>` method.

.. _class_method_Scene_getBackground:

+----------------------------------------------------------------------+
| :ref:`maths::vec3<class_marmaths_vec3>` & getBackground()            |
+----------------------------------------------------------------------+

Method returns reference to background color. Non-const reference, because during editor mode we want to have ability to change its values with sliders.
I think making copy and assigning it again is unnecessary.

.. _class_method_Scene_getEntities:

+--------------------------------------------------------------------------------------------+
| const std::vector< :ref:`mar::ecs::Entity<class_Entity>` >& getEntities() const            |
+--------------------------------------------------------------------------------------------+

Method returns const reference to vector of all entities, so that we can iterate every entity in our game.

.. _class_method_Scene_getCollections:

+-------------------------------------------------------------------------------------------------------------------+
| const std::vector< :ref:`mar::ecs::EntityCollection<class_EntityCollection>` >& getCollections() const            |
+-------------------------------------------------------------------------------------------------------------------+

Method returns const reference to vector of all collections, so that we can iterate every collection in our game.

.. _class_method_Scene_getView:

+------------------------------------------------+
| template<typename T> auto getView()            |
+------------------------------------------------+

I encourage you to read about :ref:`entt::view<class_entt_view>`, because it is the type returned from this method. We can iterate over all entities,
that contains ``T`` component.

.. _class_method_Scene_getComponent:

+-----------------------------------------------------------------------------------------------+
| template<typename T> T& getComponent(:ref:`entt::entity<class_entt_entity>` entity)           |
+-----------------------------------------------------------------------------------------------+

In order to iterate over entities in view, I have created method for passing :ref:`entt::entity<class_entt_entity>` as a argument, so that we can 
get ``T`` component.

Members
-------

.. _class_member_Scene_m_name:

+------------------------------------+-------------------------+
| std::string m_name                 | ``"Empty Scene"``       |
+------------------------------------+-------------------------+

m_name is a scene name variable.

.. _class_member_Scene_m_sceneRegistry:

+-------------------------------------------------------------------+
| :ref:`SceneRegistry<class_SceneRegistry>` m_sceneRegistry         |
+-------------------------------------------------------------------+

m_sceneRegistry is a core for whole scene. I encourage you to read about SceneRegistry :ref:`here<class_SceneRegistry>` and :ref:`here<class_entt_registry>`.

.. _class_member_Scene_m_container:

+-----------------------------------------------------------------------+
| :ref:`EntityContainer<class_EntityContainer>` m_container             |
+-----------------------------------------------------------------------+

m_container is container for all stored entities and collections in scene. You can read about it :ref:`here<class_EntityContainer>`.

.. _class_member_Scene_m_sceneCamera:

+----------------------------------------------------------------------------+
| :ref:`graphics::RenderCamera<class_RenderCamera>` m_sceneCamera            |
+----------------------------------------------------------------------------+

m_sceneCamera is a game camera for the scene.

.. _class_member_Scene_m_backgroundColor:

+-----------------------------------------------------------------+-----------------------------------------+
| :ref:`maths::vec3<class_marmaths_vec3>` m_backgroundColor       | ``{ 0.22f, 0.69f, 0.87f }``             |
+-----------------------------------------------------------------+-----------------------------------------+

m_backgroundColor is a background color for scene.
