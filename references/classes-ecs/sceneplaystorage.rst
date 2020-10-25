.. _class_ScenePlayStorage:

ScenePlayStorage
================

As the name suggests, ``ScenePlayStorage`` is storage for Scene during Play mode. When we are editing scene in Editor Mode and then want to test our game,
we click Play button and after those tests we expect that engine saved all important data about scene. Any actions from Play mode should have no impact into
Editor mode. This method just saves state of scene before Play button clicked.

It has two nested classes to help organize things:

* :ref:`EntityStorage<nested_class_EntityStorage>`
* :ref:`CollectionStorage<nested_class_CollectionStorage>`

Public Methods
--------------

.. _class_method_ScenePlayStorage_pushEntityToStorage:

+----------------------------------------------------------------------+
| void pushEntityToStorage(const :ref:`Entity<class_Entity>` & entity) |
+----------------------------------------------------------------------+

Method pushes :ref:`Entity<class_Entity>` to :ref:`m_entityStorage<class_member_ScenePlayStorage_m_entityStorage>` member. Firstly creates new storage in vector and then
pushes data from entity to that variable.

.. _class_method_ScenePlayStorage_pushCollectionToStorage:

+--------------------------------------------------------------------------------------------------+
| void pushCollectionToStorage(const :ref:`EntityCollection<class_EntityCollection>` & collection) |
+--------------------------------------------------------------------------------------------------+

Method pushes :ref:`EntityCollection<class_EntityCollection>` to :ref:`m_collectionStorage<class_member_ScenePlayStorage_m_collectionStorage>` member. Firstly 
creates new storage in vector and then pushes data from collection to that variable.

.. _class_method_ScenePlayStorage_loadEntityFromStorage:

+------------------------------------------------------------------------+
| void loadEntityFromStorage(const :ref:`Entity<class_Entity>` & entity) |
+------------------------------------------------------------------------+

Method loads entity's from :ref:`m_entityStorage<class_member_ScenePlayStorage_m_entityStorage>` member and afterwards deletes unneeded storage.

.. _class_method_ScenePlayStorage_loadCollectionFromStorage:

+----------------------------------------------------------------------------------------------------+
| void loadCollectionFromStorage(const :ref:`EntityCollection<class_EntityCollection>` & collection) |
+----------------------------------------------------------------------------------------------------+

Method loads collection's data from :ref:`m_collectionStorage<class_member_ScenePlayStorage_m_collectionStorage>` member and afterwards deletes unneeded storage.

.. _class_method_ScenePlayStorage_clear:

+--------------+
| void clear() |
+--------------+

Method is responsible for whole cleanup stuff in storages. It clears all memory used by every storage and make them ready for other run.

Private Methods
---------------

.. _class_method_ScenePlayStorage_pushEntityToStorage_private:

+------------------------------------------------------------------------------------------------------------------------------------------------------+
| void pushEntityToStorage(std::vector< :ref:`EntityStorage<nested_class_EntityStorage>` >& vectorStorage, const :ref:`Entity<class_Entity>` & entity) |
+------------------------------------------------------------------------------------------------------------------------------------------------------+

Because there was issue with differentiating :ref:`Entity<class_Entity>` class instances and entities from :ref:`EntityCollection<class_EntityCollection>` I have created
private method, where we can explicitly tell, to which storage should we pass data.

.. _class_method_ScenePlayStorage_pushOperation:

+------------------------------------------------------------------------------------------------------------------------------------------------------+
| void pushOperation(:ref:`EntityStorage<nested_class_EntityStorage>` & storage, const :ref:`Entity<class_Entity>` & entity);                          |
+------------------------------------------------------------------------------------------------------------------------------------------------------+

``pushOperation`` is method created in order to make it clear, that this body is responsible for push data into storage.

.. _class_method_ScenePlayStorage_loadEntityFromStorage_private:

