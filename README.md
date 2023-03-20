## Description
This playbook deploys an S3 bucket using CloudFormation. It includes tasks to generate a CloudFormation template file using Jinja2, create the S3 bucket using CloudFormation, delete the CloudFormation stack, and remove the CloudFormation template file.

## Advantages of Using Jinja2 to Generate CloudFormation Templates
There are several advantages to using Jinja2 to generate CloudFormation templates:

Modularity: Jinja2 allows you to break up your CloudFormation template into reusable components. You can create a separate Jinja2 template for each resource or set of resources, and then use the include statement to include them in your main template. This makes it easier to manage and update your templates over time.

Simpler syntax: Jinja2's syntax is simpler and more readable than CloudFormation's JSON or YAML syntax. This makes it easier to understand and modify your templates, especially if you're not familiar with CloudFormation's syntax.

Dynamic data: Jinja2 allows you to use dynamic data in your templates. For example, you can use Ansible variables to generate the values of your CloudFormation resources. This makes it easier to generate CloudFormation templates that are customized for different environments or use cases.

Conditionals and loops: Jinja2 allows you to use conditionals and loops in your templates. This can be useful for generating CloudFormation resources based on complex conditions or for creating multiple resources based on a single template.

Error checking: Jinja2 performs error checking when it renders templates. This can help you catch errors in your templates before you deploy them to AWS.

Using Jinja2 to generate CloudFormation templates can make it easier to manage and modify your templates over time, and can help you generate more flexible and dynamic templates that can be customized for different environments or use cases. Additionally, Jinja2's simpler syntax and error checking can help you catch errors in your templates before you deploy them to AWS, reducing the risk of errors and downtime.

## Tasks
### Generate CloudFormation template file using Jinja2
This task generates a CloudFormation template file by rendering a Jinja2 template. The template module is used to render the template, with the src parameter specifying the path to the template file and the dest parameter specifying the path where the rendered template will be saved. The bucket_name variable is set to the value of the bucket_name variable for the current environment.

### Create S3 bucket using CloudFormation
This task uses the cloudformation module to create an S3 bucket using CloudFormation. The state parameter is set to present, which tells Ansible to create the stack if it does not exist. The region parameter is set to the value of the region variable for the current environment, and the stack_name parameter is set to the value of the stack_name variable for the current environment. The template parameter specifies the path to the CloudFormation template file that was generated in the previous task. The disable_rollback parameter is set to yes, which tells CloudFormation to not roll back changes if the stack creation fails. The ansible_python_interpreter variable is set to /usr/bin/python3 to specify the Python interpreter that Ansible should use. The AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY environment variables are used to authenticate with AWS.

Delete S3 bucket CloudFormation stack
This task uses the cloudformation module to delete the CloudFormation stack that was used to create the S3 bucket