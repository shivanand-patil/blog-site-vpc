# Create a VPC from scratch, set up your own NAT and much more using AWS
**What the heck is a VPC?**
---------------------------

Amazon Virtual Private Cloud (VPC) is a service that allows you to launch AWS resources in a logically isolated virtual network that you've defined. This virtual network closely resembles a traditional network that you'd operate in your own data center, with the benefits of using the scalable infrastructure of AWS.

With a VPC, you can have complete control over your virtual networking environment, including:

*   The IP address range of your VPC
    
*   The subnets within your VPC
    
*   The security groups that control inbound and outbound traffic to your VPC resources
    
*   The route tables control how traffic is routed within your VPC and to the internet
    

**NOTE: Assuming that you have an AWS account, let's get started with VPC!**

* * *

Getting started with a Virtual Private Cloud (VPC)
--------------------------------------------------

1.  Go to the AWS website to log in to your AWS account, and Click on the **Console** button in the top right corner of the page.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695384645692/308c48ca-e1e2-4600-8ef0-e56a4335ed29.png?auto=compress,format&format=webp)
    
2.  Click on the **Services** tab in the top left corner of the page and make sure the selected region is "Oregon" (us-west-2) as we will be performing all the operations in the same region.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695384759520/19b4cd3b-e17e-46a1-9840-83ef172988d8.png?auto=compress,format&format=webp)
    
3.  In the search bar, type "VPC" and then select the **VPC** service from the drop-down menu.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695384808619/cb78759e-dce4-49c8-a59a-bb31a66d2aab.png?auto=compress,format&format=webp)
    
4.  Click on the "Create VPC" button
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695384934237/f1d424e3-0e2d-4805-9413-af438790a34e.png?auto=compress,format&format=webp)
    

* * *

Create a VPC
------------

Once you are on the VPC service page, click on the Create VPC button.

1.  **Select VPC only under resources to create.**
    
    This will create a VPC with the default resources, such as a default route table and a default security group.
    
2.  **Give your own VPC name under the name tag.**
    
    This is a name that you will use to identify your VPC. It is a good idea to give your VPC a descriptive name so that you can easily find it later.
    
3.  **Select IPv4 CIDR manual input under the IPv4 CIDR block option.**
    
    This will allow you to specify your own IPv4 CIDR block for your VPC.
    
4.  **Give 10.0.0.0/16 in the input field.**
    
    This is the CIDR block that you will use for your VPC. It is a /16 CIDR block, which means that it contains 65,536 IP addresses.
    
5.  **Click on the Create VPC button.**
    
    This will create your VPC.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695385820076/35b2fcbc-c4d1-4647-bb14-f50891a329bd.png?auto=compress,format&format=webp)
    

* * *

Create Subnets
--------------

Before moving further we need to understand what is a subnet.

**What is a subnet?**

A subnet is a logical division of a VPC. It is a range of IP addresses that are carved out of the VPC's CIDR block. Subnets allow you to isolate resources within your VPC and control how they communicate with each other.

**Creating a subnet**

To create a subnet, follow these steps:

1.  Click on the **Subnets** tab on the left panel of the VPC dashboard.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695386437214/85144cc9-9323-4981-87bc-dd7111dea2a3.png?auto=compress,format&format=webp)
    
2.  Click on the **Create Subnet** button.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695386507696/e02f45e5-20aa-4e88-ad0d-967852897a67.png?auto=compress,format&format=webp)
    
3.  Select the VPC that you created in the previous step.
    
4.  Under **Subnet settings**, give your subnet a name, such as "Border subnet".
    
5.  Under the **Availability zone**, select the availability zone where you want to create the subnet.
    
6.  Under **IPv4 CIDR block**, give the subnet a CIDR block. The CIDR block must be a subset of the VPC's CIDR block. In this example, we will use the CIDR block 10.0.0.0/24.
    
    In this example, we are creating a subnet with the CIDR block 10.0.0.0/24. This means that the subnet will have 256 IP addresses, from 10.0.0.0 to 10.0.0.255.
    
