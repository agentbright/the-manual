Environments
============

We use the following environments:

Development
-----------
* Local environment

Test
----
* To run tests

Staging
-------
* Any feature branch that has been deployed using Instapusher uses the staging
  environment
* A permanent staging environment is located at http://agentbright.us
* After each deployment, the database is reset and populated from [setup.rake](https://github.com/agentbright/agent-bright/blob/master/lib/tasks/setup.rake)

Acceptance
----------
* http://agent-bright-beta.herokuapp.com
* Database does not reset after each build

Production
----------
* http://beta.agentbright.com
