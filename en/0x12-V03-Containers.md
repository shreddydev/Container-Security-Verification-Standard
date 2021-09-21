# V3: Containers

## Control Objective

The main component of container-based solutions are the containers themselves. Not only do they contain services and application logic but also interact with other systems and containers to exchange data that is often sensitive and demands accurate protection.

Ensure that a verified container solution satisfies the following high level requirements:

* Ensure that the containers run with the least possible privileges.
* Harden services inside the container and minimize the attack surface.
* Leverage security features of the container technology in use.

## Security Verification Requirements

| # | Description | L1 | L2 | L3 | Since |
| --- | --- | --- | --- | -- | -- |
| **3.1** | Verify that the root user isn't used within containers except during initialization and privileges are dropped on completion. |  | ✓ | ✓ | 1.0 |
| **3.2** | Verify that user namespacing is enabled. |  | ✓ | ✓ | 1.0 |
| **3.3** | Verify that within each container image, a new user is created, which is then used to perform all operations within the container. |  |  | ✓ | 1.0 |
| **3.4** | Verify that syscalls from containers are restricted by applying a specific (non-standard) _seccomp_- or _AppArmor_-profile to each container, based on the needs of the container. |  |  | ✓ | 1.0 |
| **3.5** | Verify that containers cannot be granted any additional privileges during their runtime by setting the appropriate values to flags (allowPrivilegeEscalation, defaultAllowPrivilegeEscalation). | ✓ | ✓ | ✓ | 1.0 |
| **3.6** | Verify that all base images are explicitly specified, using their hash instead of name and tag. |  |  | ✓ | 1.0 |
| **3.7** | Verify that the signature of each image is verified before productive usage. | |  | ✓ | 1.0 |
| **3.8** | Verify that only required software packages are installed in images. |  | ✓ | ✓ | 1.0 |
| **3.9** | Verify that the root file system is mounted in read-only mode. |  | ✓ | ✓ | 1.0 |
| **3.10** | Verify that after a container has been actively accessed (e.g., for troubleshooting), it's deleted and replaced by a new instance (container) of the image. |  | ✓ | ✓ | 1.0 |
| **3.11** | Verify that Dockerfiles use the `COPY` directive instead of the `ADD` directive unless the source is fully trusted. | ✓ | ✓ | ✓ | 1.0 |
| **3.12** | Verify that remote management services such as SSH or RDP are disabled or not even installed within containers. | ✓ | ✓ | ✓ | 1.0 |
| **3.15** | Verify that the network socket of the node isn't mounted inside any container directly, unless it is used for monitoring or administration. If access to the network socket is required, check if read-only access is sufficient and limit the access of the container accordingly. | ✓ | ✓ | ✓ | 1.0 |
| **3.16** | Verify that all images used are signed by a trusted notary. |  |  | ✓ | 1.1 |