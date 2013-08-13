# Meteor JS
###Tom Coleman

@tmeasday

DiscoverMeteor.com



## Meteor is a:
<p class="fragment">All-JavaScript</p>
<p class="fragment">Realtime</p>
<p class="fragment">Simple</p>
###Web Framework



## Meteor is All-JS
Front- _and_ Back-end have the same language (and code!):

```js
// client code

'click .delete': function() {
  if (user.canDelete(post)) 
    Meteor.call('deletePost', user, post);
}

```

```js
// server code

Meteor.methods({
  deletePost: function(user, post) {
    if (! user.canDelete(post)) 
      throw "Can't delete that post!";
  }
});

```



## Meteor is All-JS
Front- _and_ Back-end use the same APIs:

```js
// client code

'click .delete': function() {
  var post = Posts.findOne(id);
}

```

```js
// server code

Meteor.methods({
  deletePost: function(user, id) {
    var post = Posts.findOne(id);
  }
});

```



## Meteor is All-JS
Front- _and_ Back-end use the same templates:

```handlebars
{{#if showPosts}}
  {{#each posts}}
    <a href="{{pathFor 'showPost'}}">{{title}}</a>
  {{/each}}
{{/if}}

```

<p class="fragment">Actually, you can't do this on the server, **YET**.</p>



## Meteor is All-JS
**Smart Packages** can install code both on the client and the server:

```bash
meteor add accounts-ui
```

Adds: 

  - account security on the server
  - login UI on the client



## Meteor is Realtime
### Mongo-backed collections with automatic sync.




## Meteor is Realtime
- No more REST/SOAP/HTTP APIs
- Stop thinking about the client-server interface
- Stop thinking about data format



## Meteor is Realtime
### Latency Compensation means _instant_ updates



## Meteor is Realtime
### Security is baked into the framework
```js
mrt add accounts-base
```



## Meteor is Simple
### Mongo API available everywhere
```js
Posts.find({author: 'Tom Coleman'}).fetch()
```

- On the server, a sychronous Mongo API
- On the client, a in-memory Mongo cache (minimongo)



## Meteor is Simple
### Publications and Subscriptions control data distribution
```js
// Server

Meteor.publish('postsSince', function(date) {
  return Posts.find({authorId: this.userId, createdAt: {$gt: date}});
});
```

```js
// Client

Meteor.subscribe('postsSince', new Date);
```



## Meteor is Simple
Declarative Templating means dealing with data changes is easy.



## Meteor is Simple
Realtime functionality comes "for free".
```bash
mrt add presence
```


# Thanks!