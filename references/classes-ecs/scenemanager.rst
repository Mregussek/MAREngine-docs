
.. _class_SceneManager:

SceneManager
============

SceneManager is a manager for :ref:`Scene<class_Scene>` instance. It tells other engine parts in what state the current scene is, like is it in PlayMode, EditorMode.
Also it updates the whole scene in selected Mode and connects scene to graphics engine (pushes data into :ref:`RenderPipeline<class_RenderPipeline>` ).

SceneManager has one friend class: 

* :ref:`mar::ecs::SceneEvents<class_SceneEvents>`

Also there is one typedef:

* :ref:`graphics::RenderPipeline<class_RenderPipeline>` to RenderPipeline

Public Methods
--------------

.. _class_method_SceneManager_initialize:

+----------------------------------------+
| void initialize() const                |
+----------------------------------------+

Method initializes whole scene. Iterates through all entities and collections and then pushes it to graphics engine.

.. _class_method_SceneManager_shutdown:

+--------------------------------+
| void shutdown()                |
+--------------------------------+

Method calls :ref:`shutdown<class_method_Scene_shutdown>` from m_scene instance and deletes scene.

.. _class_method_SceneManager_update:

+------------------------------+
| void update()                |
+------------------------------+

Method updates scene in selected mode. Checks if it is PlayMode, PauseMode or EditorMode and then updates scene to proper mode.

Setters
-------

.. _class_method_SceneManager_setScene:

+------------------------------------------------------------------+
| void setScene( :ref:`Scene<class_Scene>` * scene)                |
+------------------------------------------------------------------+

Method sets pointer to scene which should be managed. Pass selected ``scene`` as an argument.

.. _class_method_SceneManager_setEditorMode:

+------------------------------+
| void setEditorMode()         |
+------------------------------+

Use this method, if you want to be in EditorMode.

.. _class_method_SceneManager_setPlayMode:

+------------------------------+
| void setPlayMode()           |
+------------------------------+

Use this method, if you want to be in PlayMode. It initializes scripts and makes a copy for all entities.

.. _class_method_SceneManager_setExitPlayMode:

+------------------------------+
| void setExitPlayMode()       |
+------------------------------+

Use this method, if you want quit PlayMode. It loads all data, so that game is in the state set before PlayMode was set.

.. _class_method_SceneManager_setPauseMode:

+------------------------------+
| void setPauseMode()          |
+------------------------------+

Use this method if you want to be in PauseMode.

.. _class_method_SceneManager_unsetPauseMode:

+------------------------------+
| void unsetPauseMode()        |
+------------------------------+

Use this method, if you want to quit PauseMode.

Getters
-------

.. _class_method_SceneManager_getScene:

+-------------------------------------------------------+
| :ref:`Scene<class_Scene>` * getScene()                |
+-------------------------------------------------------+

Method returns non-const pointer to scene, because we would like to create new entity or collection from GUI editor, or somewhere else in code.

.. _class_method_SceneManager_isEditorMode:

+------------------------------+
| bool isEditorMode()          |
+------------------------------+

Method returns true, if scene is in EditorMode.

.. _class_method_SceneManager_isPlayMode:

+------------------------------+
| bool isPlayMode()            |
+------------------------------+

Method returns true, if scene is in PlayMode.

.. _class_method_SceneManager_isPauseMode:

+------------------------------+
| bool isPauseMode()           |
+------------------------------+

Method returns true, if scene is in PauseMode.

Private Methods
---------------

.. _class_method_SceneManager_initPlayMode:

+------------------------------+
| void initPlayMode()          |
+------------------------------+

Method initializes PlayMode. Iterates over all entities and collections and runs ``start()`` method from :ref:`PythonScript<class_PythonScript>` .

.. _class_method_SceneManager_exitPlayMode:

+------------------------------+
| void exitPlayMode()          |
+------------------------------+

Method exits PlayMode. Iterates over all entities and collections and loads its parameters.

.. _class_method_SceneManager_updateEditorMode:

+------------------------------+
| void updateEditorMode()      |
+------------------------------+

Methods updates scene during Editor Mode. For now it only checks, if user wants to use Editor Camera, or to check Play Mode camera. If user changes
his mind it also changes camera.

.. _class_method_SceneManager_updatePlayMode:

+------------------------------+
| void updatePlayMode()        |
+------------------------------+

Method updates scene during Play mode. It iterates over all existing entities and collections. Calls ``update()`` method from :ref:`PythonScript<class_PythonScript>` 
and :ref:`updateEntityInPlaymode<class_method_SceneManager_updateEntityInPlaymode>` .

.. _class_method_SceneManager_updatePauseMode:

+------------------------------+
| void updatePauseMode()       |
+------------------------------+

Method updates scene during Pause mode. It iterates over all existing entities and collections and updates its states. 
Comparing to :ref:`updatePlayMode<class_method_SceneManager_updatePlayMode>` it calls only :ref:`updateEntityInPlaymode<class_method_SceneManager_updateEntityInPlaymode>` .

.. _class_method_SceneManager_updateEntityInPlaymode:

+------------------------------------------------------------------------------------------------------------------------------------------------------+
| void updateEntityInPlaymode(const :ref:`Entity<class_Entity>` & entity, :ref:`RenderPipeline<class_RenderPipeline>` & renderPipeline)                |
+------------------------------------------------------------------------------------------------------------------------------------------------------+

Method is reponsible for pushing modified data in Play mode to :ref:`RenderPipeline<class_RenderPipeline>`. As a parameter it needs ``entity``, which was updated during 
last frame. This modified data from ``entity`` is pushed into passed ``renderPipeline``.

.. _class_method_SceneManager_submitCameraIfPossible:

+-------------------------------+
| bool submitCameraIfPossible() |
+-------------------------------+

Method iterates over all entiies that have :ref:`CameraComponent<class_CameraComponent>` and looks for one component with "main" in its camera ID. If found, 
parameters of CameraComponent are passed to :ref:`RenderPipeline<class_RenderPipeline>`. Returns true, if camera ID with "main" was found, false otherwise.

Members
-------

.. _class_member_Scene_m_scene:

+-----------------------------------------+-------------------------+
| :ref:`Scene*<class_Scene>` m_scene      | ``nullptr``             |
+-----------------------------------------+-------------------------+

m_scene is a Scene pointer that needs to be managed (that needs to be played).

.. _class_member_Scene_m_playStorage:

+---------------------------------------------------------------------+
| :ref:`ScenePlayStorage<class_ScenePlayStorage>` m_playStorage       |
+---------------------------------------------------------------------+

m_playStorage is a storage for all the data during Play Mode. Read about this :ref:`here<class_ScenePlayStorage>` .

.. _class_member_Scene_m_EditorMode:

+-------------------------+----------------------+
| bool m_EditorMode       | ``true``             |
+-------------------------+----------------------+

m_EditorMode is a boolean, that contains information about current state of Scene - true for EditorMode, false for PlayMode.

.. _class_member_Scene_m_PauseMode:

+------------------------+-----------------------+
| bool m_PauseMode       | ``false``             |
+------------------------+-----------------------+

m_PauseMode is a boolean, that contains information about current state of Scene - true for PauseMode, false for EditorMode or PlayMode.
**Important note: m_pauseMode can be only true, if m_EditorMode is false (if there is PlayMode enabled)!**
