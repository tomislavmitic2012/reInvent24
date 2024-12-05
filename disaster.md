### AWS for natural disaster warning

#### 12/04/2025

* Earthquake warning system by Earthscope consortium
* Use AWS technology to detect earth quakes

* Integrating Geophysics via Apps run on AWS
* GNSS (Global Navigation Satelite System)

* Geodesy
    * System to track earth's crust movement
    * Used in GPS
    * Used in ShakeAlert earthquake warning system

* Alert people about strong damaging earthquakes
* Distributed Goephysical Instruments distributed around the world
* Measure Seismic Activity, mograte it to data center and diseminate out to public

* Seismic instruments may be over saturated
    * Sometimes mis-judge magnitude of the earthquake
    * Can have deadly consequences

* Need for complimentary dataset to help gauge earthquakes force
* GNSS is used for this secondary dataset
* Signals are sent form satelites to Stations on Earth
* Through complex calculations give latitide/longitude and potential magnitude of earthquake
* Can give up to a .2 measurement accuracy of the magniutude of the earthquake

* Large datasets generated and need to be moved around
    * IOT data ingestion problems
    * Stream processing problems
    * Observability problems
    * Archive the data for Datascience

* IOT data ingest
    * GNSS data colelcted from thousands of locations worldwide
    * Most are at the edges of the world
    * Data streamed in realtime mostly
    * Except for Arctic and Antarctic
  
* Stream Porcessing
    * Realtime stream processing built out
    * Apache KAfka Managed steream processing
    * Elastic Container Service

* Benefits
    * Horizonal Scalability and Fault Tolerance
    * Extensibility and flexibility
    * Observability

* Kafka provides stable predictable paritioning 
* Partitions distributed across consumer groups
* All data from one station going to same compute

* Control planes vs Data planes
    * Control plane is administrative backbone of the system
    * Provides tooling to administer the system
    * Comprised of DBs and varius Compute Instances

* Data plane never interacts with the control plain

* Extensibility
    * allos seamless extension of the system and functionality by dpeloying more producers/consumers to Kafka topics
    * consistent foundation of tech stech
    * Easy to experiment with

* Measurements must be accurate so observability of data is important
    * Open source observability stack
    * Adot collector in side car configuration
    * Sends it to prometheus
    * Logs go from ECS to cloud watch

* Timeseries Analysis
    * Prometheus
        * Central repo of system health
        * Great for summaries
    * Amazon Timeseries for Live Analysis
        * Built for time series
        * Native integration with grafana
        * SQL like syntax
        * Old data falls off and is archived for posterior analysis

* Impact of system
    * Better more accurate estimations of magnitude of earth quakes
    * Tech foundation us used for all scientific instrument dataflows
    * Could not achieve this with on-prem services

* Looking Forward
    * ML earthquacke detection
    * High-Fi GNSS products
    * Data Science platform
    * Full archive analysis



