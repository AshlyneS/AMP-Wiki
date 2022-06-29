ADS (Application Deployment Service) is AMPs central management system for provisioning and providing access to server instances. It has 4 different deployment modes depending on how it's going to be used. Standalone, Controller, Target and Hybrid.

When setting up ADS, the default is Standalone. If you are using a single computer/VPS for AMP - this is the option you should select.

# Standalone

Standalone mode is used when you're deploying AMP on just a single computer/VPS. ADS provides management and authentication services for all of the local instances and cannot have additional targets registered to it and can only create instances locally.

# Controller

When configured as a Controller, ADS provides authentication and centralized management services for other systems that are running ADS in Target mode. Unlike the other modes, it cannot create local application instances (except Template instances) and other targets/instances rely on it for authentication. Part of its role is to delegate instance creation to remote targets.

When another instance is dependent on a controller it can continue to function in its absence, this includes activities running its application and executing scheduled tasks. However without the controller users will not be able to log into its API/Panel and manage it.

Communication between the controller and remote targets/instances is two way, so each side needs to be able to establish connections to the other.

# Target

ADS Targets can create and provide information about local instances under the instruction of a remote controller. They are dependent on the controller they are registered with for authentication and management services.

# Hybrid

Hybrid instances function like both a target and a controller at the same time. It can create instances locally, provides management and authentication services, but can also delegate instance creation to remote targets. Generally speaking this mode is advised against.