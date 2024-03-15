# Variables

Variables in Terraform play a crucial role in making your configurations more adaptable and reusable. They allow you to pass in values from outside your configurations and share data between different parts of your Terraform setup.

## Input Variables

Input variables are like parameters for your Terraform configurations. They let you inject values into your modules or configurations from external sources. You can define input variables either within a module or at the root level of your configuration. Here's how you set up an input variable:

```hcl
variable "example_var" {
  description = "An example input variable"
  type        = string
  default     = "default_value"
}
```

In this setup:

- `variable` declares an input variable named `example_var`.
- `description` gives a human-readable explanation of the variable.
- `type` specifies the data type of the variable (like `string`, `number`, `list`, `map`, etc.).
- `default` provides an optional default value for the variable.

You can then use this input variable within your module or configuration like so:

```hcl
resource "example_resource" "example" {
  name = var.example_var
  # other resource configurations
}
```

Here, `var.example_var` references the input variable.

## Output Variables

Output variables allow you to expose specific values from your module or configuration, making them accessible for use elsewhere in your Terraform setup. Here's how you define an output variable:

```hcl
output "example_output" {
  description = "An example output variable"
  value       = resource.example_resource.example.id
}
```

In this setup:

- `output` declares an output variable named `example_output`.
- `description` provides a description of the output variable.
- `value` specifies the value you want to expose. This can be a resource attribute, a computed value, or any other expression.

You can reference output variables in the root module or in other modules using the syntax `module.module_name.output_name`, where `module_name` is the name of the module containing the output variable.

For instance, if you have an output variable named `example_output` in a module called `example_module`, you can access it in the root module like this:

```hcl
output "root_output" {
  value = module.example_module.example_output
}
```

This enables you to share data seamlessly between different parts of your Terraform configuration, fostering a more modular and maintainable infrastructure-as-code approach.