7.  Click on the **Create Subnet** button.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695386633482/228a5b42-284e-4cb3-8a1b-a28c248cc674.png?auto=compress,format&format=webp)
    

This will create a subnet in the selected availability zone with the specified CIDR block.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695386797364/6be15476-bd32-4021-b359-f52f37b2c113.png?auto=compress,format&format=webp)

* * *

**Create a Route Table for the Border Subnet and editing subnet associations**
------------------------------------------------------------------------------

but but but what is a routing/route table??

**What is a routing/route table?**

A routing table is a set of rules that determine how traffic is routed within a VPC. It contains a list of destinations (IP addresses or CIDR blocks) and the next-hop devices that should be used to reach those destinations.

**Why do we need a route table?**

A route table is necessary to route traffic within a VPC and to the internet. Without a route table, traffic would not be able to flow between different subnets within a VPC or to the internet.

**Creating a route table**

To create a route table, follow these steps:

1.  Click on the **Route Tables** tab on the left panel of the VPC dashboard.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695387313003/95d91283-1e5a-47d1-97b3-d727f498363a.png?auto=compress,format&format=webp)
    
2.  Click on the **Create route table** button.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695387346802/f086e962-6ccb-496d-8e7a-d246d3b4ac12.png?auto=compress,format&format=webp)
    
3.  Under **Route table settings**, give your route table a name, such as "Border RT".
    
4.  Select the VPC that you created in the previous steps.
    
5.  Click on the **Create route table** button.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695387430956/49314edd-b99c-43fe-9d7c-9a2febf756d8.png?auto=compress,format&format=webp)
    

This will create a route table in the selected VPC. You can now add routes to the route table to control how traffic is routed within the VPC and to the internet.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695387468357/44e76bba-086c-48ab-a182-3dbc2170c252.png?auto=compress,format&format=webp)

1.  To associate the "Border RT" route table to the border subnet under subnet associations, Under the **Subnet associations** tab, click

**Edit subnet associations**.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695387863064/edd9e9d4-4c46-435e-9e91-832357b68763.png?auto=compress,format&format=webp)

Select the **border subnet** checkbox.

Click **Save Associations**.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695387894074/ec15e436-f027-4318-b3ef-2e69a0e9c708.png?auto=compress,format&format=webp)

* * *

Create an Internet Gateway
--------------------------

**What is an internet gateway?**

An internet gateway is a highly available device that allows you to connect your VPC to the internet. It provides a central egress point for internet traffic from your VPC.

**Why do we need an internet gateway?**

An internet gateway is necessary to allow resources in your VPC to access the internet. Without an internet gateway, resources in your VPC will not be able to access the internet.

**Creating an Internet gateway**

To create an internet gateway, follow these steps:

1.  Click on the **Internet gateways** tab on the left panel of the VPC dashboard.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695388374259/fb40f31d-2628-47da-a7d9-a9f65b97901e.png?auto=compress,format&format=webp)
    
2.  Click on the **Create Internet Gateway** button.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695388408626/ffd395f0-67a2-45ee-830d-c41e43ea6f5b.png?auto=compress,format&format=webp)
    
3.  Under **Internet gateway settings**, give your Internet gateway a name, such as "border GW".
    
4.  Click on the **Create Internet Gateway** button.
    

This will create an internet gateway in your AWS account.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695388458259/f18cba9a-85e0-4195-a380-c341d970f5d0.png?auto=compress,format&format=webp)

**Attaching the internet gateway to the VPC**

To attach the internet gateway to the VPC, follow these steps:

1.  Go to the **Internet gateways** page in the Amazon VPC console.
    
2.  Select the **border GW** internet gateway.
    
3.  Under the **Actions** menu, click **Attach to VPC**.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695388542156/7fb8d240-02d3-40b2-97d8-227361738fa2.png?auto=compress,format&format=webp)
    
4.  Select the VPC that you created in the previous steps.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695388572901/d0fa130d-3935-4a86-97b6-712d15041546.png?auto=compress,format&format=webp)
    
