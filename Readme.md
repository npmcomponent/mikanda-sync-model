*This repository is a mirror of the [component](http://component.io) module [mikanda/sync-model](http://github.com/mikanda/sync-model). It has been modified to work with NPM+Browserify. You can install it using the command `npm install npmcomponent/mikanda-sync-model`. Please do not open issues or send pull requests against this repo. If you have issues with this repo, report it to [npmcomponent](https://github.com/airportyh/npmcomponent).*
# sync-model

  Takes a model and updates its values using DOM data.

## Installation

  Install with [component(1)](http://component.io):

    $ component install mikanda/sync-model

## Usage

  ```js
  var syncModel = require('sync-model');
  var model = require('model');

  var el,
      entity,
      EntityClass;
  el = document.querySelector('#my-form');
  EntityClass = model(...)
    .use(
      syncModel({
        date: function(value) {
          return new Date(value);
        }
      })
    )
    .attr('my-attr', { type: 'string', format: 'date' });
  entity = new EntityClass(...);
  entity.syncWith(el);
  ```

## API

### SyncModel([handlers])

  Initialize the plugin.  `handlers` is an optional array with format
  handlers.  Format handlers are functions which are called to convert
  values of a given format to their proper representation.  They
  should have the following definition:

  ```js
  function myHandler(value) {

    // convert value to a representation

    return convert(value);
  }
  ```

  The object looks like this:

  ```js
  {
    '<format-name>': function(value) {},
    ...
  }
  ```

### Model#syncWith(el)

  Synchronizes the model with the data in the `DOMElement` `el`.

## License

  MIT
