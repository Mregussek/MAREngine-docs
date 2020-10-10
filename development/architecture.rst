Architecture
============

.. seealso::

    This page describes the MAREngine's architecture. From this site you can learn how everything works.
    There are only the most important information, that you need to know for proper understanding MAREngine workflow.


Namespaces
----------

mar
~~~

**mar** is the main namespace for everything. mar brings together all the other namespaces that are responsible for specific engine elements, such as:

* Entity-Component-System (`mar::ecs <https://marengine-docs.readthedocs.io/en/latest/references/namespaces/ecs.html>`__)
* Graphics (`mar::graphics <https://marengine-docs.readthedocs.io/en/latest/references/namespaces/graphics.html>`__)
* Scripting Module for Python (`mar::scripting <https://marengine-docs.readthedocs.io/en/latest/references/namespaces/scripting.html>`__)
* GUI Editor (`mar::editor <https://marengine-docs.readthedocs.io/en/latest/references/namespaces/editor.html>`__)
* LayerStack (`mar::layers <https://marengine-docs.readthedocs.io/en/latest/references/namespaces/layers.html>`__)
* Window and Input (`mar::window <https://marengine-docs.readthedocs.io/en/latest/references/namespaces/window.html>`__)
* 3rd_party dependencies such as OpenGL, GLFW, Vulkan (`mar::platforms <https://marengine-docs.readthedocs.io/en/latest/references/namespaces/platforms.html>`__)
* Logging and debugging information (`mar::debug <https://marengine-docs.readthedocs.io/en/latest/references/namespaces/debug.html>`__)


General
-------

The most important concepts
~~~~~~~~~~~~~~~~~~~~~~~~~~~

* Entity (Can be found in: `mar::ecs <https://marengine-docs.readthedocs.io/en/latest/references/namespaces/ecs.html>`__)



* EntityCollection (Can be found in: `mar::ecs <https://marengine-docs.readthedocs.io/en/latest/references/namespaces/ecs.html>`__)



* Components (Can be found in: `mar::ecs <https://marengine-docs.readthedocs.io/en/latest/references/namespaces/ecs.html>`__)



* Scene (Can be found in: `mar::ecs <https://marengine-docs.readthedocs.io/en/latest/references/namespaces/ecs.html>`__)



* SceneManager (Can be found in: `mar::ecs <https://marengine-docs.readthedocs.io/en/latest/references/namespaces/ecs.html>`__)



* RenderPipeline (Can be found in: `mar::graphics <https://marengine-docs.readthedocs.io/en/latest/references/namespaces/graphics.html>`__)



* RendererBatch (Can be found in: `mar::graphics <https://marengine-docs.readthedocs.io/en/latest/references/namespaces/graphics.html>`__)