5.  Click **Attach Internet Gateway**.
    

This will attach the "border GW" internet gateway to the VPC. Resources in the VPC will now be able to access the internet through the "border GW" internet gateway.

**Note:** Internet gateways that are created are detached by default. You must explicitly attach the internet gateway to the VPC before resources in the VPC can access the internet.

* * *

**Create a Security Group for the Border Subnet**
-------------------------------------------------

**What is a security group?**

A security group is a firewall that controls inbound and outbound traffic to the instances in your VPC. It acts as a virtual firewall for your instances, protecting them from unauthorized access.

**What are inbound and outbound rules in a security group?**

Inbound rules control which traffic can reach your instances, while outbound rules control which traffic can leave your instances.

**Creating a security group**

To create a security group, follow these steps:

1.  Click on the **Security groups** option under **Security** in the left panel of the VPC dashboard.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695389655017/b08b91d9-7203-4611-ba75-a3ec750c4396.png?auto=compress,format&format=webp)
    
2.  Click on the **Create Security Group** button.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695389680939/89699675-1246-4389-a1cf-7a8c0df17cde.png?auto=compress,format&format=webp)
    
3.  Under **Basic details**, give your security group a name, such as "Border SG".
    
4.  Enter a proper description.
    
5.  Under **VPC**, select the VPC that you created in the previous steps.
    
6.  Click on the **Create Security Group** button.
    

This will create a security group in your VPC.

**Editing inbound and outbound rules**

To edit the inbound and outbound rules for the security group, follow these steps:

1.  Under the **Inbound Rules** tab, click on the **Add Rule** button.
    
2.  Under **Type**, select **SSH**.
    
3.  Under **Source**, select **Anywhere**.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695389895310/a2d9f425-4a19-468f-9106-6321f4a43d86.png?auto=compress,format&format=webp)
    

This will add a rule to the inbound rules of the security group that allows SSH traffic from anywhere.

You can also add additional rules to the inbound and outbound rules of the security group, depending on your specific needs. For example, you could add a rule to the inbound rules that allows HTTP traffic from only specific IP addresses.

**Important:** It is important to configure the security groups in your VPC carefully to ensure that your instances are properly protected. Leaving the security groups open to too much traffic can increase the risk of attack.

* * *

**Create a Machine Inside the Border Subnet**
---------------------------------------------

**To create a machine inside the Border subnet:**

1.  In the AWS Management Console, search for **EC2** and select the **EC2** service.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695390891034/0a90fed8-40a7-41e0-a499-f6f9f41a09c9.png?auto=compress,format&format=webp)
    
2.  Click on the **Launch Instance** button.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695390925285/d9ecbb39-7bd3-4c20-9897-c708c9051512.png?auto=compress,format&format=webp)
    
3.  Under Names and tags provide a name for the instance, in this example, it's "PublicInstance".
    
4.  Under **Choose an Amazon Machine Image (AMI)**, select the AMI for the Ubuntu operating system.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695391073410/63f2953f-1b0e-499d-89bf-f6432794400d.png?auto=compress,format&format=webp)
    
5.  Under **Instance type**, select the **t2.micro** instance type.
    
6.  Under **Key pair**, select the key pair that you created in a previous step.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695391121328/40cc8af3-dfc7-4934-aba7-04ab6762bde7.png?auto=compress,format&format=webp)
    
7.  Under **Network settings**, select the VPC that you created in a previous step.
    
8.  Under **Subnet**, select the Border subnet.
    
9.  Under **Security Groups**, select the Border SG security group.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695391187508/72397ab0-9da2-4a7e-9ff7-649136c6907b.png?auto=compress,format&format=webp)
    
10.  Click on the **Launch Instance** button.
    

This will launch an EC2 instance in the Border subnet with the specified AMI, instance type, key pair, VPC, subnet, and security group.

**Additional notes:**

