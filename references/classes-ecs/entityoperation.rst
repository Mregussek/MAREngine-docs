.. _class_EntityOperation:

EntityOperation
===============

``EntityOperation`` class contains only static methods, which are used for specific actions with :ref:`Entities<class_Entity>` or :ref:`EntityCollections<class_EntityCollection>`.

Public Static Methods
---------------------

.. _class_method_EntityOperation_copyEntity:

+---------------------------------------------------------------------------------------------------------------------------------+
| static void copyEntity(const :ref:`Entity<class_Entity>` & src, const :ref:`Entity<class_Entity>` & dst)                        |
+---------------------------------------------------------------------------------------------------------------------------------+

Method copies ``src`` Entity instance to ``dst``. Please make sure, that both entities passed are valid. Copying entity means that, every component attached to ``src``
entity is copied into ``dst`` entity instance. Method checks, if ``dst`` already have those components, if has components are replaced, if not they are added.

.. _class_method_EntityOperation_copyCollection:

+--------------------------------------------------------------------------------------------------------------------------------------------------------+
| static void copyCollection(const :ref:`EntityCollection<class_EntityCollection>` & src, const :ref:`EntityCollection<class_EntityCollection>` & dst)   |
+--------------------------------------------------------------------------------------------------------------------------------------------------------+

Method copies ``src`` EntityCollection to ``dst``. Please make sure, that both collections passed are valid. Copying collection means that, every component attached to ``src``
collection is copied into ``dst`` instance. Secondly method is created new entities and calls :ref:`copyEntity<class_method_EntityOperation_copyEntity>` method 
for entities that are stored in collection.

Private Static Methods
----------------------

.. _class_method_EntityOperation_copyComponent_Entities:

+--------------------------------------------------------------------------------------------------------------+
| template<typename T>                                                                                         |
| static void copyComponent(const :ref:`Entity<class_Entity>` & src, const :ref:`Entity<class_Entity>` & dst)  |
+--------------------------------------------------------------------------------------------------------------+

Method is responsible for copying selected component from ``src`` entity to ``dst``. Method checks, if ``dst`` already has this component, if so it replaces current
instance, if not it adds component to ``dst`` and then replaces it. ``T`` stands for component

.. _class_method_EntityOperation_copyComponent_Collections:

+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| template<typename T>                                                                                                                                                 |
| static void copyComponent(const :ref:`EntityCollection<class_EntityCollection>` & src, const :ref:`EntityCollection<class_EntityCollection>` & dst)                  |
+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Method is responsible for copying selected component from ``src`` collection to ``dst``. Method checks, if ``dst`` already has this component, if so it replaces current
instance, if not it adds component to ``dst`` and then replaces it. ``T`` stands for component
