---
title: "Interpolation in Terraform"
datePublished: Wed Jul 05 2023 16:23:30 GMT+0000 (Coordinated Universal Time)
cuid: cljpxhjad000209l44mo2bypp
slug: interpolation-in-terraform
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688574132179/7087b921-6f8d-4b7e-8350-a4794cb946f0.jpeg
tags: devops, terraform, iac, devops-articles, trainwithshubham

---

![Getting Started with Terraform in 5 Minutes – Collabnix](https://usercontent.one/wp/collabnix.com/wp-content/uploads/2021/11/Screen-Shot-2021-11-27-at-4.57.02-PM.png align="left")

1. Variable Interpolation:
    
    * `${var.variable_name}`: Interpolates the value of a variable.
        
2. Resource Attribute Interpolation:
    
    * `${resource_type.resource_name.attribute}`: Interpolates the value of a specific attribute of a resource.
        
3. Data Attribute Interpolation:
    
    * `${`[`data.data`](http://data.data)`_`[`type.data`](http://type.data)`_name.attribute}`: Interpolates the value of a specific attribute of a data source.
        
4. Output Interpolation:
    
    * `${output.output_name}`: Interpolates the value of an output variable.
        
5. String Interpolation:
    
    * `"${expression}"`: Interpolates a string with an expression.
        
6. List Interpolation:
    
    * `[element1, element2, ...]`: Interpolates a list of elements.
        
7. Map Interpolation:
    
    * `{key1 = value1, key2 = value2, ...}`: Interpolates a map of key-value pairs.
        
8. Conditional Interpolation:
    
    * `condition ? true_val : false_val`: Interpolates a value based on a condition.
        
9. Numeric Interpolation:
    
    * Arithmetic operations: `+`, `-`, `*`, `/`, `%`: Interpolates the result of arithmetic operations on numbers.
        
10. Splat Expression Interpolation:
    
    * `${resource_type.resource_name.*.attribute}`: Interpolates a list of values for a specific attribute of multiple resources.
        
11. Count Interpolation:
    
    * `${count.index}`: Interpolates the current index value when using resource or module count.
        
12. Element Interpolation:
    
    * `${list[index]}`: Interpolates a specific element from a list based on the index.
        
13. Lookup Interpolation:
    
    * `${lookup(map, key, default)}`: Interpolates the value of a key in a map and provides a default value if the key doesn't exist.
        
14. File Interpolation:
    
    * `${file(path)}`: Interpolates the content of a file at the specified path.
        
15. Templatefile Interpolation:
    
    * `${templatefile(path, vars)}`: Interpolates the content of a template file at the specified path, replacing variables with values from the `vars` map.
        
16. Join Interpolation:
    
    * `${join(delimiter, list)}`: Interpolates a string by joining elements of a list with the specified delimiter.
        
17. Lower and Upper Case Interpolation:
    
    * `${lower(string)}`: Interpolates a lowercase version of the given string.
        
    * `${upper(string)}`: Interpolates an uppercase version of the given string.
        
18. Regex Replace Interpolation:
    
    * `${replace(string, regex, replacement)}`: Interpolates a string by replacing substrings matching a regex pattern with a specified replacement.
        
19. JSON Interpolation:
    
    * `${jsonencode(data_structure)}`: Interpolates a JSON-encoded string representation of a data structure.
        
20. Terraform Function Interpolation:
    
    * `${function_name(arg1, arg2, ...)}`: Interpolates the result of a Terraform function call with the specified arguments.