.. _class_SceneEvents:

SceneEvents
===========

SceneEvents is a abstraction layer for Event system during all Scene operations. Using this method we can update stuff during engine execution. There is one static member,
which has to be called in order to execute event. Example:

.. code-block:: cpp

    auto& transform = entity.getComponent<TransformComponent>();
    transform.center.x += 5.0f;
    SceneEvents::Instance().onTransformUpdate(entity);


.. warning:: 

    All public methods with "on" at the beginning of its name are marked const, because they do not modify :ref:`s_instance<class_member_SceneEvents_s_instance>`.


Static Public Methods
---------------------

.. _class_method_SceneEvents_Instance:

+-----------------------------------------------+
| static SceneEvents& Instance()                |
+-----------------------------------------------+

Returns reference to static member of SceneEvents class - :ref:`s_instance<class_member_SceneEvents_s_instance>` .

Setters
-------

.. _class_method_SceneEvents_setSceneManager:

+-----------------------------------------------------------------------------+
| void setSceneManager(:ref:`SceneManager*<class_SceneManager>` & manager)    |
+-----------------------------------------------------------------------------+

Method sets :ref:`m_sceneManager<class_member_SceneEvents_m_sceneManager>` member.

Public Methods
--------------

Transform
~~~~~~~~~

.. _class_method_SceneEvents_onTransformUpdate:

+-----------------------------------------------------------------------------+
| void onTransformUpdate(const :ref:`Entity<class_Entity>` * e) const         |
+-----------------------------------------------------------------------------+

Method should be called, when :ref:`TransformComponent<class_TransformComponent>` is updated, which means that if user called 
:ref:`recalculate<class_method_TransformComponent_recalculate>` method or updated component in any other way. As argument should be
passed pointer to entity, which component was updated.

Renderable
~~~~~~~~~~

.. _class_method_SceneEvents_onRenderableAdd:

+--------------------------------------+
| void onRenderableAdd() const         |
+--------------------------------------+

Method should be called if user added :ref:`RenderableComponent<class_RenderableComponent>` to an :ref:`Entity<class_Entity>` instance.

.. _class_method_SceneEvents_onRenderableUpdate:

+-----------------------------------------------------------------------------+
| void onRenderableUpdate(const :ref:`Entity<class_Entity>` * e) const        |
+-----------------------------------------------------------------------------+

Method should be called if user updated :ref:`RenderableComponent<class_RenderableComponent>` in an :ref:`Entity<class_Entity>` instance.
As argument should be passed pointer to entity, which component was updated.

.. _class_method_SceneEvents_onRenderableRemove:

+-----------------------------------------+
| void onRenderableRemove() const         |
+-----------------------------------------+

Method should be called if user removed :ref:`RenderableComponent<class_RenderableComponent>` from an :ref:`Entity<class_Entity>` instance.

Camera
~~~~~~

.. _class_method_SceneEvents_onCameraAdd:

+--------------------------------------+
| void onCameraAdd() const             |
+--------------------------------------+

Method should be called if user added :ref:`CameraComponent<class_CameraComponent>` to an :ref:`Entity<class_Entity>` instance.

.. _class_method_SceneEvents_onCameraUpdate:

+-----------------------------------------------------------------------------+
| void onCameraUpdate(const :ref:`Entity<class_Entity>` * e) const            |
+-----------------------------------------------------------------------------+

Method should be called if user updated :ref:`CameraComponent<class_CameraComponent>` in an :ref:`Entity<class_Entity>` instance.
As argument should be passed pointer to entity, which component was updated.

.. _class_method_SceneEvents_onCameraRemove:

+-----------------------------------------+
| void onCameraRemove() const             |
+-----------------------------------------+

Method should be called if user removed :ref:`CameraComponent<class_CameraComponent>` from an :ref:`Entity<class_Entity>` instance.

Color
~~~~~

.. _class_method_SceneEvents_onColorAdd:

+--------------------------------------+
| void onColorAdd() const              |
+--------------------------------------+

Method should be called if user added :ref:`ColorComponent<class_ColorComponent>` to an :ref:`Entity<class_Entity>` instance.

.. _class_method_SceneEvents_onColorUpdate:

+-----------------------------------------------------------------------------+
| void onColorUpdate(const :ref:`Entity<class_Entity>` * e) const             |
+-----------------------------------------------------------------------------+

Method should be called if user updated :ref:`CColorComponent<class_ColorComponent>` in an :ref:`Entity<class_Entity>` instance.
As argument should be passed pointer to entity, which component was updated.

.. _class_method_SceneEvents_onColorRemove:

+-----------------------------------------+
| void onColorRemove() const              |
+-----------------------------------------+

Method should be called if user removed :ref:`ColorComponent<class_ColorComponent>` from an :ref:`Entity<class_Entity>` instance.

Texture2D
~~~~~~~~~

.. _class_method_SceneEvents_onTexture2DAdd:

+--------------------------------------+
| void onTexture2DAdd() const          |
+--------------------------------------+

Method should be called if user added :ref:`Texture2DComponent<class_Texture2DComponent>` to an :ref:`Entity<class_Entity>` instance.

.. _class_method_SceneEvents_onTexture2DUpdate:

+-----------------------------------------------------------------------------+
| void onTexture2DUpdate(const :ref:`Entity<class_Entity>` * e) const         |
+-----------------------------------------------------------------------------+

Method should be called if user updated :ref:`Texture2DComponent<class_Texture2DComponent>` in an :ref:`Entity<class_Entity>` instance.
As argument should be passed pointer to entity, which component was updated.

.. _class_method_SceneEvents_onTexture2DRemove:

+-----------------------------------------+
| void onTexture2DRemove() const          |
+-----------------------------------------+

Method should be called if user removed :ref:`Texture2DComponent<class_Texture2DComponent>` from an :ref:`Entity<class_Entity>` instance.

TextureCubemap
~~~~~~~~~~~~~~

.. _class_method_SceneEvents_onTextureCubemapAdd:

+--------------------------------------+
| void onTextureCubemapAdd() const     |
+--------------------------------------+

Method should be called if user added :ref:`TextureCubemapComponent<class_TextureCubemapComponent>` to an :ref:`Entity<class_Entity>` instance.

.. _class_method_SceneEvents_onTextureCubemapUpdate:

+-----------------------------------------------------------------------------+
| void onTextureCubemapUpdate(const :ref:`Entity<class_Entity>` * e) const    |
+-----------------------------------------------------------------------------+

Method should be called if user updated :ref:`TextureCubemapComponent<class_TextureCubemapComponent>` in an :ref:`Entity<class_Entity>` instance.
As argument should be passed pointer to entity, which component was updated.

.. _class_method_SceneEvents_onTextureCubemapRemove:

+-----------------------------------------+
| void onTextureCubemapRemove() const     |
+-----------------------------------------+

Method should be called if user removed :ref:`TextureCubemapComponent<class_TextureCubemapComponent>` from an :ref:`Entity<class_Entity>` instance.

Light
~~~~~

.. _class_method_SceneEvents_onLightAdd:

+--------------------------------------+
| void onLightAdd() const              |
+--------------------------------------+

Method should be called if user added :ref:`LightComponent<class_LightComponent>` to an :ref:`Entity<class_Entity>` instance.

.. _class_method_SceneEvents_onLightUpdate:

+-----------------------------------------------------------------------------+
| void onLightUpdate(const :ref:`Entity<class_Entity>` * e) const             |
+-----------------------------------------------------------------------------+

Method should be called if user updated :ref:`LightComponent<class_LightComponent>` in an :ref:`Entity<class_Entity>` instance.
As argument should be passed pointer to entity, which component was updated.

.. _class_method_SceneEvents_onLightRemove:

+-----------------------------------------+
| void onLightRemove() const              |
+-----------------------------------------+

Method should be called if user removed :ref:`LightComponent<class_LightComponent>` from an :ref:`Entity<class_Entity>` instance.

Script
~~~~~~

.. _class_method_SceneEvents_onScriptAdd:

+--------------------------------------+
| void onScriptAdd() const             |
+--------------------------------------+

Method should be called if user added :ref:`ScriptComponent<class_ScriptComponent>` to an :ref:`Entity<class_Entity>` instance.

.. _class_method_SceneEvents_onScriptUpdate:

+-----------------------------------------------------------------------------+
| void onScriptUpdate(const :ref:`Entity<class_Entity>` * e) const            |
+-----------------------------------------------------------------------------+

Method should be called if user updated :ref:`ScriptComponent<class_ScriptComponent>` in an :ref:`Entity<class_Entity>` instance.
As argument should be passed pointer to entity, which component was updated.

.. _class_method_SceneEvents_onScriptRemove:

+-----------------------------------------+
| void onScriptRemove() const             |
+-----------------------------------------+

Method should be called if user removed :ref:`ScriptComponent<class_ScriptComponent>` from an :ref:`Entity<class_Entity>` instance.

Other
~~~~~

.. _class_method_SceneEvents_onEntityCopy:

+-----------------------------------------+
| void onEntityCopy() const               |
+-----------------------------------------+

Method should be called, if user called :ref:`copyEntity<class_method_EntityOperation_copyEntity>` from :ref:`EntityOperation<class_EntityOperation>` class.

.. _class_method_SceneEvents_onEntityRemove:

+-----------------------------------------+
| void onEntityRemove() const             |
+-----------------------------------------+

Method should be called, when user has deleted some :ref:`Entity<class_Entity>` from scene.

.. _class_method_SceneEvents_onCollectionTransformUpdate:

+------------------------------------------+
| void onCollectionTransformUpdate() const |
+------------------------------------------+

Method should be called, when :ref:`TransformComponent<class_TransformComponent>` is updated in some :ref:`EntityCollection<class_EntityCollection>` instance, 
which means that if user called  :ref:`recalculate<class_method_TransformComponent_recalculate>` method or updated component in any other way.

.. _class_method_SceneEvents_onCollectionRemove:

+-----------------------------------------+
| void onCollectionRemove() const         |
+-----------------------------------------+

Method should be called, when user has deleted :ref:`EntityCollection<class_EntityCollection>` from scene.

.. _class_method_SceneEvents_onCollectionOBJloaded:

+------------------------------------------------------------------------------------------------------------------+
| void onCollectionOBJloaded(const :ref:`EntityCollection<class_EntityCollection>` & collection) const             |
+------------------------------------------------------------------------------------------------------------------+

Method should be called, when user has loaded some external file into :ref:`EntityCollection<class_EntityCollection>` instance. As a argument
should be passed ``collection`` that has been filled with that external data.

Static Members
--------------

.. _class_member_SceneEvents_s_instance:

+-----------------------------------------------+-------------------------+-------------------------+
| :ref:`static SceneEvents<class_SceneEvents>`  | s_instance              | ``nullptr``             |
+-----------------------------------------------+-------------------------+-------------------------+

:ref:`SceneEvents<class_SceneEvents>` static instance, that allows user to call event from anywhere.

Members
-------

.. _class_member_SceneEvents_m_sceneManager:

+-----------------------------------------------+-------------------------+-------------------------+
| :ref:`SceneManager*<class_SceneManager>`      | m_sceneManager          | ``nullptr``             |
+-----------------------------------------------+-------------------------+-------------------------+

``m_sceneManager`` is a pointer to :ref:`SceneManager<class_SceneManager>` , which allows user to manage scene during execution. This members methods are called in bodies of
:ref:`SceneEvents<class_SceneEvents>` methods.
