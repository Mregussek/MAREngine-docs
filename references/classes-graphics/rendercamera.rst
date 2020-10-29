.. _class_RenderCamera:

RenderCamera
============

RenderCamera is an abstraction for Model-View-Projection matrices. It defines an eye and camera in order to watch scene.

Because it does some math stuff, I created 3 typedefs:

* :ref:`mar::maths::Trig<class_marmaths_trig>` to trig
* :ref:`mar::maths::vec3<class_marmaths_vec3>` to vec3
* :ref:`mar::maths::mat4<class_marmaths_mat4>` to mat4

Getters
-------

.. _class_method_RenderCamera_getProjection:

+------------------------------------------------------------------------------------------------+
| const :ref:`maths::mat4<class_marmaths_mat4>` & getProjection() const                          |
+------------------------------------------------------------------------------------------------+

Returns const reference to :ref:`m_projection<class_member_RenderCamera_m_projection>` variable.

.. _class_method_RenderCamera_getView:

+------------------------------------------------------------------------------------------+
| const :ref:`maths::mat4<class_marmaths_mat4>` & getView() const                          |
+------------------------------------------------------------------------------------------+

Returns const reference to :ref:`m_view<class_member_RenderCamera_m_view>` variable.

.. _class_method_RenderCamera_getModel:

+-------------------------------------------------------------------------------------------+
| const :ref:`maths::mat4<class_marmaths_mat4>` & getModel() const                          |
+-------------------------------------------------------------------------------------------+

Returns const reference to :ref:`m_model<class_member_RenderCamera_m_model>` variable.

.. _class_method_RenderCamera_getMVP:

+-----------------------------------------------------------------------------------------+
| const :ref:`maths::mat4<class_marmaths_mat4>` & getMVP() const                          |
+-----------------------------------------------------------------------------------------+

Returns const reference to :ref:`m_mvp<class_member_RenderCamera_m_mvp>` variable.

.. _class_method_RenderCamera_getPosition:

+----------------------------------------------------------------------------------------------+
| const :ref:`maths::vec3<class_marmaths_vec3>` & getPosition() const                          |
+----------------------------------------------------------------------------------------------+

Returns const reference to :ref:`m_position<class_member_RenderCamera_m_position>` variable.

Public Methods
--------------

.. _class_method_RenderCamera_calculatePerspective:

+--------------------------------------------------------------------------------------------------------------------+
| void calculatePerspective(float zoom, float aspectRatio, float nearPlane, float farPlane)                          |
+--------------------------------------------------------------------------------------------------------------------+

Calculates new projection matrix - perspective one - and saves it into :ref:`m_projection<class_member_RenderCamera_m_projection>` variable.

.. _class_method_RenderCamera_calculateOrthographic:

+---------------------------------------------------------------------------------------------------------------------------------------+
|void calculateOrthographic(float left, float right, float top, float bottom, float nearPlane, float farPlane)                          |
+---------------------------------------------------------------------------------------------------------------------------------------+

Calculates new projection matrix - orthographic one - and saves it into :ref:`m_projection<class_member_RenderCamera_m_projection>` variable.

.. _class_method_RenderCamera_calculateView:

+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| void calculateView(:ref:`maths::vec3<class_marmaths_vec3>` position, :ref:`maths::vec3<class_marmaths_vec3>` lookAt, :ref:`maths::vec3<class_marmaths_vec3>` up)    |
+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Calculates new view matrix and saves it into :ref:`m_view<class_member_RenderCamera_m_view>` variable, also it assigns new camera position to :ref:`m_position<class_member_RenderCamera_m_position>`.
``position`` argument stands for new camera position, lookAt vec3 argument defines, where the camera should look at, and ``up`` argument says, where is "up", where heaven is.

.. _class_method_RenderCamera_calculateModel:

+-------------------------------------------------------------------------------------------+
| void calculateModel(:ref:`maths::vec3<class_marmaths_vec3>` arg)                          |
+-------------------------------------------------------------------------------------------+

Calculates new model matrix and saves it into :ref:`m_model<class_member_RenderCamera_m_model>` variable.

.. _class_method_RenderCamera_recalculateMVP:

+------------------------------------------------+
| void recalculateMVP()                          |
+------------------------------------------------+

Calculates new Model-View-Projection matrix from :ref:`m_projection<class_member_RenderCamera_m_projection>` and :ref:`m_view<class_member_RenderCamera_m_view>`
product. Saves result into :ref:`m_mvp<class_member_RenderCamera_m_mvp>` variable.

.. _class_method_RenderCamera_calculateCameraTransforms:

+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| void calculateCameraTransforms(const :ref:`ecs::TransformComponent<class_TransformComponent>` & transform, const :ref:`ecs::CameraComponent<class_CameraComponent>` & camera)   |
+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Method is building new Model-View-Projection matrices from given ``transform`` and ``camera`` components. Using this data MAREngine calculates completely new camera.

Members
-------

.. _class_member_RenderCamera_m_model:

+---------------------------------------------------+
| :ref:`maths::mat4<class_marmaths_mat4>` m_model   |
+---------------------------------------------------+

Variable to define scene in world space using Model matrix.

.. _class_member_RenderCamera_m_view:

+------------------------------------------------------+
| :ref:`maths::mat4<class_marmaths_mat4>` m_view       |
+------------------------------------------------------+

Variable to define scene in view space using View matrix.

.. _class_member_RenderCamera_m_projection:

+-----------------------------------------------------------+
| :ref:`maths::mat4<class_marmaths_mat4>` m_projection      |
+-----------------------------------------------------------+

Variable to define scene in clip using Projection matrix.

.. _class_member_RenderCamera_m_mvp:

+--------------------------------------------------+
| :ref:`maths::mat4<class_marmaths_mat4>` m_mvp    |
+--------------------------------------------------+

Multiplication result of ``m_projection`` * ``m_view``.

.. _class_member_RenderCamera_m_position:

+---------------------------------------------------------+
| :ref:`maths::mat4<class_marmaths_mat4>` m_position      |
+---------------------------------------------------------+

Current camera position.