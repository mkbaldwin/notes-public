# Resilient Architectures

* Resiliency is the ability of an application to avoid and recover from failures. 
* Resilience is quantified in terms of availability.
* Availability is a metric as the percentage of time the application is performing as expected.

## Availability

Availability if often referred to by the number of nines. 

| Number of Nines | Availability | Annual Downtime              |
|-----------------|--------------|------------------------------|
| 2               | 99%          | 3 days, 15 hours, 39 minutes |
| 3               | 99.9%        | 8 hours, 45 minutes          |
| -               | 99.95%       | 4 hours, 22 minutes          |
| 4               | 99.99%       | 52 minutes                   |
| 5               | 99.999%      | 5 minutes                    |

## Traditional Applications

Applications that are written to utilize traditional Linux or Windows servers. To run these applications on AWS you will
use one or more EC2 instances. Databases can either be run on an EC2 instance you manage or using a managed service
such as Amazon Relational Database Service (RDS).

* Dependencies on AWS services such as RDS or EC2 are hard dependencies.
* To calculate the availability multiply the availability of each service.

```
 .9 (single EC2) x .9995 (RDS multi-AZ) = 0.89955 (89.995%)
```

* To increase availability you can add multiple EC2 instances and load balance traffic.
* To calculate the availability of three EC2 instances in a cluster take 100% minus the product of the instance failure rate.

```
1 - (.1 x .1 x .1) = .999
```

Page 250

## Cloud-Native Applications

Cloud-Native applications are written to use the resources of a specific cloud platform. 