*   **Enable auto-assign public IP:** This will assign a public IP address to your EC2 instance. This is necessary if you want to access your EC2 instance from the internet.
    
*   **Select existing security group:** This allows you to select an existing security group to associate with your EC2 instance.
    
*   **Border SG:** This is the security group that you created in a previous step.
    

Once the EC2 instance has launched, you can connect to it using the SSH protocol. To do this, you will need to use the SSH private key that you downloaded when you created the key pair.

* * *

**Remotely SSH Login to the PublicInstance Using Terminal**
-----------------------------------------------------------

Before we remotely connect to our PublicInstance, we need to edit the route for Border RT, where the destination is 0.0.0.0/0 which is anywhere on the internet, target as border GW that we created in the previous steps and save changes:

1.  Go to the **Route tables** page in the Amazon VPC console.
    
2.  Select the **Border RT** route table.
    
3.  Under the **Routes** tab, click on the **Edit Routes** button.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695392730484/4ef8f6f3-aa33-4d8f-a112-b03eb784d32d.png?auto=compress,format&format=webp)
    
4.  Click on the **Add Route** button.
    
5.  Under **Destination**, enter `0.0.0.0/0`.
    
6.  Under **Target**, select the **border GW** internet gateway.
    
7.  Click on the **Save** button.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695392786564/39cfbfea-d825-4a47-b751-5ac2cdfe4a86.png?auto=compress,format&format=webp)
    

Now, To remotely SSH log in to the PublicInstance using the terminal:

1.  Copy the public IP address of the PublicInstance machine. You can find the public IP address in the AWS Management Console by going to the EC2 service and selecting the PublicInstance instance.
    
2.  Open a terminal window.
    
3.  Run the following command, replacing `<Public-IP-Address>` with the public IP address of the PublicInstance machine:
    

```
ssh ubuntu@<Public-IP-Address>

```


You will be prompted to enter your SSH private key. Enter the SSH private key that you downloaded when you created the key pair.

If the SSH connection is successful, you will be logged in to the PublicInstance machine.

**Example:**

```
ssh ubuntu@192.168.1.100

```


This will log in to the PublicInstance machine with the public IP address 192.168.1.100.

Once you are logged in to the PublicInstance machine, you can start using it like any other Linux machine. You can run commands, install software, and create files.

**Important:** Do not share your SSH private key with anyone else. Your SSH private key is the key to your EC2 instance. If someone else has your SSH private key, they will be able to log in to your EC2 instance and do anything they want.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695393397576/60ed5d8c-a540-472a-9295-2720279c536a.png?auto=compress,format&format=webp)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695393430651/56555df8-3ac8-4190-a1e8-85cd2de3de96.png?auto=compress,format&format=webp)

Do not worry about me exposing my public IP address of the instance, I have deleted all the resources :D

* * *

**Half the work done: Now it's time to create a private subnet**
----------------------------------------------------------------

So far, we've created a VPC with a public subnet and launched an ec2 machine which will act as a NAT gateway. This is a good start, but we're only halfway there. Now we need to create a private subnet for our application servers.

### **Why do we need a private subnet?**

We need a private subnet because we want to protect our application servers from direct access to the internet. By putting our application servers in a private subnet, we can use our NAT gateway to control all inbound and outbound traffic.

**Creating a private subnet**

To create a private subnet, follow these steps:

1.  Go to the VPC service in the AWS Management Console.
    
2.  Under **Resources**, click on **Subnets**.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695386437214/85144cc9-9323-4981-87bc-dd7111dea2a3.png)
    
3.  Click on the **Create Subnet** button.
    
    note: Make sure to create the subnet under the same VPC that we created earlier
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695386507696/e02f45e5-20aa-4e88-ad0d-967852897a67.png)
    
4.  Give your subnet a name, such as `app subnet`.
    
5.  Select the VPC that you created in a previous step.
    
6.  Under **Subnet settings**, select the **Availability Zone** where you want to create the subnet.
    
7.  Under **IPv4 CIDR block**, enter a CIDR block for your subnet. Make sure that the CIDR block is within the CIDR block of your VPC.
    
