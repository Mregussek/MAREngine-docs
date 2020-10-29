
.. _class_Entity:

Entity
======

The entity is a general purpose object. It only consists of a unique id (uint32_t, which can found at :ref:`entt::entity<class_entt_entity>` ). Every entity is a container, where
:ref:`components<ecs_Components>` can be attached. Entities are the base of all objects, that can be found in the scene.

.. warning::

    If Entity has no :ref:`RenderableComponent<class_RenderableComponent>` and some mesh component (one from :ref:`texture components<ecs_TextureComponents>`),
    it cannot be rendered!

.. _attention_Tag_Transform_DefaultComponents_Entity:

.. attention::

    By default every entity should have its :ref:`TagComponent<class_TagComponent>` and :ref:`TransformComponent<class_TransformComponent>`! So there is no need to check if
    Entity has those components attached! A lack of them is considered a huge error!


Entity has two friend classes:

* :ref:`mar::ecs::Scene<class_Scene>`
* :ref:`mar::ecs::EntityCollection<class_EntityCollection>`

Constructors / Descructors
--------------------------

.. _class_constructor_Entity_scene_registry:

+------------------------------------------------------------------------------+
| Entity( :ref:`SceneRegistry*<class_SceneRegistry>` * scene)                  |
+------------------------------------------------------------------------------+

This is default constructor for :ref:`Entity class<class_Entity>`, because we need to initialize :ref:`m_scene member<class_member_Entity_m_scene>`! If :ref:`m_scene member<class_member_Entity_m_scene>`
will stay as nullptr value, Entity instance will immedietaly crash. During this constructor call entity is created.

Public Methods
--------------

.. _class_method_Entity_destroyYourself:

+-----------------------------------------------+
| void destroyYourself() const                  |
+-----------------------------------------------+

Method destroys Entity. Instance is not valid anymore. Marked const, as it does not modify Entity instance.

.. _class_method_Entity_addDefault:

+-----------------------------------------------+
| void addDefault() const                       |
+-----------------------------------------------+

Method adds default components to entity ( :ref:`EngineOnlyComponents<ecs_EngineOnlyComponent>` ). Without these components
:ref:`RenderPipeline<class_RenderPipeline>` will not work. Marked const, as it does not modify Entity instance.

.. _class_method_Entity_copyDefault:

+---------------------------------------------------------------------+
| void copyDefault(const :ref:`Entity<class_Entity>` & other) const   |
+---------------------------------------------------------------------+

Method copies default components ( :ref:`EngineOnlyComponents<ecs_EngineOnlyComponent>` ) from ``other`` Entity to ``this`` Entity.
Marked const, as it does not modify Entity instance.

.. _class_method_Entity_isValid:

+-----------------------------------------------+
| const bool isValid() const                    |
+-----------------------------------------------+

Method checks, if current Entity is valid (valid means, if entity is created). Marked const, as it does not modify Entity instance.

.. _class_method_Entity_hasComponent:

+---------------------------------------------------------+
| template<typename T> const bool hasComponent() const    |
+---------------------------------------------------------+

Method returns true, if entity has component attached. It is a templated method, where ``T`` stands for component. Marked const, as it does not modify Entity instance.

.. _class_method_Entity_addComponent:

+-------------------------------------------------------------------------------+
| template<typename T, typename... Args> T& addComponent(Args&&... args) const  |
+-------------------------------------------------------------------------------+

Method adds component to Entity object. ``T`` stands for selected component. Parameter pack ``Args`` stands for arguments with which component can be created, but practically always
component is created without any addinational arguments. Method returns reference to newly created component. Method marked const, as it does not modify Entity instance.

.. _class_method_Entity_getComponent:

+-----------------------------------------------------------------------------------------------------------+
| template<typename T> T& getComponent() const                                                              |
+-----------------------------------------------------------------------------------------------------------+

Method returns reference to component attached to Entity. Method does not check, if component is already attached, make sure to check it 
with :ref:`hasComponent<class_method_Entity_hasComponent>` method! Exception is Tag and Transform, :ref:`check this<attention_Tag_Transform_DefaultComponents_Entity>` .
Marked const, as it does not modify Entity instance.

.. _class_method_Entity_replaceComponent:

+------------------------------------------------------------------------------------------------------------+
| template<typename T> T& replaceComponent(const :ref:`Entity<class_Entity>` & other) const                  |
+------------------------------------------------------------------------------------------------------------+

Method replaces current component of ``this`` entity instance with component of ``other`` entity. Method returns reference to newly created component.
``T`` stands for selected component. Marked const, as it does not modify Entity instance.

.. _class_method_Entity_removeComponent:

+----------------------------------------------------+
| template<typename T> void removeComponent() const  |
+----------------------------------------------------+

Method removes component from current Entity. ``T`` stands for component to delete. Marked const, as it does not modify Entity instance.

Operators
---------

.. _class_operator_Entity_bool:

+-----------------------------------------------------------------------------------------------------------+
| operator const bool() const                                                                               |
+-----------------------------------------------------------------------------------------------------------+

Operator calls :ref:`isValid<class_method_Entity_isValid>` and returns its result.

Members
-------

.. _class_member_Entity_m_entityHandle:

+----------------------------------------------------------------+-------------------------+
| :ref:`entt::entity<class_entt_entity>` m_entityHandle          | ``entt::null``          |
+----------------------------------------------------------------+-------------------------+

``m_entityHandle`` is unique ID for this Entity instance. By default is ``entt::null``, which stands for not valid Entity.

.. _class_member_Entity_m_scene:

+--------------------------------------------------------------------+-------------------------+
| :ref:`SceneRegistry*<class_SceneRegistry>` m_scene                 | ``nullptr``             |
+--------------------------------------------------------------------+-------------------------+

``m_scene`` is a pointer to :ref:`SceneRegistry<class_SceneRegistry>` instance. Using this pointer we can add, remove, remove and do other stuff with components.
It is a sort of storage of every entity. By default its a  ``nullptr``. 
