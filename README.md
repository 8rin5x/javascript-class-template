# JavaScript class template

## About

Class template for making a private declaration in JavaScript

## Usage

Create a class template by entering `class:`

``` javascript
const ClassName = (function () {
  // Private modifier
  const _ = new Proxy({}, {
    get: (obj, name) => {
      if (obj[name] === undefined) {
        obj[name] = Symbol(name)
      }
      return obj[name]
    },
    set: () => { }
  })

  // constructor
  function ClassName() {
    
  }

  return ClassName
})()
```

### Template usage example

``` javascript
const Example = (function () {
  // Private modifier
  const _ = new Proxy({}, {
    get: (obj, name) => {
      if (obj[name] === undefined) {
        obj[name] = Symbol(name)
      }
      return obj[name]
    },
    set: () => { }
  })

  // constructor
  function Example(privateValue, publicValue) {
    // private instance
    this[_.privateInstanceName] = privateValue
    // public instance
    this.publicInstanceName = publicValue
  }

  // alias
  const proto = Example.prototype

  // private prototype
  proto[_.privatePrototypeName] = function () {}
  // public prototype
  proto.publicPrototypeName = function () {}

  return Example
})()
```