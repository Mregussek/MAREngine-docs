
.. _class_RendererBatch:

RendererBatch
=============

RendererBatch is a renderer, than can draw :ref:`RenderPipeline's<class_RenderPipeline>` data to the screen.

Public Methods
--------------

.. _class_method_RendererBatch_initialize:

+--------------------------------------------+
| void initialize()                          |
+--------------------------------------------+

Method initializes Renderer, prepares buffers for incoming data, loads and compiles shaders.

.. _class_method_RendererBatch_close:

+---------------------------------------+
| void close()                          |
+---------------------------------------+

Method is shutdowning renderer. Deletes all buffers, clears everything.

.. _class_method_RendererBatch_draw:

+------------------------------------------------------------------------------+
| void draw(:ref:`RenderPipeline<class_RenderPipeline>` & renderPipeline)      |
+------------------------------------------------------------------------------+

Method is responsible for drawing data from passed ``renderPipeline``. It iterates through every container that ``renderPipeline`` and draws it to the screen.

Private Methods
---------------

.. _class_method_RendererBatch_drawContainer:

+------------------------------------------------------------------------------------------+
| void drawContainer(const :ref:`RenderConatiner<class_RenderContainer>` & container)      |
+------------------------------------------------------------------------------------------+

Separated method for drawing ``container``. It binds needed buffers and pushes vertices with indices to them.

.. _class_method_RendererBatch_passTexturesToShader:

+-------------------------------------------------------------------------------------------------+
| void passTexturesToShader(const :ref:`RenderConatiner<class_RenderContainer>` & container)      |
+-------------------------------------------------------------------------------------------------+

Method pushes every color, texture2D and Cubemap texture to shader from given ``container``.

.. _class_method_RendererBatch_passLightToShader:

+----------------------------------------------------------------------------------------------+
| void passLightToShader(const :ref:`RenderConatiner<class_RenderContainer>` & container)      |
+----------------------------------------------------------------------------------------------+

Method pushes lights from given ``container`` to shader.

.. _class_method_RendererBatch_passCameraToShader:

+--------------------------------------------------------------------------------------+
| void passCameraToShader(const :ref:`RenderCamera<class_RenderCamera>` * camera)      |
+--------------------------------------------------------------------------------------+

Method pushes ``camera`` to shader.

Members
-------

.. _class_member_RendererBatch_m_buffers:

+-----------------------------------------------------------------------+
| :ref:`platforms::PipelineOpenGL<class_PipelineOpenGL>` m_buffers      |
+-----------------------------------------------------------------------+

Pipeline for OpenGL buffers. 

.. _class_member_RendererBatch_m_shader:

+------------------------------------------------------------------+
| :ref:`platforms::ShaderOpenGL<class_ShaderOpenGL>` m_shader      |
+------------------------------------------------------------------+

Just shader from OpenGL.

