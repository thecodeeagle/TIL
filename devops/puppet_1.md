# Puppet

Have been using Puppet for a long time now, let's understand it better.

Puppet is an SCM tool (Software - Configuration - Management) that follows a declarative syntax.

**What's a Declarative Syntax**
focuses on describing the desired outcome or state of a system without explicitly detailing the step-by-step instructions to achieve it.

Like saying "what" you want, not "how" to get there.
The control flow is abstracted and managed by the system, its like a higher level language, closer to the problem domain. 

Coming back to Puppet, it has its own Ruby based Domain Specific Language (that's why we write spec tests in .rb) to express the desired state of the system.
Model driven approach - Infrastructure as Code

## Master Agent Communication

Puppet architecture consists of two entities - puppet agent and puppet master. 

In short
Puppet agent --> requests master certificate to puppet master, which sends the same.

Similarly, Puppet master --> requests for slave certificate from puppet agent, who sends the same.

Then puppet agent can ask for data from master, which is sent across by it.

## Resource Abstraction

 - **File:** Ruby
 - **Package:** Apt, Yum, Gems, RPM, Deb
 - **Service:** Redhat, Launchd, SMF, Debian
 - **User:** Useradd, Ldap, Netinfo

## Terminologies

 1. **Resource :** A unit of configuration. State is managed by puppet.
 2. **Resource Declaration:** Fragment of puppet code --> details the desired state of a resource and instructs puppet to manage it.
 3. **Manifest:** Code written in puppet language, ends with .pp extension. Can declare resources and classes, set variables, evaluate functions, and define classes and nodes.
 4. **Templates:** Partial document, gets filled with data from variables. Used for --> generating configuration files tailored to an individual system.
 5. **Modules:** Collection of classes, resource types, files, functions and templates, organized around a particular purpose. Modules can be shared through puppet forge.
 6. **Environment:** An isolated group of agent nodes that a master can serve with its own main manifest and set of modules.
 7. **Tasks:** Single action you can run on a target machine to make as-needed changes.
 8. **Plans**: Set of tasks that can be combined with other logic.