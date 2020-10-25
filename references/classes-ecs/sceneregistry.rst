.. _class_SceneRegistry:

SceneRegistry
=============

A SceneRegistry can store and manage entities, as well as create views and groups to iterate the underlying data structures. It is used both to construct and 
to destroy entities. SceneRegistry is just abstraction for :ref:`entt::registry<class_entt_registry>` , because I have found a lot of linker errors with using just
:ref:`m_registry<class_member_SceneRegistry_m_registry>` member. Now it is used as a member only by :ref:`mar::ecs::Scene<class_Scene>` .

SceneRegistry has three friend classes: 

* :ref:`mar::ecs::Scene<class_Scene>`
* :ref:`mar::ecs::Entity<class_Entity>`
* :ref:`mar::ecs::EntityCollection<class_EntityCollection>`

Constructors / Destructors
--------------------------

.. _class_constructor_SceneRegistry:

+-----------------------------------------------+
| SceneRegistry()                               |
+-----------------------------------------------+

This is default constructor for :ref:`SceneRegistry<class_SceneRegistry>`, because we need to initialize :ref:`m_registry member<class_member_SceneRegistry_m_registry>`.

Public Methods
--------------

.. _class_method_SceneRegistry_cleanup:

+-----------------------------------------------+
| void cleanup()                                |
+-----------------------------------------------+

Method destroys all created entities in a registry at once.

Members
-------

.. _class_member_SceneRegistry_m_registry:

+----------------------------------------------------------------+
| :ref:`entt::registry<class_entt_registry>` m_registry          |
+----------------------------------------------------------------+

``m_registry`` is a core for Entity-Component System. With this we can instantiate all entities, destroy them, attach components and so on. Please read about 
this :ref:`here<class_entt_registry>` .