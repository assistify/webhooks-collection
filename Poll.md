# Simple polls

A Webhook can be used to ask your fellow channel members about a couple of alternative options. This is done by
entering a question beginning with a keyword and some answer options like this:

    !poll "Where do we want to go for the team event?" "To the pub" "Cooking event" "Laser tag"

Members answer by clicking on pre-defined reaction icons.

## Setting up the integration

Just create an outgoing web hook listening on messages in all required channels, choose a trigger word ('!poll' in the
example above) and insert and activate the
[Javascript from this Gist](https://gist.githubusercontent.com/sampaiodiego/db4b60717e7ac0051024dde23c6a902e/raw/756c18109e327fd5dca6412faa7c819af5f816c2/Rocket.Chat%2520-%2520poll%2520bot.js).
You also need to add a URL (which is never called because the Javascript prevents it), it could, for example, be 'http://example.com'
