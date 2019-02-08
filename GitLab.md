# GitLab Integration

GitLab is a source repository based on git and a user friendly UI. It is used in larger corporations due to the fact,
that there is an OpenSource version available which can be deployed on premises. Current versions of GitLab have a
component named GitLab-CI, which helps building CI/CD pipelines using worker nodes which are not part of GitLab itself,
but can be separate servers, even AWS EC2 or Kubernetes pods, which are spun up on demand.

Integrations of GitLab in Assistify helps getting information about new commits or failing integration tests in the
pipeline. Therefore, they work by GitLib calling an incoming webhook in Assistify which prints out a message in one of
the channels.

# Setting up the integration

There is a documentation how to setup such a webhook in the
[Rocket.Chat documentation](https://rocket.chat/docs/administrator-guides/integrations/gitlab/).
