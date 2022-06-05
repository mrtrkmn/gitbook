Cloud Computing - 2022

[I WEEK]

---

## IT Trends 

- Outsourcing 
	- Companies do not run their IT infrastructures on dedicated servers, instead they ask for other companies to handle it
	
- Recentralization
	- Remote Desktops, instead of giving resources to everyone, just provide a remote connection for them

- Edge Computing
	- IoT, due to distributed computing we are placing edge servers to act immediately when there is something very urgent. Instead of traversing over cloud we are accessing directly to edge server to take action  

- Resource sharing instead of overprovisioning
	- Trying to reduce costs that company may have

- Server Consolidation 
	- Virtualizing servers to use resources much efficient

- Green Computing 
	- data centers consumes a lot of energy, G.C tries to reduce energy and trying to use energy from renewable energy sources

- Scalable Computing
	- we do not use single computer, a lot of servers are working coordinated

- Application dynamism
	- Applications are used all over the world and they may have different load in different time intervals, in order to handle those kind of situations, there should be application dynamism

- Big Data
- Machine Learning
- Stream Processing
- IoT
- Mobile computing
- Autonomous Computing
	- Automatic recovery > Running Cloud Centers

## Cloud Computing

 - Access to IT services over the Internet. 

### CC : IT as a Service 

 - **ITaaS**

 	- Expand traditional e-commerce in the internet to IT structures
 	- Rent from a virtual store front the basic necessities to build a virtual data center
 		- Resources: CPU, memory, storage, networking
 		- Services: application servers, databases, authentication, messaging
 		- Applications: ISVs or self-developed

 	- Pay per use: no capital investment necessary
 	- Scalability: dynamically adapt the resources to your needs
 	- Profit from economy of scale
 	- Enable environmental sustainability 
 		- Backing data centers can be optimized for efficient utilization
 		- ... can be built at appropriate places (green energy, free cooling)

## Cloud Service Models

| **Own IT**            | **IaaS Cloud**                | **PaaS Cloud**                          | **SaaS Cloud**                             |   |
|-----------------------|-------------------------------|-----------------------------------------|--------------------------------------------|---|
| **Your Servers**      | _Amazon WS OpenStack Alibaba_ | _Microsoft Azure Google App Engine AWS_ | _Salesforce.com Google Apps Microsoft 365_ |   |
| **Data**              | **Data**                      | **Data**                                | **Data**                                   |   |
| **Application Logic** | **Application LOgic**         | **Application Logic**                   | _Application Logic_                        |   |
| **Devel./Runtime**    | **Devel./Runtime**            | _Devel./Runtime_                        | _Devel./Runtime_                           |   |
| **Infrastructure**    | _Infrastructure_              | _Infrastructure_                        | _Infrastructure_                           |   |


### Infrastructure as a Service (IaaS)

- Offers

  - Servers, storage, network

- Technologies

  - Commodity hardware
  - Virtualization of servers, storage and networks
  - Server template technology binding hardware OS
  - Automated management of the infrastructure enabling self-service of customers
    - dynamic provisioning of physical resources
    - management of virtual resources
    - optimization of utilization, power efficiency
    - high reliability and guaranteeing SLAs
    

### Platform as a Service (PaaS)

- Offers
  - Application infrastructure services
    - Managed services: databases, execution environments, integrated development platforms
  - Serverless computing
  
- Technologies
  - Service Oriented Architecture
  - Backend Services that can be used in your application
  - Scalable application middleware, e.g databases, file systems
  - Special programming models and interfaces
  - Automatic scaling, version management

- Example:
  - MS Azur: Microservice Fabric
  - Amazon: FaaS > Lambda functions
  - Google Application Engine
  
  
  
 ### Software as a Service (SaaS)
 
 - Offers
 
  - Consumer or industrial applications to individual or enterprise users.
 
 - Technologies
 
  - Standard applications as well as cloud native applications
  - Autoscaling 
  - Multi-tenancy
  - Broad spectrum of user interfaces
  
 - Example
 
  - Salesforce
  - Google
  - Dropbox
  
  ## Deployment Models
  
  - Public Cloud
    - IT resources are provisioned over the Internet via Web applications or services from an off-site third-party provider
  
  - Community Cloud
    - Shared by a group of organizations
  
  - Private Cloud
    - IT services are offered via private networks for the exclusive use of one client, providing full control over data,security and quality of service
      e.g built and managed by a company's own IT organization
      
  - Hybrid Cloud
   
  
  
  
  
## Essential Characteristics of Cloud Computing 

- On-demand self-service
  - A consumer can unilaterally provision computing capabilites, such as server time and network storage, as needed automatically without requiring human interaction with each service provider

- Broad network access
  - Capabilites are available over the network and accessed through standard mechanisms that promote use by heterogeneous thin or thick client platforms 
    e.g mobile phones, tablets, laptops and workstations

