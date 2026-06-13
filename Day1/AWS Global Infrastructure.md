What is AWS Global Infrastructure?
- The physical, geographic hardware footprint that powers the AWS cloud platform.
- It is a global grid of data centers connected by a private, high-speed fiber-optic network.
- It is organized into a clear hierarchy: Regions ➔ Availability Zones ➔ Local Zones & Edge Locations.

Why is it needed?
- Disaster Recovery: Protects applications from being wiped out by a single physical incident (like power failure, fire, or floods).
- Compliance: Helps businesses meet strict local data residency laws (like India's DPDPA or Europe's GDPR) by keeping data inside country borders.
- Performance: Reduces network latency by placing application resources physically closer to end users.

Problems it solves?
- High Latency: Avoids routing traffic across oceans, which slows down the user experience.
- Single Points of Failure: Prevents massive downtime by distributing workloads across independent infrastructure footprints.
- Data Sovereignty Violations: Eliminates the risk of legal penalties by ensuring customer data stays exactly where regulations mandate.


Real-World Architecture Components
1. Regions: * A distinct, separate geographic area (e.g., ap-south-1 in Mumbai).
  -  Each region is completely isolated from the others to guarantee maximum fault tolerance.
2. Availability Zones (AZs): * Distinct data center clusters inside a specific Region.
  -  Each AZ has engineered isolation with its own independent power, cooling, and network grids.
  -  They are connected to each other via ultra-fast, low-latency fiber paths ( <2ms ).
3. Edge Locations: * Small, global points of presence used by Amazon CloudFront (CDN).
  -  They do not run heavy virtual machines; they only cache static assets (like frontends and images) close to the user's browser.
4. Local Zones: * Extensions of a region placed inside highly populated cities (like Bengaluru).
  -  They provide single-digit millisecond latency for intense local compute needs without needing a full-scale regional footprint.