8.  Click on the **Create Subnet** button.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695972905309/f0a7886c-c475-4ffd-9e8e-ed7ce87ccb7e.png?auto=compress,format&format=webp)
    

This will create a private subnet in your VPC.

* * *

**Creating Route Table for App Subnet**
---------------------------------------

To create a route table for the App subnet:

1.  Go to the **Route tables** page in the Amazon VPC console.
    
2.  Click on the **Create route table** button.
    
3.  Under **Route table settings**, give your route table a name, such as "App RT".
    
4.  Select the VPC that you created in a previous step.
    
5.  Click on the **Create route table** button.
    

This will create a route table in your VPC.

**Note:** You can create multiple route tables in a VPC, but each subnet can only be associated with one route table.

**Next steps:**

Once you have created the App RT route table, you need to associate it with the App subnet. To do this, follow these steps:

1.  Go to the **Route tables** page in the Amazon VPC console.
    
2.  Select the **App RT** route table.
    
3.  Under the **Subnet Associations** tab, click on **Edit Subnet Associations**.
    
4.  Select the **App subnet** checkbox.
    
5.  Click on the **Save Associations** button.
    

This will associate the App RT route table with the App subnet.

### Here comes the interesting part hmm....

**To add a route to the App RT route table to route all traffic to the PublicInstance instance:**

1.  Go to the **Route tables** page in the Amazon VPC console.
    
2.  Select the **App RT** route table.
    
3.  Under the **Routes** tab, click on the **Edit Routes** button.
    
4.  Click on the **Add Route** button.
    
5.  Under **Destination**, enter `0.0.0.0/0`.
    
6.  Under **Target**, select the **PublicInstance** instance.
    
7.  Click on the **Save** button.
    

This will add a route to the App RT route table that tells traffic to anywhere on the internet to go through the PublicInstance instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695974097992/52787cc4-3506-49c3-bd43-96d46cbcbe32.png?auto=compress,format&format=webp)

**Why is this necessary?**

The 'PublicInstance' instance is acting as a NAT gateway for the App subnet. This means that all traffic from the App subnet to the internet must go through the PublicInstance instance.

By adding a route to the App RT route table that routes all traffic to the PublicInstance instance, we are ensuring that all traffic from the App subnet to the internet is routed through the NAT gateway.

**Important:** If you do not add this route to the App RT route table, traffic from the App subnet to the internet will not be routed through the NAT gateway. This could pose a security risk, as resources in the App subnet would be directly exposed to the internet.

* * *

**Create a Security Group for the App Subnet**
----------------------------------------------

To create a security group for the App subnet:

1.  Go to the **Security Groups** page in the Amazon VPC console.
    
2.  Click on the **Create Security Group** button.
    
3.  Under **Basic details**, give your security group a name, such as "App SG".
    
4.  Enter a proper description.
    
5.  Under **VPC**, select the VPC that you created in a previous step.
    
6.  Click on the **Create Security Group** button.
    

This will create a security group in your VPC.

**Editing Inbound and Outbound Rules**

Once you have created the App SG security group, you need to edit the inbound and outbound rules to allow traffic.

To edit the inbound rules:

1.  Go to the **Security Groups** page in the Amazon VPC console.
    
2.  Select the **App SG** security group.
    
3.  Under the **Inbound Rules** tab, click on the **Add Rule** button.
    
4.  Under **Type**, select **All Traffic**.
    
5.  Under **Source**, select **Anywhere**.
    
6.  Click on the **Save** button.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696055193821/06036c8b-958b-4212-bcb2-15bc7f9c57f9.png?auto=compress,format&format=webp)
    

Now, for outbound rules:

1.  Go to the **Security Groups** page in the Amazon VPC console.
    
2.  Select the **App SG** security group.
    
3.  Under the **Outbound rules** tab, make sure that the following rule is selected.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695981353564/b7dc366c-9f4e-49e4-9bde-aa6fd5e0ad9f.png?auto=compress,format&format=webp)
    