- Resouce pooling
  - The provider's computing resources are pooled to serve multiple consumers using a multi-tenant model, with different physical and virtual resources dynamically assigned and reassigned according to consumer demand.
    There is a sense of location independence in that the customer generally has no control or knowledge over the exact location of the provided resources but may be abale to specify location at a higher level of abstraction. 
    (e.g country, state or datacenter) Examples of resources include storage processing, memory and network bandwidth.

- Rapid elasticity
  - Capabilities can be elastically provisioned and released in some cases automatically, to scale rapidly outward and inward commensurate with demand.
  To the consumer the capabilites available for provisioning often appear to be unlimited and can be appropriated in any quantity at any time.
  
- Measured service
  - Cloud systems automatically control and optimize resource use by leveraging a metering capability at some level of abstraction appropriate to the type of service.
  ( e.g storage, processing, bandwidth and active user accounts) Resource usage can be monitored, controlled, and reported, providing transparency for both the provider and consumer of the utilized service
  



### Cloud Technologies
---

![Cloud Technologies](../.gitbook/assets/cloud-techs.jpg)

---


### From monitoring perspective
---

![Cloud Technologies-Monitoring](../.gitbook/assets/cloud-tech-2.jpg)




## AWS 

-  Amazon EC2 provides

    - Virtual machines running inside the Amazon Cloud
    - Ephemeral storage tied to the virtual machine
    - Block storage that persists over time and can be mounted in the VM
    - Virtual firewall to secure your network in Cloud
    - Based on Xen hypervisor, offering also Nitro Hypervisor based on KVM


## Technology sources of the Cloud 

 - Cloud Computing has tech sources:
    - Service Oriented Architectures
    - Virtualization
    - Server Consolidation
    - Grid Computing
    - Cluster Computing


## Cloud Computing Pros/Cons


| **Pros**                             | **Cons**                   |
|--------------------------------------|----------------------------|
| Economy of scale                     | Security                   |
| Scalability                          | Controllability            |
| Elasticity                           | Vendor lockin              |
| Rapid development                    | cost, monthly fees         |
| No capital investment                | Limited trust in providers |
| No caring about infrastructure       | Breaking SLAs              |
| Limited access to on-premise servers |                            |
| Fault tolerance                      |                            |
| Collaboration                        |                            |



## Summary 

- Cloud computing enables IT as a Service
- No capital investment but pay per use
- Service models: IaaS, PaaS, SaaS
- Deployment models; public,private, hybrid

- Major benefits:

    - Economy of scale
    - Enables sharing of resources
    - Division of work
    - Elasticity

- Major drawbacks:

    - Relies on trust into providers
    - Interoperability is missing
    


# WEEK II - Cloud Computing



Semiconductor process

Processor architecture

Accelerators

Data Centers 



## Processor Architecture

### CPU

- Driving forces
  - Increase in transistors due to process technology 
  - Increase in clock speed stopped
  - Need for performance increase
  - Need for energy reduction

- Trends
  - Multi-core processors
  - SIMD support
  - Combination of core private and shared caches
  - Heterogeneity
  - Hardware support for energy control
  - 64 bit architectures


### Skylake XP Socket

- Mesh
  - 2D Mesh network
  - Dimension-order routing
  - Mesh clock rate
  - 32 bytes per cycle
  - Sub-NUMA cluster mode
  - up to 205W



## Processors for mobile devices 

- ARM 
  - British company, 2016 acquired by SoftBank (Japan)
  - Developing processor design 
  - Integrated into SoCs for mobile devices

- Apple
  - iPhone 12 and iPad Air 2020
  - 64 bit CPU, 6 Cores, 2 high performance Firestorm, 4 energy-efficient icestorm 
  - 4 core GPU
  - 16 core neural engine
  - Matrix multiplication machine learning accelerators
  - Image and signal processor
  - TSMC 5nm processor
  - 11.8 billion transistors
  - Package on package implementation with 4GB LPDDR4X memory

- Apple M1 - Core Architecture
  - 16 billion transistors
  - 8-core CPU
  - 8-core GPU
  - 16-core Neural Engine

  - For CPU
    - Four high-performance cores  - Firestorm
    - Four high-efficiency cores - Icestorm
      - To handle lighter workloads
    
    - big.LITTLE Processing is current trend
    - Intel latest Alder Lake - Hybrid Core


- Apple M1 Pro

  - 33.7 billion transistors
  - 8 high performance and 2 high efficiency cores
  - 16 core GPU (128 ALUs each)
  - 32 GByte Unified Memory 
  - 200 GB/s bandwidth

- Apple M1 Max
  - 57 billion transistors
  - Same CPU as M1 Pro
  - 32 core GPU x 128 ; 10.4 TFlops
  - 64 GB Unified Memory
  - 400 GB/s bandwidth
  - 86 W CPU+GPU


## General Purpose Graphics Processors (GPGPU)

### Accelerator Programming 

- Motivation for accelerators
  - Increase computational speed
  - Reduce energy consumption
  - Achieved by specialization
    - Specialize in the operations
    - Specialize in on-chip communication
    - Specialize in memory accesses

- Three types of accelators
  - GPGPUs
  - Many standard cores
  - FPGA

