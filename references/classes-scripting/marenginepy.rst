
.. _class_MAREnginePy:

MAREnginePy
===========

**MAREnginePy** is an embedded Python module that you can import and use along with MAREngine.

With this module you can modify entities :ref:`TransformComponent<class_TransformComponent>`, :ref:`ColorComponent<class_ColorComponent>`, :ref:`LightComponent<class_LightComponent>`
and :ref:`CameraComponent<class_CameraComponent>` .

I have embedded :ref:`MARMaths<3rdparty_marmaths>` library, components that are above and Entity with its Trampoline.  You can read about Trampolineread in
:ref:`pybind11<3rdparty_pybind11>` documentation.

We have:

* vec3
    * Static methods:
        * normalize(vec3)
    * Methods:
        * add(float)
        * subtract(float)
        * multiply(float)
        * divide(float)
        * add(vec3)
        * subtract(vec3)
        * multiply(vec3)
        * divide(vec3)
        * cross(vec3)
        * dot(vec3)
        * length
    * Members:
        * x     float
        * y     float
        * z     float

* vec4
    * Static methods:
        * normalize(vec4)
    * Methods:
        * add(float)
        * subtract(float)
        * multiply(float)
        * divide(float)
        * add(vec4)
        * subtract(vec4)
        * multiply(vec4)
        * divide(vec4)
        * dot(vec4)
        * length
    * Members:
        * x     float
        * y     float
        * z     float
        * w     float

* mat4
    * Static methods:
        * identity()
        * orthographic(float left, float right, float top, float bottom, float near, float far)
        * perspective(float fov, float aspectRatio, float near, float far)
        * lookAt(vec3 eye, vec3 center, vec3 up)
        * translation(vec3)
        * scale(vec3)
        * rotation(float, vec3)
        * inverse(mat4)
    * Methods:
        * getColumn(int)
        * multiply(vec4)
        * multiply(mat4)

* basic
    * Static methods:
        * square(float)

* trig
    * Static methods:
        * toRadians(float)
        * toDegrees(float)
        * sine(float radians)
        * cosine(float radians)
        * tangent(float radians)

* Transform
    * Members:
        * scale             vec3
        * center            vec3
        * angles            vec3
        * general_scale     float
        * transform         mat4

* Color
    * Members:
        * texture           vec3

* Light
    * Members:
        * ambient       vec3
        * diffuse       vec3
        * specular      vec3
        * constant      float
        * linear        float
        * quadratic     float
        * shininess     float

* Camera
    * Members:
        * p_fov
        * p_aspectRatio
        * p_near
        * p_far
        * o_left
        * o_right
        * o_bottom 
        * o_top
        * o_near
        * o_far

* Entity
    * Methods:
        * start()
        * update()
    * Members:
        * transform
        * light
        * camera
        * color