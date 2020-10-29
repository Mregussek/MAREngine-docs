
.. _class_PythonScript:

PythonScript
============

PythonScript is a class that defines Python module in C++ with embedded interpreter.

Static Public Methods
---------------------

.. _class_method_PythonScript_appendCurrentPath:

+--------------------------------------+
| static void appendCurrentPath()      |
+--------------------------------------+

Starts static interpreter and then appends current path, which is ``.`` to embedded intepreter.

.. _class_method_PythonScript_changeSlashesToDots:

+-----------------------------------------------------------------+
| static std::string changeSlashesToDots(std::string script)      |
+-----------------------------------------------------------------+

In given ``script`` variable, which is path to script, method is changing all slashes to dots. Example: "/some/path/file.py"  --->  ".some.path.file.py"

.. _class_method_PythonScript_getModuleFromPath:

+---------------------------------------------------------------+
| static std::string getModuleFromPath(std::string script)      |
+---------------------------------------------------------------+

From given ``script`` variable, which is path to script with dots instead of slashes, method is returning module.
Example: ".some.path.file.py" ---> "file"

Public Methods
--------------

.. _class_method_PythonScript_loadScript:

+--------------------------------------------------+
| void loadScript(std::string path_to_script)      |
+--------------------------------------------------+

Method is loading script from given ``path_to_script`` and imports module to :ref:`m_scriptModule<class_member_PythonScript_m_scriptModule>` variable. If it is its first run
sets :ref:`m_initialized<class_member_PythonScript_m_initialized>` to ``true``. Creates new instance of loaded class from module to 
:ref:`m_module<class_member_PythonScript_m_module>` variable.

.. _class_method_PythonScript_start:

+-------------------------------------------------------------------------+
|  void start(const :ref:`ecs::Entity<class_Entity>` & entity) const      |
+-------------------------------------------------------------------------+

Calls ``start()`` from class in module. Firstly it is initialized with values from given ``entity``.

.. _class_method_PythonScript_update:

+-------------------------------------------------------------------------+
| void update(const :ref:`ecs::Entity<class_Entity>` & entity) const      |
+-------------------------------------------------------------------------+

Calls ``update()`` from class in module. It starts with loading values from given ``entity`` (in order to do something in Editor during PlayMode),
then it calls ``update()``, at the end we are loading values from Python module into given ``entity``, that can be now rendered with data after update.

Members
-------

.. _class_member_PythonScript_m_scriptModule:

+--------------------------------------------------------------+
| :ref:`py::module<class_pybind11_module>` m_scriptModule      |
+--------------------------------------------------------------+

Member for holding imported module. 

.. _class_member_PythonScript_m_module:

+--------------------------------------------------------+
| :ref:`py::object<class_pybind11_object>` m_module      |
+--------------------------------------------------------+

Member for holding loaded class from module.

.. _class_member_PythonScript_m_initialized:

+----------------------+-----------------+
| bool m_initialized   |  { false }      |
+----------------------+-----------------+

Member, from which we can know that ``this`` script was initialized before.