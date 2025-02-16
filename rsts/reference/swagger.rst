.. _reference-swagger:

#############################
Flyte API Playground: Swagger
#############################

.. tags:: Basic

Flyte services expose gRPC services for efficient/low latency communication across all services as well as for external clients (FlyteCTL, FlyteConsole, Flytekit Remote, etc.).

The service definitions are defined `here <https://github.com/flyteorg/flyteidl/tree/master/protos/flyteidl/service>`__.
FlyteIDL also houses open API schema definitions for the exposed services:

- `Admin <https://github.com/flyteorg/flyteidl/blob/master/gen/pb-go/flyteidl/service/admin.swagger.json>`__
- `Auth <https://github.com/flyteorg/flyteidl/blob/master/gen/pb-go/flyteidl/service/auth.swagger.json>`__
- `Identity <https://github.com/flyteorg/flyteidl/blob/master/gen/pb-go/flyteidl/service/identity.swagger.json>`__

For convenience, Flyte deployments also ship with a `redocly/redoc <https://github.com/Redocly/redoc>`__ image container to expose swagger UI.
By default, it is only deployed in sandbox deployments.

To view the UI, run the following command:

.. prompt:: bash $

   flytectl sandbox start

Once sandbox setup is complete, a ready-to-explore message is shown:

.. prompt::

   👨‍💻 Flyte is ready! Flyte UI is available at http://localhost:30081/console 🚀 🚀 🎉 


Visit http://localhost:30081/openapi to view swagger UI for the service and documentation of the payload fields. To test, send sample queries!