4.  Click **save rules**.
    

but but but but🍑, what did we just do???

Now that you have created a security group for the App subnet and edited the inbound and outbound rules to allow traffic from anywhere, you can start launching application servers in the App subnet. The application servers will be able to receive traffic from anywhere on the internet.

* * *

now what????

### **Create a Machine Inside the App Subnet**

To create a machine inside the App subnet:

1.  Search for **EC2** in the search bar and select the **EC2** service.
    
2.  Click on the **Launch Instance** button.
    
3.  Under **Choose an Amazon Machine Image (AMI)**, select the AMI for the **Ubuntu** operating system.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695975369165/87a4facd-a52f-4bb0-9c1d-5e43c6d240aa.png?auto=compress,format&format=webp)
    
4.  Under **Instance type**, select the **t2.micro** instance type.
    
5.  Under **Key pair**, select the key pair that you created in a previous step.
    
6.  Under **Network settings**, select the VPC that you created in a previous step.
    
7.  Under **Subnet**, select the App subnet.
    
8.  Disable **Auto-assign public IP**. This will ensure that the PrivateInstance machine does not have a public IP address.
    
9.  Under **Firewall**, select **Select existing security group**.
    
10.  Select the **App SG** security group from the common security groups menu.
    
11.  Click on the **Launch Instance** button.
    

This will launch a PrivateInstance machine in the App subnet.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695975459960/c217fc7e-2de3-48a1-abbb-18aa034855e5.png?auto=compress,format&format=webp)

**Why Disable Auto Assign Public IP?**

We disable the **Auto-assign public IP** because the PrivateInstance machine does not need to be accessible from the internet. The PrivateInstance machine will communicate with the internet through the PublicInstance instance, which is acting as a NAT gateway.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695975292844/07444bf0-d2a2-4f8f-9920-48ef5b184c76.png?auto=compress,format&format=webp)

* * *

### So, does the machine in our Border Subnet 'PublicInstance' will act as a NAT gateway?

Simple answer: NO, नहीं, না, కాదు, இல்லை, ಇಲ್ಲ, ਨਹੀਂ , નહિં, नाही, ഇല്ല

To make this happen we need to make sure a few things are enabled and are in the right place.

The machine in the Border Subnet 'PublicInstance' will act as a NAT gateway once you run the following commands:

Note: You need to run these commands on 'PublicInstance', make sure you SSH login to the 'PublicInstace' and execute these commands.

```
echo 1 | sudo tee /proc/sys/net/ipv4/conf/all/forwarding
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

```


**What do these commands do?**

The first command enables IP forwarding on the PublicInstance machine. This allows the PublicInstance machine to forward traffic between its network interfaces.

The second command creates a NAT rule that tells the PublicInstance machine to masquerade all outgoing traffic from its eth0 interface. This means that the PublicInstance machine will use its public IP address for all outgoing traffic, regardless of the IP address of the device that originated the traffic.

**How does this make the PublicInstance machine a NAT gateway?**

When a device in the App subnet sends traffic to the internet, the traffic is first routed to the PublicInstance machine. The PublicInstance machine then forwards the traffic to the internet using its public IP address. The response traffic from the internet is routed back to the PublicInstance machine, which then forwards it to the device in the App subnet that originated the request.

**Why is this important?**

NAT gateways allow multiple devices on a local network to share a single public IP address for outbound traffic. This is important because public IP addresses are a limited resource. By using a NAT gateway, multiple devices on a local network can access the internet without each device needing its public IP address.

* * *

Are we done now?

Hmmmm, not yet. not done yet. You may ask "Bruhh frrr??? WHYYYYY?"

because, To connect to the PrivateInstance machine using the PublicInstance machine, you need to edit your SSH configuration file. This file is located in the `.ssh` directory in your home directory.

To edit the SSH configuration file, open a terminal window and navigate to the `.ssh` directory:

```
cd ~/.ssh

```


Then, open the `config` file in a text editor:

