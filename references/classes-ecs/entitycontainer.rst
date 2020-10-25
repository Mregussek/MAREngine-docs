.. _class_EntityContainer:

EntityContainer
===============

EntityContainer is a abstraction class for :ref:`Entity<class_Entity>` and :ref:`EntityCollection<class_EntityCollection>` storage. Now it is used as a member only by
:ref:`mar::ecs::Scene<class_Scene>` . Contains only two members, entities vector and collections vector. Created, because there was a lot of linker errors and this
was great solution to abstract those vectors.

EntityContainer has one friend class: 

* :ref:`mar::ecs::Scene<class_Scene>`

Members
-------

.. _class_member_EntityContainer_m_entities:

+----------------------------------------------------------------+
| std::vector< :ref:`Entity<class_Entity>` > m_entities          |
+----------------------------------------------------------------+

``m_entities`` is a vector of :ref:`Entity<class_Entity>` .

.. _class_member_EntityContainer_m_collections:

+----------------------------------------------------------------------------------------+
| std::vector< :ref:`EntityCollection<class_EntityCollection>` > m_collections           |
+----------------------------------------------------------------------------------------+

``m_collections`` is a vector of :ref:`EntityCollection<class_EntityCollection>` .

