---
author: SimpliLearn
rating:
genre: STEM
format: article
---
# AWS Tutorial for Beginners (2021)
`SOURCE:` [source](https://www.simplilearn.com/tutorials/aws-tutorial/what-is-aws)
#article #wip 
`AUTHOR:` Simplilearn

---
# What is AWS?
The author begins by discussing life before [[AWS]]. It took lots of energy and time to get servers online and optimized. There was lots of overhead for companies that wanted their own servers. 

Thanks to [[cloud computing]], this is no longer an issue, the author says. AWS provides a cloud infrastructure that gives us all the functionality and security of onsite servers, but adds a pay-as-you-go model. This eliminates overhead for those who don't need a ton of servers. 

AWS, the author says, is also very reliable and flexible. In 2016, Amazon made $10 billion on this service. 

The author describes services available through AWS. S3 is a great storage solution that is cloud based. Migration and data collection / transfer products exist in this system. EC2 is a flexible compute service that changes based on needs. Amazon Lambda is a compute service that bills us per second of compute time. Route 53 is a DNS cloud service. 

The article explains the benefits of AWS services. It creates a standardized environment and can speed up time-to-market for new services and tools. It allows secure backups and faster recovery after system failures. It also allows companies to analyze live data much faster without spending time and money maintaining the local data infrastructure. 

# AWS fundamentals
The article describes the reasons that somebody might want AWS, and the history of the service. It now offers more than 100 cloud services and is used by more than 45% of the global market. AWS is a secure [[cloud computing]] platform that provides storage, networking, compute power, and more. 

The author says that AWS provides security, experience, flexibility, ease-of-use, and scalability. Depending on the use case, there are lots of different services and levers to tweak. 

# What is AWS EC2 and why is it important?
The author begins by explaining the innovations in cloud. No hardware units are required locally, it's easy to scale resources, and you only pay for what you use. Users have complete control and security is great. You can now work on compute problems from anywhere in the world, on practically any machine. 

The author introduces EC2. AWS offers lots and lots of services under different domains. EC2 is web service that provides secure and scalable compute capacity in the cloud. We can scale our resources up or down very fast, and this is integrated easily with other services.

The author imagines a use case for EC2. If we have a business with many users, and we want to create an email list to advertise to those consumers, we can use AWS for this. If we use SNS for notifications, EC2 for compute, this will work. 

The article provides an overview of steps. We need an AWS account, then an EC2 instance. We need to create an Amazon Machine Image (AMI), choose an instance type (choose the hardware), configure that instance, then we can add storage to the instance. After that, we can add some tags, to easily identify the instance at a later time. This is useful when a business can run many instances at the same time. We should also configure the security firewall for the instance. At the end, we should review all the configurations and submit the instance. 

The first step, the author says, is choosing an AMI. This is just a template for the instance. We choose software, OS, additional applications, and software information. There are predefined and custom AMIs. You can compare AMIs on the AMI Marketplace. 

Then, the article continues, we have to choose the instance type. This could be compute optimized, where we have lots of processing power. This could be memory optimized, where high memory is a priority. This could be GPU enabled, which is good for gaming applications. Storage optimized, or general-purpose are other options. General purpose instances are pretty balanced and work well for middle-of-the-road applications. These instance types are fixed and cannot be altered after the instance is created. 

Thirdly, we continue, we can customize the instance. There are lots of billing options, and here's where we can change IP address settings, and many other things. We determine the shutdown behavior when the user ends the program from the desktop portal. Advanced details allow us to bootstrap the instance, aka install scripts that should run whenever the instance starts. Payment options include options to reserve compute resources upfront, which allows a discount. You can also bid for instances in order to try and save money. Normal rates are available, but these will be a little higher. 

The fourth step, the author says, is to add storage. We cah have ephemeral storage which is free and temporary, or we can pay for storage. We can hook this up to Amazon S3 to use their storage services. Free users get up to 30 GB of temporary storage. After that, we add tags. This helps to identify the machine where we may have 1000 virtual machines running for a larger firm. 

Finally, the article continues, we review security settings and review all of these things. When we submit the instance, the EC2 instance will launch. However, there's a final option. We can create a key-pair. The private key will be downloaded by the user, and the public key is used by Amazon to confirm the user's identity. 

The author covers the next step. We access the EC2 instance. We need the PuTTY and PuTTY generator tools. PuTTY generator allows us to accept .pem files, which is the form that our private key comes in. This step is needed when a Windows machine is trying to connect with a Linux system. 

The article returns to the hypothetical use case. We can use Amazon SNS to create a new notification list for our products. We can add subscribers to that list in order to notify them. We can create a S3 bucket where we can store that event. Whenever something goes in the S3 bucket, SNS will send a notification to the subscribers. We connect the bucket and the SNS with the EC2 instance. The EC2 instance keeps the two in sync. 

# Dissecting AWS' virtual private cloud (VPC)
...