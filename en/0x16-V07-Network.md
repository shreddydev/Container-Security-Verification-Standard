# V7: Network

## Control Objective

Nearly all modern applications and services aren't monolithic but instead consist of multiple components interacting with each other through network connections. Securing networks is its own security discipline but there are some aspects that container technologies can affect and where they can improve security when using networks.

Ensure that a verified container solution satisfies the following high level requirements:

* Choose a good network driver and configure it correctly.
* Disable unneeded features and apply restrictions.
* Enforce encryption when transferring data over networks.

## Security Verification Requirements

| # | Description | L1 | L2 | L3 | Since |
| --- | --- | --- | --- | -- | -- |
| **7.1** | Verify that a production ready networking driver is used. | ✓ | ✓ | ✓ | 1.0 |
| **7.2** | Verify that a load balancing features is present and active (e.g. by using DNS Round Robin or virtual IPs (VIP)). |  | ✓ | ✓ | 1.0 |
| **7.5** | Verify that network communication between different pods is not possible by default. This can for example be done by using a network plugin which supports this feature. |  | ✓ | ✓ | 1.0 |
| **7.7** | Verify that published ports are assigned to a specific network interface of a node. |  | ✓ | ✓ | 1.0 |
| **7.8** | Verify that management and data/application traffic is separated by different network interfaces. |  |  | ✓ | 1.0 |
| **7.9** | Verify that each application (one or more services) is assigned at least one separate, isolated overlay network in order to ensure Layer 3 segmentation. |  | ✓ | ✓ | 1.0 |
| **7.10** | Verify that encryption between containers or nodes on the overlay network is enabled. |  | ✓ | ✓ | 1.0 |
| **7.11** | Verify that the used subnets do not overlap with other subnets (e.g. overlay networks). | ✓ | ✓ | ✓ | 1.0 |
| **7.12** | Verify that published ports are limited to a necessary minimum. | ✓ | ✓ | ✓ | 1.0 |
