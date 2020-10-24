.. _class_SceneEvents:

SceneEvents
===========

SceneEvents description

Static Public Methods
---------------------

.. _class_method_SceneEvents_Instance:

+-----------------------------------------------+
| static SceneEvents& Instance()                |
+-----------------------------------------------+

Instance description

Setters
-------

.. _class_method_SceneEvents_setSceneManager:

+-----------------------------------------------------------------------------+
| void setSceneManager(:ref:`SceneManager*<class_SceneManager>` & manager)    |
+-----------------------------------------------------------------------------+

setSceneManager description

Public Methods
--------------

Transform
~~~~~~~~~

.. _class_method_SceneEvents_onTransformUpdate:

+-----------------------------------------------------------------------------+
| void onTransformUpdate(const :ref:`Entity<class_Entity>` * e) const         |
+-----------------------------------------------------------------------------+

onTransformUpdate description

Renderable
~~~~~~~~~~

.. _class_method_SceneEvents_onRenderableAdd:

+--------------------------------------+
| void onRenderableAdd() const         |
+--------------------------------------+

onRenderableAdd description

.. _class_method_SceneEvents_onRenderableUpdate:

+-----------------------------------------------------------------------------+
| void onRenderableUpdate(const :ref:`Entity<class_Entity>` * e) const        |
+-----------------------------------------------------------------------------+

onRenderableUpdate description

.. _class_method_SceneEvents_onRenderableRemove:

+-----------------------------------------+
| void onRenderableRemove() const         |
+-----------------------------------------+

onRenderableRemove description

Camera
~~~~~~

.. _class_method_SceneEvents_onCameraAdd:

+--------------------------------------+
| void onCameraAdd() const             |
+--------------------------------------+

onCameraAdd description

.. _class_method_SceneEvents_onCameraUpdate:

+-----------------------------------------------------------------------------+
| void onCameraUpdate(const :ref:`Entity<class_Entity>` * e) const            |
+-----------------------------------------------------------------------------+

onCameraUpdate description

.. _class_method_SceneEvents_onCameraRemove:

+-----------------------------------------+
| void onCameraRemove() const             |
+-----------------------------------------+

onCameraRemove description

Color
~~~~~

.. _class_method_SceneEvents_onColorAdd:

+--------------------------------------+
| void onColorAdd() const              |
+--------------------------------------+

onColorAdd description

.. _class_method_SceneEvents_onColorUpdate:

+-----------------------------------------------------------------------------+
| void onColorUpdate(const :ref:`Entity<class_Entity>` * e) const             |
+-----------------------------------------------------------------------------+

onColorUpdate description

.. _class_method_SceneEvents_onColorRemove:

+-----------------------------------------+
| void onColorRemove() const              |
+-----------------------------------------+

onColorRemove description

Texture2D
~~~~~~~~~

.. _class_method_SceneEvents_onTexture2DAdd:

+--------------------------------------+
| void onTexture2DAdd() const          |
+--------------------------------------+

onTexture2DAdd description

.. _class_method_SceneEvents_onTexture2DUpdate:

+-----------------------------------------------------------------------------+
| void onTexture2DUpdate(const :ref:`Entity<class_Entity>` * e) const         |
+-----------------------------------------------------------------------------+

onTexture2DUpdate description

.. _class_method_SceneEvents_onTexture2DRemove:

+-----------------------------------------+
| void onTexture2DRemove() const          |
+-----------------------------------------+

onTexture2DRemove description

TextureCubemap
~~~~~~~~~~~~~~

.. _class_method_SceneEvents_onTextureCubemapAdd:

+--------------------------------------+
| void onTextureCubemapAdd() const     |
+--------------------------------------+

onTextureCubemapAdd description

.. _class_method_SceneEvents_onTextureCubemapUpdate:

+-----------------------------------------------------------------------------+
| void onTextureCubemapUpdate(const :ref:`Entity<class_Entity>` * e) const    |
+-----------------------------------------------------------------------------+

onTextureCubemapUpdate description

.. _class_method_SceneEvents_onTextureCubemapRemove:

+-----------------------------------------+
| void onTextureCubemapRemove() const     |
+-----------------------------------------+

onTextureCubemapRemove description

Light
~~~~~

.. _class_method_SceneEvents_onLightAdd:

+--------------------------------------+
| void onLightAdd() const              |
+--------------------------------------+

onLightAdd description

.. _class_method_SceneEvents_onLightUpdate:

+-----------------------------------------------------------------------------+
| void onLightUpdate(const :ref:`Entity<class_Entity>` * e) const             |
+-----------------------------------------------------------------------------+

onLightUpdate description

.. _class_method_SceneEvents_onLightRemove:

+-----------------------------------------+
| void onLightRemove() const              |
+-----------------------------------------+

onLightRemove description

Script
~~~~~~

.. _class_method_SceneEvents_onScriptAdd:

+--------------------------------------+
| void onScriptAdd() const             |
+--------------------------------------+

onScriptAdd description

.. _class_method_SceneEvents_onScriptUpdate:

+-----------------------------------------------------------------------------+
| void onScriptUpdate(const :ref:`Entity<class_Entity>` * e) const            |
+-----------------------------------------------------------------------------+

onScriptUpdate description

.. _class_method_SceneEvents_onScriptRemove:

+-----------------------------------------+
| void onScriptRemove() const             |
+-----------------------------------------+

onScriptRemove description

Other
~~~~~

.. _class_method_SceneEvents_onEntityCopy:

+-----------------------------------------+
| void onEntityCopy() const               |
+-----------------------------------------+

onEntityCopy description

.. _class_method_SceneEvents_onEntityRemove:

+-----------------------------------------+
| void onEntityRemove() const             |
+-----------------------------------------+

onEntityRemove description

.. _class_method_SceneEvents_onCollectionTransformUpdate:

+------------------------------------------+
| void onCollectionTransformUpdate() const |
+------------------------------------------+

onCollectionTransformUpdate description

.. _class_method_SceneEvents_onCollectionRemove:

+-----------------------------------------+
| void onCollectionRemove() const         |
+-----------------------------------------+

onCollectionRemove description

.. _class_method_SceneEvents_onCollectionOBJloaded:

+------------------------------------------------------------------------------------------------------------------+
| void onCollectionOBJloaded(const :ref:`EntityCollection<class_EntityCollection>` & collection) const             |
+------------------------------------------------------------------------------------------------------------------+

onCollectionOBJloaded description

Static Members
--------------

.. _class_member_SceneEvents_s_instance:

+-----------------------------------------------+-------------------------+-------------------------+
| :ref:`static SceneEvents<class_SceneEvents>`  | s_instance              | ``nullptr``             |
+-----------------------------------------------+-------------------------+-------------------------+

s_instance description

Members
-------

.. _class_member_SceneEvents_m_sceneManager:

+-----------------------------------------------+-------------------------+-------------------------+
| :ref:`SceneManager*<class_SceneManager>`      | m_sceneManager          | ``nullptr``             |
+-----------------------------------------------+-------------------------+-------------------------+

m_sceneManager description