## Operationally Ready

A challenge in the world of consulting is that you will often work on developing a system, but only infrequently have direct experience with what is required to care for a system once it has moved to production. Experiencing production support allows you to see and understand dimensions of software development that you cannot experience firsthand during an exclusively development-oriented engagement.

Our goal here is to explain some challenges of supporting production code, with an eye towards helping you understand how to write better code that can function well in a production environment without introducing an undue operational burden. Some key areas of focus are:

1. Consider your documentation needs
2. Write code that is serviceable in a production environment
3. Write code that is maintainable over time


### Documentation
The intent of the Software Engineering Principles is to focus on the delivery of quality software, but we would be remiss to not address some of the particularly acute needs of documentation for production delivery.

There are two dimensions of the documentation space for production code:

1. Change Management requirements peculiar to a particular customer
2. Runbook and Playbook information needed for operational support processes

**Change Management** documentation will vary from customer customer site. Sometimes this documentation is genuinely useful and well considered, sometimes this documentation is less useful for the particulars of your impelementation. In either case, it is something that is typically reqiured to move your code into production. Check with your delivery manager to ensure that the level of documentation required is within the scope of Concord's engagement, but generally this documentation is a blocker to deployment and therefore required -- it is rare that you will be able to get an exemption at a large client from this procedural documentation. The best course of action is to (a) ensure the documentation is within Concord's scope, and (b) understand the intended need and target audience of the document to produce a useful artifact.

**Runbook and Playbook information** documents the correct way to operate the system. How do you gracefully stop the system? Are there any order dependencies you need to consider when you are starting the software? Are there operational scripts for managing the system, and where are they located? Runbooks and Playbooks explain the proper operation of your system, and help ensure consistency in the operational environment. 

1. Runbooks explain the proper way to start the system, stop the system, and perform any routine maintenance such as data backups or archival
2. Playbooks explain operational responses in exceptional circumstances. If an error occurs, where do you look for diagnostic information? If a particular known error condition occurs, how do you recover?

Without this information, the system will suffer from inconsistent operating procedures and errors introduced as an artifact of improper usage. Even if the core software is well-written, the reputaton of the system will be damaged by outages and errors that could have been avoided by providing proper operating instructions.

### Serviceability


### Maintainability


