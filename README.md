[![AutoOps](https://github.com/AutoOps/st2/raw/master/AutoOps_logo.png)](https://www.AutoOps.com)


---



### About AutoOps

AutoOps is a platform for integration and automation across services and tools. It ties together your existing infrastructure and application environment so you can more easily automate that environment -- with a particular focus on taking actions in response to events.

AutoOps helps automate common operational patterns. Some examples are:

* **Facilitated Troubleshooting** - triggering on system failures captured by Nagios, Sensu, New Relic and other monitoring, running a series of diagnostic checks on physical nodes, OpenStack or Amazon instances, and application components, and posting results to a shared communication context, like Slack or JIRA.
* **Automated remediation** - identifying and verifying hardware failure on OpenStack compute node, properly evacuating instances and emailing VM about potential downtime, but if anything goes wrong - freezing the workflow and calling PagerDuty to wake up a human.
* **Continuous deployment** - build and test with Jenkins, provision a new AWS cluster, turn on some traffic with the load balancer, and roll-forth or roll-back based on NewRelic app performance data.

AutoOps helps you compose these and other operational patterns as rules and workflows or actions; and these rules and workflows - the content within the AutoOps platform - are stored *as code* which means they support the same approach to collaboration that you use today for code development and can be shared with the broader open source community via [AutoOps Exchange](https://exchange.AutoOps.org).

### Who is using AutoOps?

See the list of known AutoOps [ADOPTERS.md](/ADOPTERS.md) and [Thought Leaders](https://AutoOps.com/AutoOps-thought-leaders/).

### How it works

#### AutoOps architecture

![AutoOps architecture diagram](https://user-images.githubusercontent.com/597113/92291633-6b5aae00-eece-11ea-912e-3bf977aa3cea.png)

AutoOps plugs into the environment via an extensible set of adapters: sensors and actions.

* **Sensors** are Python plugins for inbound integration that watch for events from external systems and fire a AutoOps trigger when an event happens.

* **Triggers** are AutoOps representations of external events. There are generic triggers (e.g., timers, webhooks) and integration triggers (e.g., Sensu alert, JIRA issue updated). A new trigger type can be defined by writing a sensor plugin.

* **Actions** are AutoOps outbound integrations. There are generic actions (SSH, HTTP request), integrations (OpenStack, Docker, Puppet), or custom actions. Actions are either Python plugins, or any scripts, consumed into AutoOps by adding a few lines of metadata. Actions can be invoked directly by user via CLI, API, or the web UI, or used and called as part of automations - rules and workflows.

* **Rules** map triggers to actions (or to workflows), applying matching criterias and map trigger payload data to action inputs.

* **Workflows** stitch actions together into "uber-actions", defining the order, transition conditions, and passing context data from one action to the next. Most automations are multi-step (eg: more than one action). Workflows, just like "atomic" actions, are available in the action library, and can be invoked manually or triggered by rules.

* **Packs** are the units of content deployment. They simplify the management and sharing of AutoOps pluggable content by grouping integrations (triggers and actions) and automations (rules and workflows). A growing number of packs is available on the AutoOps Exchange. Users can create their own packs,  share them on GitHub, or submit them to the AutoOps Exchange organization.

* **Audit trail** is the historical list of action executions, manual or automated, and is recorded and stored with full details of triggering context and execution results. It is also captured in audit logs for integrating with external logging and analytical tools: LogStash, Splunk, statsd, or syslog.

AutoOps is a service with modular architecture. It is comprised of loosely coupled microservice components that communicate over a message bus, and scales horizontally to deliver automation at scale. AutoOps has a full REST API, CLI client, and web UI for admins and users to operate it locally or remotely, as well as Python client bindings for developer convenience.

AutoOps is an established project and remains actively developed by a broad community.

By contributing you agree that these contributions are your own (or approved by your employer) and you grant a full, complete, irrevocable copyright license to all users and developers of the project, present and future, pursuant to the license of the project.
