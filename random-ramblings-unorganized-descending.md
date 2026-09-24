# Influence Check
*A 60-second checklist before you nudge someone toward a decision or action.*

## Step 0: Name it
- My goal is: ______________________
- The way I'm going about it is: ______________________

*If you can't write it plainly, pause before sending.*

## Test 1: Disclosure — Could I say it out loud?
- [ ] I can state my goal and my method to them in plain words.
- [ ] If they saw my notes or a screenshot of my plan, they'd feel respected, not used.
- [ ] I'm not hiding a stake, a decision already made, or allies lined up behind the scenes.

**Red flags:** Planting ideas through others · "casual" suggestions that were engineered · sounding neutral while holding a stake

## Test 2: Decline — Can they say no?
- [ ] A real "no" is available, and I've said so.
- [ ] Saying no costs them no warmth, standing, or goodwill from me.
- [ ] Any deadline or urgency I mention is real.

**Red flags:** Guilt lines ("I'll just do it myself") · "everyone already agreed" · going cold after a no · invented urgency

## Test 3: Endorsement — Will they agree it was fair?
- [ ] My appeal speaks to their own goals and values, not a soft spot.
- [ ] I'm not leveraging insecurity, fear of missing out, or their need for my approval.
- [ ] Once they fully understand, I expect they'd say "fair enough."

**Red flags:** Identity challenges ("I thought you were someone who...") · praise used as a lever · withholding what would change their choice

## How to read it
- **All boxes ticked:** go ahead.
- **Any box unticked:** pause and rewrite.
- **Still unsure:** ask directly: *"Here's what I'm hoping for. How does that land?"*

## Instead of... try...
| Instead of... | Try... |
|---|---|
| "I guess I'll just do it all myself." | "I could really use help with X. Would you be up for it? No pressure." |
| "Everyone's already on board." | "Three people support it and two have concerns. I'd like your honest view." |
| "I thought you were the type to step up." | "You mentioned wanting more leadership experience. This could be a step toward it." |
| Quietly lining up allies before a vote. | "I lean toward B and have talked with a few people. Please challenge it." |

## Fine as is
Humor, emotion, stories, truthful positive framing, tactful timing, and ordinary discretion (like a surprise party) are all fine.

## If you slip
"I nudged you earlier without being upfront. What I actually want is ___. You're free to say no."

---
*Influence survives being explained. Manipulation does not.*




9/22/26
- should probably just show this to people who are cold or incompetent to convince them to work on whichever they are lacking.

### S. Fiske's Stereotype Content Model (4 Quadrants adjusted to the workplace)


| Perceived Quadrant | Workplace Profile | Triggered Emotion | Behavioral Response | Common Workplace Examples |
| :--- | :--- | :--- | :--- | :--- |
| **High Warmth / High Competence** | High-performing allies who share resources and lift the team up. | **Pride & Admiration** | **Active Facilitation:** <br><br> People actively support them, champion their ideas, and want to work on their projects.<br> | Star team players, highly competent mentors, or transparent, supportive leaders. |
| **High Warmth / Low Competence** | Extremely friendly and well-liked, but routinely struggles to hit KPIs. | **Pity & Sympathy** | **Passive Facilitation (with Paternalism):** <br><br>People tolerate them and step in to do their work for them, but micro-manage or pass them over for promotion.<br> | The eager-to-please intern, a legacy employee whose skills have lapsed, or the "office cheerleader." |
| **Low Warmth / High Competence** | Brilliant executors who get things done but are hyper-competitive or toxic. | **Envy & Resentment** | **Passive Cooperation / Active Harm:** <br><br>People cooperate with them out of necessity, but will secretly rejoice or sabotage them if they slip up.<br> | The toxic top salesman, the hyper-political executive, or an aggressive "cutthroat" department. |
| **Low Warmth / Low Competence** | Unreliable performers who also isolate themselves or complain constantly. | **Contempt & Disgust** | **Active Harm / Exclusion:** <br><br>The team actively excludes them from key conversations, ignores their emails, or pushes for them to be managed out.<br> | "Quiet quitters" who are openly cynical, or chronic underperformers who miss deadlines and blame others. |


- If you want to succeed in the professional world, you'd want to have high levels of both competence and warmth.
- It doesn't matter if it's fake at first, try to practice politeness/proper ethics, while at the same time, improving your skills regularly.

1/28/26
- reminder DynamoDB Global Tables don't need manual replication setup, and it also automatically enables DynamoDB Streams feature.

1/11/26
- AWS DevOps reviewing weak topics (CodeDeploy appspec.yml lifecycle hooks, fixed environment variables available since CodeDeploy has no custom env variables, CodeDeploy + NGINX log level scenario)
- using AWS Step Functions is inappropriate when collecting the logs from your EC2 instances (attached to an ASG). you should use a CloudWatch agent instead.
- review lifecycle of EC2 instances attached to ASG (scale in: Pending->Pending:Wait->Pending:Proceed and scale out: Terminating->Terminating:Wait->Terminating:Proceed)
- unified CloudWatch Agent and metrics it can collect (system-level metrics, custom metrics)
- utilizing EventBridge and Systems Manager Automation document to listen for termination lifecycle event, pause it and then collect logs before the instance gets put away by the ASG

