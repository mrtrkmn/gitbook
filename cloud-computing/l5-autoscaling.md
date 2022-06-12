# L5- Application Elasticity

Native Cloud Applications are scalable; capacity can grow to very large workflows. 

![](../.gitbook/assets/elasticity.png)

## Resource Requirements of Applications 

- **Resources**
    - CPU Time 
    - Memory 
    - Disk 
    - Network 

- **Resouce requirements**
    - Constant
    - Dynamic 

- **Application examples**
    - Desktop
    - HPC
    - Banking Software 
    - Web applications  

## Dynamic Resource Requirements 

![](../.gitbook/assets/dynamic-resource-req.png)


## Scalability

- More resources
    - More performance (Individual requests handled faster & Decreased latency)
    - Ability to handle more workload in the same time. (Increased throughput)

**Scalability Limit** 

![](../.gitbook/assets/scalability-limt.png)

- Limit is the upper bound.
- Sequencual parts dominates paralel part of the program. 
- When there is no parallel execution, still there might be some shared resource. 

- **Scalability of applications**
    - Characteristic of an application to increase its capacity (throughput) with the amount of resources

- **Capacity of an application depends on**
    - Available resource capacities
    - Application design 

- **Scalability Limits**
    - Maximum application capacity 
    - Throughput can be limited by maximum resource capacities and/or by the application design. 

- **Application with poor or low scalability**

    - Low scalability limit 
    - Significant drop in efficiency

## Application scaling 

- **Adding more resources leads to more performance**
    - Performance can be time, work/time, throughput

    ![](../.gitbook/assets/application_scaling.png)

## Efficiency

![](../.gitbook/assets/efficiency.png)

**Elasticity of applications**

- **Elasticity**
    - Dynamic adaptation of the capacity to a change in the workload 
    - No shutdown/restart required
    - Shrink capacity, if workload decreases
    - Increase capacity, if workload increases 


**Capacity planning in traditional IT**

- Goal: Plan the reosurces to avoid under-provisioning
- Accepting high costs due to over-provisioning
- No elasticity, planning period years 

![](../.gitbook/assets/traditional_it_planning.png)

**Capacity planning in the Cloud**

- Goals: 
    - Avoid under- and over-provisioning to increase business success and reduce costs 
- **Possible due to dynamic resource management and pay-per-use cost model**
- High elasticity

![](../.gitbook/assets/capacity-planning-in-cloud.png)

## Application Architecture 

![](../.gitbook/assets/application-arc.png)

## Vertical Scaling - Scaling up 

- Increase capacity of a single service instance by increasing its resources 
    - Increase CPU time percentage 
    - Increase clock frequency
    - More cores 

- Advantage 
    - No change in the service required. 

![](../.gitbook/assets/vertical-scaling.png)


- **Replace existing resources with more powerful resources**

![](../.gitbook/assets/vertical-scaling-2.png)


- **Advantages**

    - It is easy to replace a resource with a more powerfuil resource 
    - It does not require a re-design of the application 

- **Disadvantages**
    - More powerful resource might be too expensive 
    - Resource capacity is limited 
    - Replacement of resource causes service interruption



## Horizontal Scaling - Scaling out 

- Capacity increase of service by creating more instances 
    - Assumption: Each service instance comes with own resources

![](../.gitbook/assets/horizontal-scalin.png)


- **Increase the amount of resources**

![](../.gitbook/assets/horizontal-scaling.png)

- **Advantages**
    - Scaling through adding more resources 
    - No requirement for more powerful hardware 

- **Disadvantages**
    - Increased amount of resources comes with more management overhead 
    - Horizontal scaling requires a distributed software architecture 


## Comparison horizontal and vertical scaling 

![](../.gitbook/assets/horizontal-vs-vertical.png)

## Autoscaling 

- **Autoscaling**
    - Automatically scale an application to meet the service level objectives under a varying workload while minimizing service costs. 

- **Service Level Objective (SLO)**
    - Latency of requests < latency threshold 
    - Failed request rate < failed request threshold 
    - Service availability > availability threshold 

- **Service Level Agreement (SLA)**
    - Contract specifying SLOs
    - Fines 

- **Costs**
    - #VMs, storage, network traffic, I/O traffic

## Autoscaling System 

![](../.gitbook/assets/autoscaling-system.png)

## Autoscaling Policy 

![](../.gitbook/assets/autoscaling-policy.png)

## Autoscaling Approaches 

- **Reactive**
    - Detect under-/overloaded service 
    - Scale in/out or down/up according to policy 

- **Scheduled**
    - Policy specifies scaling events (time stamped scaling actions)
    - Apply scaling actions at appropriate time 

- **Predictive**
    - Continuously predict future workload 
    - If workload will charge, schedule scaling actions ahead in time. 
    - Goals 
        - Circumvent scaling latency
        - Enable more time consuming scaling decisions 

## Resource and Service Centric Auto-Scalers 

- **Resource centric**
    - Scaling actions modify resources 
    - Services are implicitly adapted 

- **Service centric**
    - Scaling actions modify #service instances 
    - Resources are implicitly adapted


## AWS Reactive Autoscaling 

- **Resource centric**
    - Scaling of #VMs 
- **Launch template**
    - ID of the Amazon Machine Image( AMI )
    - Instance type 
    - Key pair, security groups, and other parameters used to launch EC2 instances 
- **AWS Auto Scaling Group** 
    - Set of VMs with same launch template 
    - Determines a target #VMs. Restart in case of failures 
        - Instances can be on-demand and spot instances 
    - Defines min, max, desired #VMs 
        - Scheduled actions to redefine those 
    - Set of scaling policies 
    - Optionally a load balancer 


## AWS Scaling Policies 

- **Target tracking scaling**
    - Utilization metric that drops with more resources 
    - Specification of target value 
    - Automatically adjust resources to meet target 

- **Simple Scaling**
    - Trigger based on: metric, threshold, condition
    - E.g metric >= threshold 
        - +/- #VMs 
        - Change to #VMs 
        - +/- percent of #VMs 


- **Step Scaling**
    - Depends on amount of breach 
    - Specify metric, threshold, steps based on amount 
        - +0% ... +10%: 0%
        - +10% ... +20%: 10%
        - +20% ... +infinity: 30%
        - 0% ... -infinity: 10 %

- **Policies have a cooldown period specification**
    - Only after this time, breaches are handled again. 

    