- System integration

  - NOdes with attached accelerators
  - Accelerator only designs 
  - Accelerator booster 


### GPUs 

- Graphics Processing Unit (GPU)

  - Used for visualization via interfgaces like OpenGL, DirectXC
  - NVIDIA developed the idea of GPGPU - General Purpose Graphics Processing Unit. That is to use the GPU for general processing
  - It combines every type of parallelism; Multithreading, MIMD, SIMD and even instruction-level

  - Challenges
    - programming a GPGPU
    - coordinating the scheduling of computation on the system processor and the GPU
    - managing the transfer of data between system memory and GPU memory
  
  - NVIDIA developed the CUDA language for processing on a GPGPU


### Streaming Multiprocessor

- 64 FP32 CUDA cores
- 32 FP64 CUDA cores
- 64 K registers
- L1 shared cache
- 64 KB shared memory

- Hierarchical structure of a GP100
  - 60 SMs 
  - 30 Texture Processing Clusters (TPC)
  - 6 Graphics Processing Clusters (GPC)

- HBM 
  - Vertical stacks of memory dies connected by microscopic wires through-silicon vias
  - 8Gbit die with 5000 through-silicon holes
  - 180GB/sec per stack bandwidth
  
### FPGAs as accelerators

- Field Programmable Gate Array
  - Array of logic gates to implement hardware programmed special functions
  - Specialized functional units (e.g signal processors, multipliers), possibly replicated
  - Static memory also called block memory
  - Clock rate 100-550 Mhz 
  - Programmed in VHDL

- Two big players are Altera and Xilinx
  - Dec 2015 Intel purchased Altera
  - Cost for FPGAs are decreasing while ASIC costs increase
  - Synthesized CPU cores are comparatively poor
  - Altera and Xilinx offer FPGAs with hard CPU; variety of these hybrid devices is quite narrow.

- Intel and Altera
  - Intel started delivery of Stratix 10 chip with its new hyperflex architecture for cloud computing and data centers
  - Consists of Adaptive Logic Modules (ALMs) full duplex transceivers, memory blocks, variable precision DSP blocks, PCI express and DRAM interface
  - Embedded quad-core 64 bit ARM**Cortex**- A53  hard processor system (in SoC variants)

- Other FPGA series from Intel/Altera
  - Arria, Cyclone and MAX with lower performance/less price

- Intel-Altera Heterogeneous Architecture Research Platfrom Program
  - Pair a 12-core Intel microprocesor with an Altera Stratix V FPGA module
  





### Comparison of Technologies 

![](../.gitbook/assets/comparison_of_tech.jpg)\



### Nallatch accelerator card

- Up to 10 TFlop single precision FP for machine learning, Gene sequencing, Oil&Gas, Real time network analysis


## Shared Memory Systems - NUMA 

- Characteristics
  - Multiple CPUs with multiple cores
  - Single physical address space
  - Non-uniform memory access

### NUMA Node of SuperMUC 

![](../.gitbook/assets/numa_node.png)


- 2 processors with 32 GB of memory 
- Aggregate memory bandwidth per node 102.4 GB/s
- Latency
  - local ~50ns
  - remote ~90ns


### Programming 

- Broad spectrum of programming interfaces 
  - Explicit threading, e.g with pthreads, Java threads
  - Automatic parallelization
  - OpenMP
    - Directive-based parallel programming
    - Supporting data and task parallelism
  - Explicit synchronization
  - Concurrecny bugs: data races

- Control of data locality
  - Combination of language features and OS
    - Data allocation
    - Thread pinning


### Distributed Memory Systems or Clusters

- Characteristics
  - Coupling of individual nodes via network
  - No shared physical address space
  - Explicit transfer of messages between nodes

- Programming
  - Message Passing Interface (MPI)
  - Provides P2P communication as well as collective operations 
  - Rarely race conditions only in specific situations

- Communication is expensive 
  - Performance model t(m)=startup time + m / bandwidth
  - Mapping of processes onto processors has a performance impact



### Comparing Efficiency of Computing Centers

- PUE 
  - Power usage effectiveness (PUE) is a measuire of how efficiently a computer data center uses its power;
  - PUE is the ratio of total power used by a computer facility to the power delivered to computing equipment.
  - Ideal value is 1.0
  - It does not take into account how IT power can be optimised
  - PUE = Total Facility Power / IT Equipment Power

- ERE 
  - Energy Reuse EFfectiveness measures how efficient a data center reuses the power dissipated by the computer
  - ERE is the ratio of total amount of power used by a computer facility to the power delivered to computing equipment.
  - An ideal ERE is 0.0. If no reuse, ERE = PUE
  - ERE = Total Facility Power - T_(resue) / IT Equipment Power


### Switch to Green Energy

- Energy efficiency 
  - PUE 
  - energy-aware job scheduling
  - DVFS 

- Carbon-awareness
  - Scheduling work in space and time to reduce usage of brown energy

## Summary 

  - Process Technology 
  - Processor architecture
  - GPGPU
  - FPGA
  - Data centers 
