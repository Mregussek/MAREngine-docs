
.. _class_Entity:

Entity
======

Entity Description

Entity has two friend classes: 

* :ref:`mar::ecs::Scene<class_Scene>`
* :ref:`mar::ecs::EntityCollection<class_EntityCollection>`

Constructors / Descructors
--------------------------

.. _class_constructor_entity_scene_registry:

+-----------------------------------------------+
| Entity(SceneRegistry* scene)                  |
+-----------------------------------------------+

This is default constructor for :ref:`Entity class<class_Entity>`, because we need to initialize :ref:`m_scene member<class_member_entity_m_scene>`.

Methods
-------

.. _class_method_entity_destroyYourself:

+-----------------------------------------------+
| void destroyYourself() const                  |
+-----------------------------------------------+

destroyYourself description

.. _class_method_entity_addDefault:

+-----------------------------------------------+
| void addDefault() const                       |
+-----------------------------------------------+

addDefault description

.. _class_method_entity_copyDefault:

+---------------------------------------------------------------------+
| void copyDefault(const :ref:`Entity<class_Entity>` & other) const   |
+---------------------------------------------------------------------+

copyDefault description

.. _class_method_entity_isValid:

+-----------------------------------------------+
| const bool isValid() const                    |
+-----------------------------------------------+

isValid description

.. _class_method_entity_hasComponent:

+---------------------------------------------------------+
| template<typename T> const bool hasComponent() const    |
+---------------------------------------------------------+

hasComponent description

.. _class_method_entity_addComponent:

+-------------------------------------------------------------------------------------------------------------------------------------------+
| template<typename T, typename... Args> T& addComponent(:ref:`EntityComponents<class_EntityComponents>` entcmp, Args&&... args) const      |
+-------------------------------------------------------------------------------------------------------------------------------------------+

addComponent description

.. _class_method_entity_getComponent:

+-----------------------------------------------------------------------------------------------------------+
| template<typename T> T& getComponent() const                                                              |
+-----------------------------------------------------------------------------------------------------------+

getComponent description

.. _class_method_entity_replaceComponent:

+------------------------------------------------------------------------------------------------------------+
| template<typename T> T& replaceComponent(const :ref:`Entity<class_Entity>` & other) const                  |
+------------------------------------------------------------------------------------------------------------+

replaceComponent description

.. _class_method_entity_removeComponent:

+-------------------------------------------------------------------------------------------------------------------------------------------+
| template<typename T> void removeComponent(:ref:`EntityComponents<class_EntityComponents>` entcmp) const                                   |
+-------------------------------------------------------------------------------------------------------------------------------------------+

removeComponents description

Operators
---------

.. _class_operator_entity_bool:

+-----------------------------------------------------------------------------------------------------------+
| operator const bool() const                                                                               |
+-----------------------------------------------------------------------------------------------------------+

description

Members
-------

.. _class_member_entity_m_entityHandle:

+-----------------------------------------------+-------------------------+-------------------------+
| :ref:`entt::entity<class_entt_entity>`        | m_entityHandle          | ``entt::null``          |
+-----------------------------------------------+-------------------------+-------------------------+

m_entityHandle description

.. _class_member_entity_m_scene:

+-----------------------------------------------+-------------------------+-------------------------+
| :ref:`SceneRegistry*<class_SceneRegistry>`    | m_scene                 | ``nullptr``             |
+-----------------------------------------------+-------------------------+-------------------------+

m_scene description
