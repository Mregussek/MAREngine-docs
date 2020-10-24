
.. _class_SceneManager:

SceneManager
============

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

initialize description

.. _class_method_SceneManager_shutdown:

+--------------------------------+
| void shutdown()                |
+--------------------------------+

shutdown description

.. _class_method_SceneManager_update:

+------------------------------+
| void update()                |
+------------------------------+

update description

Setters
-------

.. _class_method_SceneManager_setScene:

+------------------------------------------------------------------+
| void setScene( :ref:`Scene<class_Scene>` * scene)                |
+------------------------------------------------------------------+

setScene description

.. _class_method_SceneManager_setEditorMode:

+------------------------------+
| void setEditorMode()         |
+------------------------------+

setEditorMode description

.. _class_method_SceneManager_setPlayMode:

+------------------------------+
| void setPlayMode()           |
+------------------------------+

setPlayMode description

.. _class_method_SceneManager_setExitPlayMode:

+------------------------------+
| void setExitPlayMode()       |
+------------------------------+

setExitPlayMode description

.. _class_method_SceneManager_setPauseMode:

+------------------------------+
| void setPauseMode()          |
+------------------------------+

setPauseMode description

.. _class_method_SceneManager_unsetPauseMode:

+------------------------------+
| void unsetPauseMode()        |
+------------------------------+

unsetPauseMode description

Getters
-------

.. _class_method_SceneManager_getScene:

+-------------------------------------------------------+
| :ref:`Scene<class_Scene>` * getScene()                |
+-------------------------------------------------------+

getScene description

.. _class_method_SceneManager_isEditorMode:

+------------------------------+
| bool isEditorMode()          |
+------------------------------+

isEditorMode description

.. _class_method_SceneManager_isPlayMode:

+------------------------------+
| bool isPlayMode()            |
+------------------------------+

isPlayMode description

.. _class_method_SceneManager_isPauseMode:

+------------------------------+
| bool isPauseMode()           |
+------------------------------+

isPauseMode description

Private Methods
---------------

.. _class_method_SceneManager_initPlayMode:

+------------------------------+
| void initPlayMode()          |
+------------------------------+

initPlayMode description

.. _class_method_SceneManager_exitPlayMode:

+------------------------------+
| void exitPlayMode()          |
+------------------------------+

exitPlayMode description

.. _class_method_SceneManager_updateEditorMode:

+------------------------------+
| void updateEditorMode()      |
+------------------------------+

updateEditorMode description

.. _class_method_SceneManager_updatePlayMode:

+------------------------------+
| void updatePlayMode()        |
+------------------------------+

updatePlayMode description

.. _class_method_SceneManager_updatePauseMode:

+------------------------------+
| void updatePauseMode()       |
+------------------------------+

updatePauseMode description

.. _class_method_SceneManager_updateEntityInPlaymode:

+------------------------------------------------------------------------------------------------------------------------------------------------------+
| void updateEntityInPlaymode(const :ref:`Entity<class_Entity>` & entity, :ref:`RenderPipeline<class_RenderPipeline>` & renderPipeline)                |
+------------------------------------------------------------------------------------------------------------------------------------------------------+

updateEntityInPlaymode description

.. _class_method_SceneManager_submitCameraIfPossible:

+-------------------------------+
| bool submitCameraIfPossible() |
+-------------------------------+

submitCameraIfPossible description

Members
-------

.. _class_member_Scene_m_scene:

+-----------------------------------------+-------------------------+
| :ref:`Scene<class_Scene>` m_scene       | ``nullptr``             |
+-----------------------------------------+-------------------------+

m_scene description

.. _class_member_Scene_m_playStorage:

+---------------------------------------------------------------------+
| :ref:`ScenePlayStorage<class_ScenePlayStorage>` m_playStorage       |
+---------------------------------------------------------------------+

m_playStorage description

.. _class_member_Scene_m_EditorMode:

+-------------------------+----------------------+
| bool m_EditorMode       | ``true``             |
+-------------------------+----------------------+

m_EditorMode description

.. _class_member_Scene_m_PauseMode:

+------------------------+-----------------------+
| bool m_PauseMode       | ``false``             |
+------------------------+-----------------------+

m_PauseMode description
