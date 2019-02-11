# Instana integration

Instana is a monitoring tool that can send information to an incoming webhook in Assistify. To adapt the information
sent by Instana to the display as a message, the incoming webhook should contain a script like this:

```JavaScript
class Script {
  process_incoming_request({request}) {
    const author_icon = 'https://www.instana.com/media/RZ_INSTANA_White_new.svg'
    if (request.content.issue.state === 'OPEN') {
      if (request.content.issue.type === 'issue' || request.content.issue.type === 'incident') {
        return {
          content: {
            attachments: [{
              color: '#FF0000',
              author_name: 'Instana Server',
              author_link: 'https://your-instana-server.url/#/events?timeline.to&timeline.ws=3600000&eventId=' + request.content.issue.id + '&timeline.fm',
              author_icon,
              title: 'Open ' + request.content.issue.type + ' on: ' + request.content.issue.entityLabel + ' - ' + request.content.issue.text,
              title_link: request.content.issue.link,
              text: '' + request.content.issue.suggestion,
              ts: '' + new Date(request.content.issue.start),
              fields: [{
                title: 'EntityType',
                value: '' + request.content.issue.entityType,
                short: false
              },{
                title: 'Calls',
                value: '' + request.content.issue.traceStatistics.callCount,
                short: false
              },{
                title: 'Max. Duration',
                value: '' + request.content.issue.traceStatistics.maxDuration,
                short: false
              },{
                title: 'Mean Duration',
                value: '' + request.content.issue.traceStatistics.meanDuration,
                short: false
              },{
                title: 'Error Rate',
                value: '' + request.content.issue.traceStatistics.meanErrorRate,
                short: false
              },{
                title: 'Priority',
                value: '' + request.content.issue.severity,
                short: false
              }]
            }]
          }
        }
      }
    } else {
      if (request.content.issue.state === 'CLOSED') {
        return {
          content: {
            attachments: [{
              color: '#FF0000',
              author_name: 'Instana IAT Server',
              author_link: 'https://your-instana-server.url/#/events?timeline.to&timeline.ws=3600000',
              author_icon,
              title: 'Closed Incident or Issue',
              title_link: 'https://instana-server-iat-default-ops.dbv-test.comp.db.de/#/events?timeline.to&timeline.ws=3600000&eventId=' + request.content.issue.id + '&timeline.fm',
              text: 'Incident or Issue closed: ' + 'id: ' + request.content.issue.id,
              ts: '' + new Date(request.content.issue.end),
              fields: [{
                title: 'End',
                value: '' + new Date(request.content.issue.end),
                short: false
              }]
            }]
          }
        }
      } else {
        return {
          content: {
            attachments: [{
              color: '#FF0000',
              author_name: 'Instana IAT Server',
              author_link: 'https://your-instana-server.url/#/events?timeline.to&timeline.ws=3600000&eventId=' + request.content.issue.id + '&timeline.fm',
              author_icon,
              title: '' + request.content.issue.type + ' - ' + request.content.issue.text,
              title_link: request.content.issue.link,
              text: '' + request.content.issue.description,
              ts: '' + new Date(request.content.issue.start),
              fields: [{
                title: 'Entity',
                value: '' + request.content.issue.entity,
                short: false
              },{
                title: 'Tags',
                value: '' + request.content.issue.tags,
                short: false
              },{
                title: 'Zone',
                value: '' + request.content.issue.zone,
                short: false
              }]
            }]
          }
        }
      }
    }
  }
}
```
