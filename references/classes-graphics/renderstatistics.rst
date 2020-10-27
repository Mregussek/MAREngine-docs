
.. _class_RendererStatistics:

RendererStatistics
==================

It is a struct, that can can tell a word rendering. I believe code is self-explanatory, so there won't be much.

.. code-block:: cpp

    struct RenderStatistics {
		
		RenderStatistics() = default;

		void resetStatistics();             // reset to default values

		uint32_t drawCallsCount{ 0 };
		uint32_t verticesCount{ 0 };
		uint32_t indicesCount{ 0 };
		uint32_t shapesCount{ 0 };
		uint32_t trianglesCount{ 0 };
		uint32_t entitiesCount{ 0 };
		uint32_t entityCollectionsCount{ 0 };
		uint32_t allEntitiesCount{ 0 };

	};