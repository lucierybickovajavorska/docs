# How Automatic Scaling Works

Each [service](/documentation/overview/projects-and-services-structure.html#service) you create starts in a non-HA container running on 1 vCPU core with 1 GB RAM and 3 GB of disk space, you get this [for free](/documentation/overview/pricing.html#free-tier-unlimited-projects-and-team-members). Once your application starts requiring more computing power or a bigger disk, Zerops will enable [high availability](/documentation/ha/why-should-i-want-high-availability.html) as the first autoscaling step. For example, your Node.js service will start running on two 1 vCPU / 1GB RAM / 3 GB disk instead of one, your MongoDB will start running on one master and two slaves, each with 1 vCPU / 1 GB RAM / 3 GB disk. After that, Zerops will scale each metric of each container separately, just as your applications will require, always optimized to run as efficiently as possible.

Zerops will automatically change settings of the services to always run as optimally as possible for the given state of horizontal and vertical autoscaling.

### Vertical scaling

Each service starts with the minimum resources required, this usually means 1 vCPU 1 GB RAM and 5 GB of Disc space (see [services](/documentation/service/runtimes.html) for a detailed list). Zerops can automatically scale up to 64 CPUs, 2 TB RAM and 10 TB of disk space in a matter of seconds and then safely back down to minimum in minutes. Each metric is scaled separately, each container (when [HA](/ha/why-should-i-want-high-availability.html) is enabled) is scaled separately as well. Zerops scales by minimum steps (1 CPU, 1 GB RAM, 1 GB disk space), so there are no tiers or pricing packages. You always pay only for as much as your service currently requires. Vertical scaling is seamless, no downtime, no affecting your apps.

### Horizontal scaling

Once containers are fully scalled up vertically they start scaling horizontally by creating a new container with the last active deployed application version and start balancing requests between them. See [services](/documentation/service/runtimes.html) for a detailed list of minimum and maximum number of containers. When [HA](/documentation/ha/why-should-i-want-high-availability.html) is enabled, the minimum number of containers is 3.


### Performance tuning

Zerops is not just mindlessly scaling up and down, each service managed by Zerops is configured to scale up to its limits and tuned to perform as well as possible at the given configuration.
      
