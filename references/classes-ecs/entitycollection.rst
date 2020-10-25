.. _class_EntityCollection:

EntityCollection
================

EntityCollection is a collection of entities. This is class written specially for having several entities that are depedent om collection parameters (for instance
:ref:`TransformComponent<class_TransformComponent>` , we want to have impact on every entities position, rotation and other. Or let's say we want to create one giant Entity from other entities).

.. _attention_Tag_Transform_DefaultComponents_EntityCollection:

.. attention::

    By default every entity should have its :ref:`TagComponent<class_TagComponent>` and :ref:`TransformComponent<class_TransformComponent>`! So there is no need to check if
    Entity has those components attached! Luck of them is considered as a huge error!

EntityCollection has one friend class:

* :ref:`mar::ecs::Scene<class_Scene>`

Constructors / Descructors
--------------------------

.. _class_constructor_EntityCollection_scene_registry:

+-----------------------------------------------+
| EntityCollection(SceneRegistry* scene)        |
+-----------------------------------------------+

This is default constructor for :ref:`EntityCollection class<class_EntityCollection>`, because we need to initialize :ref:`m_scene member<class_member_EntityCollection_m_scene>`! 
If :ref:`m_scene member<class_member_EntityCollection_m_scene>` will stay as nullptr value, EntityCollection instance will immedietaly crash. During this constructor call collection is created.


Public Methods
--------------

.. _class_method_EntityCollection_destroyYourself:

+-----------------------------------------+
| void destroyYourself() const            |
+-----------------------------------------+

Method destroys EntityCollection. It iterates through all entities that are in this collection and destroys them. Instance is not valid anymore. 
Marked const, as it does not modify EntityCollection instance.

.. _class_method_EntityCollection_isValid:

+-----------------------------------------------+
| const bool isValid() const                    |
+-----------------------------------------------+

Method checks, if current EntityCollection is valid (valid means, if collection is created). Marked const, as it does not modify EntityCollection instance.

.. _class_method_EntityCollection_createEntity:

+---------------------------------------------------------------------------------------------------------------------------------+
| const :ref:`Entity<class_Entity>` & createEntity() const                                                                        |
+---------------------------------------------------------------------------------------------------------------------------------+

Method creates :ref:`Entity<class_Entity>` and puts it into this collection. By default it adds :ref:`TagComponent<class_TagComponent>` and
:ref:`TransformComponent<class_TransformComponent>` to created Entity instance. Returns it as a const reference. Marked const, as it does not modify EntityCollection instance.

.. _class_method_EntityCollection_destroyEntity:

+---------------------------------------------------------------------------------------------------------------------------------+
| void destroyEntity(int32_t entity_index) const                                                                                  |
+---------------------------------------------------------------------------------------------------------------------------------+

To be refactored...

.. _class_method_EntityCollection_getEntities:

+---------------------------------------------------------------------------------------------------------------------------------+
| const std::vector< :ref:`Entity<class_Entity>` >>& getEntities() const                                                          |
+---------------------------------------------------------------------------------------------------------------------------------+

Method returns const vector of all entities, that are in ``this`` collection. You cannot just push back entity to that vector,
you need to use :ref:`createEntity<class_method_EntityCollection_createEntity>` in order to add Entity to collection. 
Marked const, as it does not modify EntityCollection instance.

.. _class_method_EntityCollection_hasComponent:

+---------------------------------------------------------+
| template<typename T> bool hasComponent() const          |
+---------------------------------------------------------+

Method returns true, if collection has component attached. It is templated method, where ``T`` stands for component. Marked const, as it does not modify EntityCollection instance.

.. _class_method_EntityCollection_addComponent:

+-----------------------------------------------------------------------------------+
| template<typename T, typename... Args> T& addComponent(Args&&... args) const      |
+-----------------------------------------------------------------------------------+

Method adds component to EntityCollection object. ``T`` stands for selected component. Parameter pack ``Args`` stands for arguments with which component can be created, but practically always
component is created without any addinational arguments. Method returns reference to newly created component. Method marked const, as it does not modify Entity instance.

.. _class_method_EntityCollection_getComponent:

+-----------------------------------------------------------------------------------------------------------+
| template<typename T> T& getComponent() const                                                              |
+-----------------------------------------------------------------------------------------------------------+

Method returns reference to component attached to EntityCollection. Method does not check, if component is already attached, make sure to check it 
with :ref:`hasComponent<class_method_EntityCollection_hasComponent>` method! Exception is Tag and Transform, :ref:`check this<attention_Tag_Transform_DefaultComponents_EntityCollection>` .
Marked const, as it does not modify Entity instance.

.. _class_method_EntityCollection_replaceComponent:

+--------------------------------------------------------------------------------------------------------------------------------+
| template<typename T> T& replaceComponent(const :ref:`EntityCollection<class_EntityCollection>` & other) const                  |
+--------------------------------------------------------------------------------------------------------------------------------+

Method replaces current component of ``this`` collection instance with component of ``other`` collection. Method returns reference to newly created component.
``T`` stands for selected component. Marked const, as it does not modify EntityCollection instance.

.. _class_method_EntityCollection_removeComponent:

+-------------------------------------------------------------------------------------+
| template<typename T> void removeComponent() const                                   |
+-------------------------------------------------------------------------------------+

Method removes component from current EntityCollection. ``T`` stands for component to delete. Marked const, as it does not modify EntityCollection instance.

Operators
---------

.. _class_operator_EntityCollection_bool:

+-----------------------------------------------------------------------------------------------------------+
| operator const bool() const                                                                               |
+-----------------------------------------------------------------------------------------------------------+

Operator calls :ref:`isValid<class_method_EntityCollection_isValid>`  and returns its result.

Members
-------

.. _class_member_EntityCollection_m_collectionHandle:

+----------------------------------------------------------------+-------------------------+
| :ref:`entt::entity<class_entt_entity>` m_collectionHandle      | ``entt::null``          |
+----------------------------------------------------------------+-------------------------+

``m_collectionHandle`` is unique ID for this EntityCollection instance. By default is ``entt::null``, which stands for not valid collection.

.. _class_member_EntityCollection_m_scene:

+--------------------------------------------------------------------+-------------------------+
| :ref:`SceneRegistry*<class_SceneRegistry>` m_scene                 | ``nullptr``             |
+--------------------------------------------------------------------+-------------------------+

``m_scene`` is a pointer to :ref:`SceneRegistry<class_SceneRegistry>` instance. Using this pointer we can add, remove, remove and do other stuff with components.
It is some sort of storage of every entity.  By default it ``nullptr``.
