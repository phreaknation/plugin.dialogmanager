# Dialog Manager
By Joel Dies

Demo(Coming Soon)

[Video](https://youtu.be/0RNYi8aXYG4)


**This is not 100% documented but is on its way to being 100% documented.**

Help support these efforts by becoming a [Patreon](https://www.patreon.com/diesoft)

## Including in a project
Include the script into your html page.

Required Modules:

 + [Lodash](lodash.com) [CDNJS](https://cdnjs.cloudflare.com/ajax/libs/lodash.js/4.17.4/lodash.min.js)

```
<script src="/path/to/plugin/lodash.min.js"></script>

<script src="/path/to/plugin/phreaknation.manager.dialog.min.js"></script>
```

In your create of your phaser project.

```
game.plugins.add(PhreakNation.Plugins.DialogManager);
```

#### Example:
```
var config = require('./path/to/config.js');
var manDiag;
(function() {
  'use strict';

  var state = function state(game) {};

  state.prototype = {
    ...
    create: function () {
      ...
      manDiag = this.game.plugins.add(PhreakNation.Plugins.DialogManager);
      manDiag.load(config);
      var Conv = manDiag.get('dialog', 1);
      
      Conv.play();
      
      console.log('[%s]: %s', Conv.actor().name(), Conv.text());
      
      var list = Conv.answers();
      var choice = _.random(0, 2);
      console.log('Options: ', list);
      console.log('Chose: `%s`', list[choice]);
      Conv.choose(choice);
      console.log('[%s]: %s', Conv.actor().name(), Conv.text());

      Conv.next();
      console.log('[%s]: %s', Conv.actor().name(), Conv.text());

      Conv.next();
      console.log('[%s]: %s', Conv.actor().name(), Conv.text());

      list = Conv.answers();
      choice = _.random(0, 2);
      console.log('Options: ', list);
      console.log('Chose: `%s`', list[choice]);
      Conv.choose(_.random(0, 1));
      console.log('[%s]: %s', Conv.actor().name(), Conv.text());

      Conv.next();
      console.log('[%s]: %s', Conv.actor().name(), Conv.text());
      }
      ...
    },
    ...
  };

  window.MyGame.states.MyState = state;
})();
```

### Manager Methods

### version()
Return the plugin version.

#### Example:
```
manDiag.version();
```

### description()
Return a description of this plugin.

#### Example:
```
manDiag.description();
```

### format(text)
Internal Usage. Formats a text based on variables in the string.

#### Example:
```
var str = manDiag.format('Hey there {actor:0x002}, I am doing good.');
// if there was a reference to `actor:0x002` set to `Actor` in the config. See provided config for details
// 'Hey there Actor, I am doing good.'
```

### get(id, type)
Grabs an item from the config.

#### Example:
```
var Conv = manDiag.get(1, 'dialog');
```

### load(config)
Loads a config file.

#### Example:
```
manDiag.load(config);
```

### new()
TBD

#### Example:
```
// TBD
```



### Dialog Methods

### actor()
Gets the active actor.

#### Example:
```
var actor = Conv.actor();
```

### answers()
Gets the list of answers when there is an active question dialog.

#### Example:
```
var answers = Conv.answers();
```

### choose(id)
Chooses an option for the active question dialog

#### Example:
```
Conv.choose(0);
```

### emotion()
Gets the current emotion of the speaking character of the active dialog.

#### Example:
```
var emotion = Conv.emotion();
```

### next()
Loads the next dialog, if any.

#### Example:
```
Conv.next();
```

### play(id)
Initializes the conversation. Pass in an id to target a specific point of the dialog.

#### Example:
```
var Conv = manDiag.get('dialog', 1);
Conv.play();
```

### process(id, type)
Internal Usage. Processes the current dialog.

#### Example:
```
Conv.process(id);
```

### text()
Returns the formated text of the current dialog.

#### Example:
```
Conv.text();
```



### Actor Methods

### name()
Returns the name of the actor.

#### Example:
```
var actor = Conv.actor();
actor.name(); // Returns the actors name;
```
