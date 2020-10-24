.. _class_ScenePlayStorage:

ScenePlayStorage
================

Public Methods
--------------

.. _class_method_ScenePlayStorage_pushEntityToStorage:

+----------------------------------------------------------------------+
| void pushEntityToStorage(const :ref:`Entity<class_Entity>` & entity) |
+----------------------------------------------------------------------+

description

.. _class_method_ScenePlayStorage_pushCollectionToStorage:

+--------------------------------------------------------------------------------------------------+
| void pushCollectionToStorage(const :ref:`EntityCollection<class_EntityCollection>` & collection) |
+--------------------------------------------------------------------------------------------------+

description

.. _class_method_ScenePlayStorage_loadEntityFromStorage:

+------------------------------------------------------------------------+
| void loadEntityFromStorage(const :ref:`Entity<class_Entity>` & entity) |
+------------------------------------------------------------------------+

description

.. _class_method_ScenePlayStorage_loadCollectionFromStorage:

+----------------------------------------------------------------------------------------------------+
| void loadCollectionFromStorage(const :ref:`EntityCollection<class_EntityCollection>` & collection) |
+----------------------------------------------------------------------------------------------------+

description

.. _class_method_ScenePlayStorage_clear:

+--------------+
| void clear() |
+--------------+

description

Private Methods
---------------

.. _class_method_ScenePlayStorage_pushEntityToStorage_private:

+------------------------------------------------------------------------------------------------------------------------------------------------------+
| void pushEntityToStorage(std::vector< :ref:`EntityStorage<nested_class_EntityStorage>` >& vectorStorage, const :ref:`Entity<class_Entity>` & entity) |
+------------------------------------------------------------------------------------------------------------------------------------------------------+

description

.. _class_method_ScenePlayStorage_pushOperation:

+------------------------------------------------------------------------------------------------------------------------------------------------------+
| void pushOperation(:ref:`EntityStorage<nested_class_EntityStorage>` & storage, const :ref:`Entity<class_Entity>` & entity);                          |
+------------------------------------------------------------------------------------------------------------------------------------------------------+

description

.. _class_method_ScenePlayStorage_loadEntityFromStorage_private:

+--------------------------------------------------------------------------------------------------------------------------------------------------------+
| void loadEntityFromStorage(std::vector< :ref:`EntityStorage<nested_class_EntityStorage>` >& vectorStorage, const :ref:`Entity<class_Entity>` & entity) |
+--------------------------------------------------------------------------------------------------------------------------------------------------------+

description

.. _class_method_ScenePlayStorage_loadOperation:

+------------------------------------------------------------------------------------------------------------------------------------------------------+
| void loadOperation(const :ref:`EntityStorage<nested_class_EntityStorage>` & storage, const :ref:`Entity<class_Entity>` & entity)                     |
+------------------------------------------------------------------------------------------------------------------------------------------------------+

description

Members
-------

.. _class_member_ScenePlayStorage_m_entityStorage:

+-------------------------------------------------------------------------------------+
| std::vector< :ref:`EntityStorage<nested_class_EntityStorage>` > m_entityStorage     |
+-------------------------------------------------------------------------------------+

description

.. _class_member_ScenePlayStorage_m_collectionStorage:

+---------------------------------------------------------------------------------------------+
| std::vector< :ref:`CollectionStorage<nested_class_CollectionStorage>` > m_collectionStorage |
+---------------------------------------------------------------------------------------------+

description

Nested Structs
--------------

.. _nested_class_EntityStorage:

EntityStorage
~~~~~~~~~~~~~

description

Members
```````

.. _class_member_EntityStorage_transform:

+-------------------------------------------------------------------------+
| :ref:`TransformComponent<class_TransformComponent>` transform           |
+-------------------------------------------------------------------------+

description

.. _class_member_EntityStorage_light:

+-----------------------------------------------------------------+
| :ref:`LightComponent<class_LightComponent>` light               |
+-----------------------------------------------------------------+

description

.. _class_member_EntityStorage_color:

+-----------------------------------------------------------------+
| :ref:`ColorComponent<class_ColorComponent>` color               |
+-----------------------------------------------------------------+

description

.. _nested_class_CollectionStorage:

CollectionStorage
~~~~~~~~~~~~~~~~~

description

Public Methods
``````````````

.. _class_method_CollectionStorage_clear:

+--------------------------------------+
| void clear()                         |
+--------------------------------------+

description

Members
```````

.. _class_member_CollectionStorage_entities:

+-------------------------------------------------------------------------------------+
| std::vector< :ref:`EntityStorage<nested_class_EntityStorage>` > entities            |
+-------------------------------------------------------------------------------------+

description