```
nano config

```


Add the following two Host entries to the `config` file:

```
Host PublicInstance
  HostName 54.67.28.52
  ForwardAgent yes
  User ubuntu
  StrictHostKeyChecking no
  IdentityFile ~/.ssh/id_rsa

Host 10.0.10.114
  ProxyCommand ssh -q -W %h:%p PublicInstance
  ForwardAgent yes
  StrictHostKeyChecking no
  IdentityFile ~/.ssh/id_rsa
  User ubuntu

```


**Replace the following values (enter your machine IP addresses):**

*   `34.214.170.91` with the public IP address of the PublicInstance machine.
    
*   `10.0.10.41` with the private IP address of the PrivateInstance machine.
    

**Save and close the** `config` file.

Now, you can connect to the PrivateInstance machine using the following command:

```
ssh ubuntu@PrivateInstance

```


This command will use the SSH configuration file to connect to the PrivateInstance machine through the PublicInstance machine.

**Explanation of the Host entries**

The Host entry for the PublicInstance machine is fairly straightforward. It specifies the hostname, username, and SSH private key file to use to connect to the PublicInstance machine.

The Host entry for the PrivateInstance machine is a bit more complicated. It uses the ProxyCommand directive to specify that all SSH traffic to the PrivateInstance machine should be routed through the PublicInstance machine. The `-q` option to the `ssh` command tells the `ssh` client to suppress all output. The `-W %h:%p` option tells the `SSH` client to forward all traffic on the specified port to the specified host.

**Example**

The following example shows how to connect to the PrivateInstance machine using the PublicInstance machine:

```
ssh ubuntu@PrivateInstance

```


This will prompt you to enter the SSH private key for the PublicInstance machine. Once you have entered the SSH private key, you will be connected to the PrivateInstance machine.

This process is called **_SSH hopping_**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696055467374/bb7682aa-6a42-4372-b234-bfc23854fd8b.png?auto=compress,format&format=webp)

You can see in the above image that through the magic of SSH hopping.

we connected to our PrivateInstance, even though it had no public IP address.

* * *

VPC Final Boss
--------------

Can our PrivateInstance connect to the internet through our NAT gateway, which is our PublicInstance? Not yet. We can run commands like ping or apt-get update, but we won't see any results.

To make it work we need to enable a source/destination check on your PublicInstance:

1.  Go to the **Instances** page in the AWS Management Console.
    
2.  Select your PublicInstance.
    
3.  Click on **Actions**.
    
4.  From the drop-down menu, select **Network Settings**.
    
5.  Click on **Change source/destination check**.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696056336344/72e8b44e-c602-4489-a571-f0a3b2f483d6.png?auto=compress,format&format=webp)
    
6.  Select the **Stop** checkbox if it is unchecked from the pop-up window.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696056367734/2cc07926-b54d-426e-b126-37444f09b865.png?auto=compress,format&format=webp)
    
7.  Click **Save**.
    

Now let's connect and run the ping command on our PrivateInstance if it can access the Internet via NAT

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696055467374/bb7682aa-6a42-4372-b234-bfc23854fd8b.png)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696056531075/b04b1e15-d4fa-4ff8-947b-6acba3a2d67f.png?auto=compress,format&format=webp)

**Voilà, Boom, Huzzah, ¡Olé!, Bravo, C'est magnifique, Aha, Yippee, Fantástico, Kapow!**

**WE DID ITT!!!!**

We've done it! We can now access the internet from our private machines via NAT. Feeling like a tech genius? Feeling like a Cloud Genius? Feeling like LV Nilesh Ji? Hold your horses. What if I told you that you could automate the entire process using [Terraform](https://github.com/beacloudgenius/ntier), which would create all of these resources for you in minutes?

Don't feel dumb. You've just learned the underlying concepts of cloud networking fundamentals, such as VPCs, subnets, route tables, and security groups. Even if you just completed the exercise and have a basic understanding of how things work, you've accomplished a lot. See you next blog!
