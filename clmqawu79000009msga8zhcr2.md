---
title: "Ansible Molecule"
datePublished: Tue Sep 19 2023 12:38:26 GMT+0000 (Coordinated Universal Time)
cuid: clmqawu79000009msga8zhcr2
slug: ansible-molecule
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1695126492259/edcbe0b5-a1bc-4085-96ac-ae2a185f1dc0.png
tags: aws, ansible, devops, 90daysofdevops, trainwithshubham

---

**Ansible Molecule** is a testing framework for developing and testing Ansible roles and playbooks. It automates the process of spinning up test instances, applying Ansible playbooks, and running tests to ensure that your code works as expected.

***<mark>Ansible Molecule: A DevOps Engineer's Best Friend for Testing Ansible Roles</mark>***

As a DevOps engineer, one of my key responsibilities is to ensure that our infrastructure is deployed and configured consistently and reliably. To do this, I use Ansible, a popular infrastructure automation tool. Ansible roles allow me to encapsulate common tasks and configurations, making them reusable and easier to manage.

However, writing Ansible roles can be challenging, and it's important to test them thoroughly before deploying them in production. This is where Molecule comes in. Molecule is a testing framework for Ansible roles that makes it easy to create and run tests.

In this blog post, I'll give you an overview of Molecule and show you how to use it to test your Ansible roles.

### **<mark>What is Molecule?</mark>**

Molecule is a tool that helps you test your Ansible roles by creating and running test instances. It supports a variety of virtualization providers, including Docker, Vagrant, and LXC. Molecule also integrates with popular testing frameworks, such as ServerSpec and TestInfra.

**<mark>Benefits of using Molecule</mark>**

There are many benefits to using Molecule to test your Ansible roles, including:

* **Improved code quality:** Molecule helps you to identify and fix errors in your Ansible roles before deploying them in production.
    
* **Increased confidence:** By testing your Ansible roles thoroughly, you can be more confident that they will deploy and configure your infrastructure as expected.
    
* **Reduced risk:** By catching errors early, Molecule can help you to reduce the risk of outages and other disruptions.
    

**What are the key components of a testing strategy for Ansible?**

**A:** A comprehensive testing strategy for Ansible typically includes the following components:

1. **Unit Tests**: These focus on testing individual parts of an Ansible role or playbook. For example, testing custom modules, filters, and handlers.
    
2. **Integration Tests**: These verify that different parts of a system work together correctly. This could involve testing the entire playbook or role in a controlled environment.
    
3. **Functional Tests**: These validate that the system behaves as expected in real-world scenarios. This might involve deploying a system and then checking its state.
    
4. **Continuous Integration (CI)**: Integrating testing into a CI/CD pipeline ensures that changes to Ansible code are automatically tested before being deployed.
    

### **Can you explain how you might implement a testing strategy using Molecule?**

**A:** Here's a basic outline:

1. **Install Molecule**: Set up Molecule on your development machine.
    
2. **Create a New Role**: Use `molecule init role <role_name>` to create a new role.
    
3. **Write Tests**: Create tests using a testing framework like Goss or InSpec within the `tests/` directory.
    
4. **Configure Molecule**: Customize the `molecule.yml` file to define the platforms and drivers you want to test on.
    
5. **Run Tests**: Use `molecule test` to initiate the testing process. Molecule will automatically create instances, apply playbooks, and run tests.
    
6. **Integrate with CI/CD**: Set up your CI/CD pipeline to execute Molecule tests whenever changes are pushed to your repository.
    

By following these steps, you establish a robust testing strategy for your Ansible roles or playbooks.

Remember, the specifics may vary based on your organization's requirements and tools in use, but this provides a general framework.

