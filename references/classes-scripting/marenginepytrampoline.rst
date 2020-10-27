
.. _class_MAREnginePyTrampoline:

MAREnginePyTrampoline
=====================

In order to make inheritance with :ref:`pybind11<3rdparty_pybind11>` we need to make trampoline classes for Entity and for overloaded methods.

.. _class_PyEntity:

PyEntity
--------

``PyEntity`` is a class, which is used in :ref:`MAREnginePy<class_MAREnginePy>` embedded module. It defines 4 members:

* :ref:`ecs::TransformComponent<class_TransformComponent>` transform;
* :ref:`ecs::LightComponent<class_LightComponent>` light;
* :ref:`ecs::CameraComponent<class_CameraComponent>` camera;
* :ref:`ecs::ColorComponent<class_ColorComponent>` color;

and 2 methods, which can be inherited and overrided in python file:

* virtual void start()
* virtual void update()

.. _class_PyTrampoline:

PyTrampoline
------------

This is the trampoline for PyEntity's virtual methods. It inherits from PyEntity and overrides its ``start()`` and ``update()`` methods.
 They are overrided for proper usage in :ref:`MAREnginePy<class_MAREnginePy>` .