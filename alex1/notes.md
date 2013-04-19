
### Summary

This DSL combines what I (Alex) see as the best ideas from CFN YAML and Rackspace Heat/DSL,
trying to make a simple, general, and powerful framework.

The core shape of the DSL is:

    name: <name>
    metadata: <map of description, versions, etc>
    components: <map of component-id to component-spec>
    inputs: <map of input-parameter-id to input-parameter-spec>
    outputs: <map of output-parameter-id to output-parameter-spec>

This defines a blueprint which can be re-used, or even imported in
other blueprints.

The **component-spec** is the core, where specs for things like 
servers and load-balancers and tiers are described.
These are defined through **types**, of which Heat provides
a standard library, but there might be extensions in time.
Within this spec, **requirements** can be defined, which again
conform to types provided by Heat and possibly extended:
this provides a way to allow the Heat platform to do auto-wiring
(choosing the most appropriate components) and to configure the
relationship to the auto-wired instance.

For more info on this core idea, see
[Heat/DSL2](https://wiki.openstack.org/wiki/Heat/DSL2),
although note that thinking has changed some since then.


### Recent Updates

* Support for _defining_ **input** parameters is included, based on the existing DSL's.

* A sample syntax for _referencing_ parameters is introduced,
  essentially `{ type: reference, parameter: xxx }`

* A sample syntax for definining **output** attributes is introduced
  (although this is the bit I like least currently) 