![How to test Ansible and don't go nuts | Lev Goncharov](https://www.goncharov.xyz/it/assets/at_kitchen_2.png?raw=true align="left")

### **Installing Molecule:**

You can install Molecule using pip, the Python package manager:

```plaintext
bashCopy codepip install molecule
```

### **Creating a New Role:**

Let's go through the process of creating a new role and using Molecule to test it.

1. **Create a New Role:**
    

```plaintext
bashCopy codemolecule init role my_role_name
cd my_role_name
```

This command will create the directory structure for a new Ansible role and set up Molecule for testing it.

1. **Directory Structure:**
    

After running the above command, you'll have a directory structure like this:

```plaintext
arduinoCopy codemy_role_name/
├── defaults/
├── files/
├── handlers/
├── meta/
├── tasks/
├── templates/
├── tests/
│   ├── inventory/
│   └── test_default.yml
├── vars/
├── .gitignore
├── .molecule/
│   ├── Dockerfile.j2
│   ├── default/
│   │   ├── converge.yml
│   │   └── molecule.yml
│   └── molecule.yml
├── .travis.yml
├── CHANGELOG.md
├── LICENSE
├── README.md
├── molecule.yml
├── playbook.yml
├── requirements.yml
└── tasks/
    └── main.yml
```

### **Writing Tests:**

Inside the `tests/` directory, you'll find an `inventory/` directory where you can define your test inventory, and a `test_default.yml` file where you can write your tests.

For example, let's write a basic test to check if a package is installed:

```plaintext
yamlCopy code---
- name: Check if package is installed
  hosts: all
  tasks:
    - name: Check if package is installed
      become: yes
      package_facts:
        manager: apt
      assert:
        that:
          - "mypackage" in ansible_facts.packages
```

### **Running Tests:**

You can use the following commands to run tests with Molecule:

* `molecule test`: This command will create a new test environment, apply the playbook, and run the defined tests.
    
* `molecule converge`: Use this command to apply the playbook without running tests. It's useful for iterating on your playbook before running full tests.
    
* `molecule verify`: This command only runs the tests without recreating the environment.
    

**Configuring Molecule:**

You can customize Molecule's behavior by editing the `molecule.yml` file inside the `.molecule/` directory. This file allows you to define the platforms, provisioners, and other options for testing.

### **Example Molecule Configuration:**

Here's an example of a `molecule.yml` file:

```plaintext
yamlCopy code---
dependency:
  name: galaxy
driver:
  name: docker
lint:
  name: yamllint
platforms:
  - name: instance
    image: ubuntu:20.04
provisioner:
  name: ansible
verifier:
  name: testinfra
  lint:
    name: flake8
```

This configuration specifies that Molecule should use Docker for the test environment, use the Ansible provisioner, and use Testinfra for verification.

With Ansible Molecule, you can automate the testing of your roles and playbooks, ensuring that they work reliably across different environments. This helps catch issues early in the development process and provides confidence in your automation code.

### Ansible molecule workflow:

![2015 OpenStack Summit Tokyo - David Lapsley – Cisco – This won't hurt a  bit… Best practices for TDD - YouTube](https://i.ytimg.com/vi/5vKblNaD3fI/maxresdefault.jpg align="left")

1. `molecule.yml`:
    
    * **Purpose**: Configuration file that defines how Molecule operates for a specific role.
        
    * **Integration**: Contains settings for platforms, drivers, provisioners, linting, and verification.
        
    * **Example**:
        
        ```plaintext
        yamlCopy code---
        dependency:
          name: galaxy
        driver:
          name: docker
        platforms:
          - name: instance
            image: ubuntu:20.04
        provisioner:
          name: ansible
        verifier:
          name: testinfra
        ```
        
2. `prepare.yml`:
    
    * **Purpose**: Defines the tasks to prepare the instance for testing.
        
    * **Integration**: Located in the `molecule/<scenario>/` directory, where `<scenario>` is the chosen scenario for testing.
        
    * **Example**:
        
        ```plaintext
        yamlCopy code---
        - name: Prepare instance for testing
          hosts: all
          become: yes
          tasks:
            - name: Install necessary packages
              package:
                name: "{{ item }}"
                state: present
              with_items:
                - python3
        ```
        
3. `converge.yml`:
    
    * **Purpose**: Describes how to apply the role to the instance under test.
        
    * **Integration**: Also located in the `molecule/<scenario>/` directory.
        
    * **Example**:
        
        ```plaintext
        yamlCopy code---
        - name: Converge role
          hosts: all
          become: yes
          gather_facts: yes
          roles:
            - name: your-role-name
        ```
        
4. `verify.yml`:
    
    * **Purpose**: Specifies the tests to run on the converged instance.
        
    * **Integration**: Also located in the `molecule/<scenario>/` directory.
        
    * **Example**:
        
        ```plaintext
        yamlCopy code---
        - name: Verify role
          hosts: all
          become: yes
          tasks:
            - name: Check if service is running
              service:
                name: your-service-name
                state: started
            - name: Check if port is listening
              wait_for:
                host: localhost
                port: 80
                state: started
        ```
        

These files work together to define the workflow for testing an Ansible role using Molecule:

1. `prepare.yml` sets up the environment for testing (e.g., by installing necessary packages).
    
2. `converge.yml` applies the role to the instance.
    
3. `verify.yml` runs tests to validate the role's functionality.
    

The `molecule.yml` file provides the overall configuration for the testing process, including details about platforms, provisioners, drivers, and verifiers. It ties everything together and ensures that Molecule knows how to orchestrate the testing workflow for a specific role.

**Best Strategies and Practices:**

1. **Modular Roles**: Break down complex roles into smaller, reusable components. This makes testing more manageable and promotes reusability.
    
2. **Separate Configuration**: Store configuration values in role defaults or variables, not hardcoded in tasks. This allows you to configure roles differently for different environments during testing.
    
3. **Use Idempotent Tasks**: Ensure that your tasks are idempotent, meaning they can be run multiple times without causing issues. This is crucial for testing and in real-world use.
    
4. **Parameterize Tests**: Use test parameters to make your tests flexible. For example, pass in variables like package names or configuration values as parameters.
    
5. **Linting**: Include linting tools like `ansible-lint` and `yamllint` in your testing process to catch syntax and style issues early.
    
6. **Documentation**: Keep your roles and playbooks well-documented, including in-code comments, README files, and usage examples. Good documentation helps testers and users understand the expected behavior.
    

### **More Testing Examples:**

![How to test Ansible and don't go nuts | Lev Goncharov](https://www.goncharov.xyz/it/assets/at_molecule_unit_2.png?raw=true align="left")

1. **Integration Testing**: Perform integration tests to ensure that your roles work as expected in the context of a full playbook. Here's a sample test for an NGINX role:
    
    ```plaintext
    yamlCopy code---
    - name: Converge role
      hosts: all
      become: yes
      gather_facts: yes
      roles:
        - name: your-role-name
    ```
    
    This test will apply the role to your test instance.
    
2. **Functional Testing**: Write functional tests that validate the system's state after applying a playbook. For example, to ensure that NGINX is serving a webpage:
    
    ```plaintext
    yamlCopy code---
    - name: Check NGINX web page
      hosts: all
      become: yes
      tasks:
        - name: Check if NGINX serves a webpage
          uri:
            url: http://localhost
            status_code: 200
          register: result
        - name: Ensure NGINX serves the expected content
          assert:
            that:
              - "Welcome to NGINX" in result.content
    ```
    
    This test checks if NGINX serves a webpage with the expected content.
    
3. **Parameterized Tests**: Parameterize your tests to ensure your role works with different configurations. For instance, you can pass variables to your test playbook to configure software differently:
    
    ```plaintext
    yamlCopy code---
    - name: Test role with custom configuration
      hosts: all
      become: yes
      roles:
        - name: your-role-name
          vars:
            custom_config_option: "some_value"
    ```
    
    This allows you to test how your role behaves with various configuration settings.
    
4. **Using Multiple Platforms**: Define multiple platforms in your `molecule.yml` file to test your role on different operating systems or versions. This helps ensure cross-compatibility.
    
    ```plaintext
    yamlCopy codeplatforms:
      - name: ubuntu-20.04
        image: ubuntu:20.04
      - name: centos-8
        image: centos:8
    ```
    
5. **Testing Edge Cases**: Don't forget to test edge cases and error scenarios to make your role robust. For instance, test how your role handles situations where a required package is missing or a configuration file is malformed.
    

Remember to continuously integrate testing into your development workflow, preferably using a CI/CD pipeline like Travis CI, Jenkins, or GitLab CI. This ensures that your Ansible roles and playbooks are always tested before deployment.

### **Here are some additional tips for using Molecule:**

* Use Molecule to test your Ansible roles early and often. This will help you to identify and fix errors early on.
    
* Use Molecule to test your Ansible roles on multiple operating systems and versions of Ansible. This will help you to ensure that your roles are compatible with different environments.
    
* Use multiple test scenarios to test different aspects of your Ansible roles. This will help you to catch any potential problems.
    
* Integrate Molecule into your continuous integration (CI) pipeline. This will help you to automate the testing of your Ansible roles and ensure that they are always in a good state.