9/27/25
- IAM Roles for Service Accounts (IRSA) in Kubernetes on AWS, particularly with Amazon EKS, is a mechanism that allows you to grant AWS Identity and Access Management (IAM) permissions directly to Kubernetes Service Accounts. This enables your Kubernetes pods to securely access AWS resources without needing to store or manage AWS credentials within the pod or on the underlying EC2 instances.

9/24/25

-just doing AWS IAM stuff, like:
- AssumeRole for borrowing role permissions
- creating a custom policy that gives a principal read-only permissions for IAM (all IAM resources and the IAM credential report)
- randomly came across this image that reminds of IAM best practices: https://cybr.com/cloud-security/aws-iam-credentials-report-cheat-sheet/. it does point out some old practices that are kinda not best practice anymore.
- IAM attribute-based access control
- more AWS organizations stuff

9/22/25
- S3 website hosting 403 Forbidden Error, often is missing permissions or block public access options is active
- dont forget to add an Allow Read bucket policy when doing S3 website hosting. 
- said bucket policy should look like this:

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::Bucket-Name/*"
            ]
        }
    ]
}
```

- it also should disable block public access options completely for it to be accessible on the browser.


9/18/25
- if SG and NACL is allowing traffic and port type for that IP, the instance is also in a public subnet, then might wanna check if you have an Internet Gateway or not...
- no IGW = you cannot reach 

9/10/25
- TIL Apache Hive 
- it seems like Hive is built on top of Hadoop
- a distributed, fault-tolerant data warehouse system that enables analytics at a massive scale. A data warehouse provides a central store of information that can easily be analyzed to make informed, data driven decisions. 

8/25/25:
- "The instance must be in the stopped state to modify its placement properties. You cannot change the tenancy of an instance from default to dedicated or host after you've launched it."
- so yeah if a running instance doesnt let you modify its placement (`Modify instance placement` grayed out), then stop the instance first
- source: https://stackoverflow.com/questions/58495959/modify-instance-placement-grayed-out-instance-is-stopped
- LIST OF SHAREABLE AWS RESOURCES VIA RAM: https://docs.aws.amazon.com/ram/latest/userguide/shareable.html

8/18/25
- DynamoDB Local secondary indexes (LSI) are created at the same time that you create a table. You cannot add a local secondary index to an existing table, nor can you delete any local secondary indexes that currently exist.

8/17/25
- DynamoDB Global secondary indexes (GSI) does not support strong read consistency 
(ill try my best not to forget lmao)

7/21/25
- computer optimizer poggin

7/07/25
- The Amazon EC2 service provides virtual machines that emulate computer hardware, such as CPU, RAM and disk.
- The AWS service cannot see "inside" your instance because it is running an Operating System (Linux or Windows). It is the operating system that controls how memory is allocated, so it is not possible to determine "Memory Utilization" purely by looking at the virtual hardware.
- That's why the metrics provided are CPU Utilization, Network and Disk — they all involve the virtual hardware.

7/06/25
- finally reading on ECMP after putting off that shit for so long lmao
  
7/02/25
- EventBridge can listen to Trusted advisor checks' status changes, then you can trigger an event/target action based on rules defined by the dev.

7/01/25
- A black hole simply is a route that goes nowhere. (e.g. a route towards a since-then deleted network interface/instance)
- Blackhole routing can be an alternate means to mitigate DDoS attacks and block other malicious traffic. By discarding traffic intended for certain IP addresses, blackholing may improve network performance and reduce congestion.
- When dynamic routing is used with a VPN attachment or a Direct Connect gateway attachment, you can propagate the routes learned from the on-premises router through BGP to any of the transit gateway route tables.
- When dynamic routing is used with a VPN attachment, the routes in the route table associated with the VPN attachment are advertised to the customer gateway through BGP.
- You can peer two transit gateways, and route traffic between them.
- AWS Transit Gateway only shows a preferred route. example: Direct Connect gateway is preferred over Site-to-Site VPN (only serves as a backup route that will only display when DC gateway is no longer advertised). 
- Route table evaluation differs between whether you're using a VPC route table or a transit gateway route table.
- In a VPC route table, the VPC local route has the highest priority, followed by the routes that are the most specific. When a static route and a propagated route have the same destination, the static route has a higher priority.
- A network function attachment is a resource that connects a network security function (e.g. an AWS Network Firewall attachment) directly to your transit gateway. 
- AWS Network Firewall integration allows you to connect a firewall in the form of a group of Gateway Load Balancer Endpoints, one per Availability Zone, in a service-managed buffer VPC (created with appliance mode auto enabled). 

6/30/25
- having a route to the transit gateway isn't enough, you also need to ensure that a transit gateway attachment exists in the same AZ as the subnet sending the traffic, or the traffic will not be forwarded (it just gets dropped).

6/29/25
- it is weird that an AWS Control Tower account fails its prerequisites for some reason, and then making a single EC2 instance fixes this issue. I mean, it happened to me and I saw a vid on it
- really weird phenomena
- made me read further on Prerequisite: Automated pre-launch checks for your management account

6/25/25
- imagine not just using chocolatey to upgrade terraform version
- imagine going to the website to bother downloading the binary files
- lmao 


5/12/25
- 
- oh cloudwatch subscription filter doesnt directly accept a kinesis firehose delivery stream as a destination, only a kinesis stream ok
