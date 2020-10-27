
.. _class_Vertex:

Vertex
======

Vertex defines, what information MAREngine needs for proper rendering.

Definition:

.. code-block:: cpp

    struct Vertex {
		maths::vec3 position;
		maths::vec3 lightNormal;
		maths::vec2 textureCoordinates;
		float shapeID;
	};


Members
-------

.. _class_member_Vertex_position:

+--------------------------------------------------------------+
| :ref:`maths::vec3<class_marmaths_vec3>` position             |
+--------------------------------------------------------------+

``position`` is just a point in space, that defines position of this vertex.

.. _class_member_Vertex_lightNormal:

+--------------------------------------------------------------+
| :ref:`maths::vec3<class_marmaths_vec3>` lightNormal          |
+--------------------------------------------------------------+

``lightNormal`` defines how light should bounce from this vertex.

.. _class_member_Vertex_textureCoordinates:

+--------------------------------------------------------------+
| :ref:`maths::vec2<class_marmaths_vec2>` textureCoordinates   |
+--------------------------------------------------------------+

``textureCoordinates`` variable says how some texture can fit that vertex.

.. _class_member_Vertex_shapeID:

+--------------------------------------------------------------+
| float shapeID                                                |
+--------------------------------------------------------------+

``shapeID`` helps creating batch renderer. With that variable in vertices we can render more shapes during one draw call.