+--------------------------------------------------------------------------------------------------------------------------------------------------------+
| void loadEntityFromStorage(std::vector< :ref:`EntityStorage<nested_class_EntityStorage>` >& vectorStorage, const :ref:`Entity<class_Entity>` & entity) |
+--------------------------------------------------------------------------------------------------------------------------------------------------------+

Because there was issue with differentiating :ref:`Entity<class_Entity>` class instances and entities from :ref:`EntityCollection<class_EntityCollection>` I have created
private method, where we can explicitly tell, from which storage should we load data.

.. _class_method_ScenePlayStorage_loadOperation:

+------------------------------------------------------------------------------------------------------------------------------------------------------+
| void loadOperation(const :ref:`EntityStorage<nested_class_EntityStorage>` & storage, const :ref:`Entity<class_Entity>` & entity)                     |
+------------------------------------------------------------------------------------------------------------------------------------------------------+

``loadOperation`` is method created in order to make it clear, that this body is responsible for loading data from storage.

Members
-------

.. _class_member_ScenePlayStorage_m_entityStorage:

+-------------------------------------------------------------------------------------+
| std::vector< :ref:`EntityStorage<nested_class_EntityStorage>` > m_entityStorage     |
+-------------------------------------------------------------------------------------+

``m_entityStorage`` is a container for entities data. I mean :ref:`entities<class_Entity>`, that are not in some :ref:`EntityCollection<class_EntityCollection>` instance,
but they are alone.

.. _class_member_ScenePlayStorage_m_collectionStorage:

+---------------------------------------------------------------------------------------------+
| std::vector< :ref:`CollectionStorage<nested_class_CollectionStorage>` > m_collectionStorage |
+---------------------------------------------------------------------------------------------+

``m_collectionStorage`` is a container for all entities that are in some :ref:`EntityCollection<class_EntityCollection>` instance.

Nested Structs
--------------

.. _nested_class_EntityStorage:

EntityStorage
~~~~~~~~~~~~~

For now EntityStorage has 3 members, which must be saved. :ref:`PythonScript<class_PythonScript>` can modify those components, so they must stored somewhere.

Members
```````

.. _class_member_EntityStorage_transform:

+-------------------------------------------------------------------------+
| :ref:`TransformComponent<class_TransformComponent>` transform           |
+-------------------------------------------------------------------------+

We need to save entities coordinates, because script can change position, rotation, etc. of some entity.

.. _class_member_EntityStorage_light:

+-----------------------------------------------------------------+
| :ref:`LightComponent<class_LightComponent>` light               |
+-----------------------------------------------------------------+

There is need to save entities light parameters, script can change ambient light, shininess or other parameters.

.. _class_member_EntityStorage_color:

+-----------------------------------------------------------------+
| :ref:`ColorComponent<class_ColorComponent>` color               |
+-----------------------------------------------------------------+

If entity contains has :ref:`ColorComponent<class_ColorComponent>` , during runtime script can change entity's color.

.. _nested_class_CollectionStorage:

CollectionStorage
~~~~~~~~~~~~~~~~~

:ref:`EntityCollection<class_EntityCollection>` is a collection of some :ref:`entities<class_Entity>`. To make it clear, that those storages belongs to specific
collection I have added CollectionStorage class. It contains vector of :ref:`EntityStorage<nested_class_EntityStorage>`.

Public Methods
``````````````

.. _class_method_CollectionStorage_clear:

+--------------------------------------+
| void clear()                         |
+--------------------------------------+

Method's responsibility is to clear all its storages.

Members
```````

.. _class_member_CollectionStorage_entities:

+-------------------------------------------------------------------------------------+
| std::vector< :ref:`EntityStorage<nested_class_EntityStorage>` > entities            |
+-------------------------------------------------------------------------------------+

``m_entityStorage`` is a container for entities data. I mean :ref:`entities<class_Entity>`, that are in some :ref:`EntityCollection<class_EntityCollection>` instance.