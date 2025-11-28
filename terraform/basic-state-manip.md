# Basic state manipulation

Tf uses state as a reference when modifying or updating real-world objects. This process is seamless when the change comes from the config itself, however Tf will lose track of the resource if you change the name of the state module, move it to a different module or change its provider. 

Usually what this means is that Tf will destroy the old module and re-create a new one. Which is behaviour as intended. However in cases where it's important to preserve an existing infrastructure object, you can explicitly tell Tf to associate the resource with a new module. 

You can view all resources associated with a module using the `terraform state list` cmd. This can be filtered using the module or the resource type, or by ID. 

```zsh
 #Filtering by resource
$ terraform state list aws_instance.bar

#Filtering by module
$ terraform state list module.elb 

#Filtering by ID
$ terraform state list -id=sg-1234abcd 
```

- The `terraform state mv` command changes which resource address in your configuration is associated with a particular real-world object. Use this to preserve an object when renaming a resource, or when moving a resource into or out of a child module.

- The `terraform state rm` command tells Terraform to stop managing a resource as part of the current working directory and workspace, without destroying the corresponding real-world object. (You can later use terraform import to start managing that resource in a different workspace or a different Terraform configuration.)