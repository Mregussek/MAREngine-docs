.. _class_EntityOperation:

EntityOperation
===============

Public Static Methods
---------------------

.. _class_method_EntityOperation_copyEntity:

+---------------------------------------------------------------------------------------------------------------------------------+
| static void copyEntity(const :ref:`Entity<class_Entity>` & src, const :ref:`Entity<class_Entity>` & dst)                        |
+---------------------------------------------------------------------------------------------------------------------------------+

copyEntity description

.. _class_method_EntityOperation_copyCollection:

+--------------------------------------------------------------------------------------------------------------------------------------------------------+
| static void copyCollection(const :ref:`EntityCollection<class_EntityCollection>` & src, const :ref:`EntityCollection<class_EntityCollection>` & dst)   |
+--------------------------------------------------------------------------------------------------------------------------------------------------------+

copyCollection description

Private Static Methods
----------------------

.. _class_method_EntityOperation_copyComponent_Entities:

+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| template<typename T>                                                                                                                                                 |
| static void copyComponent(:ref:`EntityComponents<class_EntityComponents>` entcmp, const :ref:`Entity<class_Entity>` & src, const :ref:`Entity<class_Entity>` & dst)  |
+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

copyComponent description

.. _class_method_EntityOperation_copyComponent_Collections:

+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| template<typename T>                                                                                                                                                 |
| static void copyComponent(const :ref:`EntityCollection<class_EntityCollection>` & src, const :ref:`EntityCollection<class_EntityCollection>` & dst)                  |
+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

copyComponent description
