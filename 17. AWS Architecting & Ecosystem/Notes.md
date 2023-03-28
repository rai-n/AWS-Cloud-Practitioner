## Well Architected Framework, General Guiding Principles
* Stop guessing your capacity need, instead use auto scaling
* Test systems at production scale, AWS device farm
* Automate to make architectural experimentation easier or platform as a service such as Beanstalk
* Allow for evolutionary architecture based on changing requirements
* Drive architectures using data based on what you need
* Improve through game days, simulate app for flash sale day. E.g. stress test

## Design principles
* Scalability: vertical & horizontal
* Disposable resources: servers should be disposable and easily configured, back up data and configuration and should be done quickly
* Automation: Serverless, Infrastructure as a service, auto scaling
* Loose coupling: 
1. Monolith, gets bigger, avoid this as it is difficult to maintain and scale
2. Break it down into smaller, loosely coupled components. E.g. microservices or SQS
3. Change in or failure in one component should not cascade to other components
* Think in Services, not Servers
* What Managed services, databases, serverless can i use?


## Well Architecture Framework, 6 pillars
1. Operational Excellence
2. Security
3. Reliable
4. Performance efficiency
5. Cost optimization
6. Sustainability

* Not a balance, they are a synergy