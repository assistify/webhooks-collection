# Welcome to Assistifys Webhooks-Collection!
We collect webhooks for Assistify here, which are interesting in a corporate environment.

Integrating other systems with Assistify normally requires to set up webhooks. Also, there are other use cases, where
webhooks help implementing special behaviour of the chat, for example initiatng actions or actively fetch information
in a dialog.

We found a couple of webhooks that are actually used and can help others doing the same in their use case. Most of them
simply receive information that is then displayed in a certain channel to inform the members of this channel. The
incoming webhook is in this case very simple, it only needs a name and the name of the destination channel. The hook
URL is then used in the system which in case the event occurs. Typical use cases are source repositories, build systems
in CI/CD pipelines or monitoring services, but also social media like Twitter, which can help receiving user compaints
early and reduce the risk of reputation impact.

## Source repositories
- [GitLab](GitLab.md)
- [GitHub](https://rocket.chat/docs/administrator-guides/integrations/github/)

## Build systems / Pipelines
- [Jenkins](https://rocket.chat/docs/administrator-guides/integrations/jenkins/)

## Project manangement
- [Jira](https://rocket.chat/docs/administrator-guides/integrations/jira/)

## Monitoring
- [Instana](Instana.md)
- [Prometheus](https://github.com/pavel-kazhavets/AlertmanagerRocketChat)
- Elasticsearch Free space alert

## Social Media
- [Twitter](Twitter.md)

## Fun
- [Giphy](https://rocket.chat/docs/administrator-guides/integrations/giphy/)

## Other
- [Simple polls](Poll.md)
- [Connect channels between Assistify installations](ConnectedChannels.md)
