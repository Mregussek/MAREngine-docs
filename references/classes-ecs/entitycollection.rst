.. _class_EntityCollection:

EntityCollection
================

Public Methods
--------------

.. _class_method_EntityCollection_destroyYourself:

+-----------------------------------------------+
| void destroyYourself() const                  |
+-----------------------------------------------+

destroyYourself description

.. _class_method_EntityCollection_isValid:

+-----------------------------------------------+
| const bool isValid() const                    |
+-----------------------------------------------+

isValid description

.. _class_method_EntityCollection_createEntity:

+---------------------------------------------------------------------------------------------------------------------------------+
| const :ref:`Entity<class_Entity>` & createEntity() const                                                                        |
+---------------------------------------------------------------------------------------------------------------------------------+

createEntity description

.. _class_method_EntityCollection_destroyEntity:

+---------------------------------------------------------------------------------------------------------------------------------+
| void destroyEntity(int32_t entity_index) const                                                                                  |
+---------------------------------------------------------------------------------------------------------------------------------+

destroyEntity description

.. _class_method_EntityCollection_getEntities:

+---------------------------------------------------------------------------------------------------------------------------------+
| const std::vector< :ref:`Entity<class_Entity>` >>& getEntities() const                                                          |
+---------------------------------------------------------------------------------------------------------------------------------+

getEntities description

.. _class_method_EntityCollection_hasComponent:

+---------------------------------------------------------+
| template<typename T> bool hasComponent() const          |
+---------------------------------------------------------+

hasComponent description

.. _class_method_EntityCollection_addComponent:

+-----------------------------------------------------------------------------------+
| template<typename T, typename... Args> T& addComponent(Args&&... args) const      |
+-----------------------------------------------------------------------------------+

addComponent description

.. _class_method_EntityCollection_getComponent:

+-----------------------------------------------------------------------------------------------------------+
| template<typename T> T& getComponent() const                                                              |
+-----------------------------------------------------------------------------------------------------------+

getComponent description

.. _class_method_EntityCollection_replaceComponent:

+--------------------------------------------------------------------------------------------------------------------------------+
| template<typename T> T& replaceComponent(const :ref:`EntityCollection<class_EntityCollection>` & other) const                  |
+--------------------------------------------------------------------------------------------------------------------------------+

replaceComponent description

.. _class_method_EntityCollection_removeComponent:

+-------------------------------------------------------------------------------------+
| template<typename T> void removeComponent() const                                   |
+-------------------------------------------------------------------------------------+

removeComponents description

Operators
---------

.. _class_operator_EntityCollection_bool:

+-----------------------------------------------------------------------------------------------------------+
| operator const bool() const                                                                               |
+-----------------------------------------------------------------------------------------------------------+

description

Members
-------

.. _class_member_EntityCollection_m_collectionHandle:

+----------------------------------------------------------------+-------------------------+
| :ref:`entt::entity<class_entt_entity>` m_collectionHandle      | ``entt::null``          |
+----------------------------------------------------------------+-------------------------+

m_collectionHandle description

.. _class_member_EntityCollection_m_scene:

+--------------------------------------------------------------------+-------------------------+
| :ref:`SceneRegistry*<class_SceneRegistry>` m_scene                 | ``nullptr``             |
+--------------------------------------------------------------------+-------------------------+

m_scene description