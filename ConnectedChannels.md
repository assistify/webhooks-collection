# Shared channels

Sharing a channel between multiple Assistify installations actually means to have a channel in both and connecting them
via webhooks. What we need to do is:

1. create the channels in both installations
2. create incoming webhooks for each channel
3. create outgoing webhooks for each channel sending to its counterpart in the other installation

# Setup

Creating channels and webhooks is really straight forward. The incoming webhook needs a name and requires to
specify the receiving channel name. As the script, you can use something like that:

```JavaScript
class Script {
      process_incoming_request({ request }) {
        return !request.content.bot && request.content.text && {
          content: {
            text: "*@" + request.content.user_name + '*\n' + request.content.text.replace(/^\[\s\]\(http.*?\)\s*/, '')
          }
        }
      }
    }
```

The outgoing webhooks don't need a script. They should listen on new messages in their channel and send them to the
corresponding incoming webhook url.
