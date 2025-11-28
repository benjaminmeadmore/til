# Resource Addressing
Terraform uses a state file to associate real-world objects with a remote directory. It then references these resources via address. The resource address of an object is a string that identifies zero or more resource instances in your overall config:

```zsh
[module path][resource spec]
```

## Module path 
A module path addresses a module within a tree of modules. It takes the form:

```zsh
module.module_name[module index]
```

- `module` - Module keyword indicating a child module (non-root). Multiple module keywords in a path indicate nesting.
- `module_name` - User-defined name of the module.
- `[module index]` - (Optional) Index to select an instance from a module call that has multiple instances, surrounded by square bracket characters ([ and ]).

If you perform an operation on a module without specifying a unique resource underneath i.e. `module.foo` then the command applies to every resource within the module, as well as all instances if there are multiple. 

## Resource spec
A resource spec addresses a specific resource instance in the selected module, behaves very similarly to module paths. It has the following syntax:

```zsh
resource_type.resource_name[instance index]
```

- `resource_type` - Type of the resource being addressed.
- `resource_name` - User-defined name of the resource.
- `[instance index]` - (Optional) Index to select an instance from a resource that has multiple instances, surrounded by square bracket characters ([ and ]).