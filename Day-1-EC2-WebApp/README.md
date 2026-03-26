<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Set Up a Web App in the Cloud

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-devops-vscode)

**Author:** Abhijeet Pandit  
**Email:** clipex39@gmail.com

---

## Set Up a Web App Using AWS and VS Code

![Image](http://learn.nextwork.org/thoughtful_turquoise_happy_river_turtle/uploads/aws-devops-vscode_7a1de541)

---

## Introducing Today's Project!

This project is  Day one of a seven day Devops Challenge ! In this project, we're going to set up the foundation of a CI/CD pipeline by creating a web app from scratch. We'll need to launch an EC2 instance and connect to the instance using VScode to generate a web app inside.                                                                                       

This project is part one of a series of DevOps projects where I'm building a CI/CD pipeline! I'll be working on the next project tomorrow :)

I did this project to kickstart the 7 day DevOps challenge. Challenge well Accepted now !! And its great to set up a web app in the cloud using EC2 and VS Code. 

### Key tools and concepts

Services I used were VSCode and EC2. Key concepts I learnt include SSH connections, using an IDE, launching an instance, editing an index file, using key pairs.

### Project reflection

This project took me approximately 3 hours including  full demo time and some troubleshooting time !! It was most rewarding to see a successful SSH connection to our EC2 instance, whether that's over the terminal or over the VS Code SSH connection.

One thing I didn't expect in this project was 

---

## Launching an EC2 instance

### What I did in this step

In this step, we are launching an EC2 instance in our AWS account! We're also going to set up its network settings which helps us Find our EC2 Instance and our key pair, Which helps us make sure we have the permission to access the EC2 Instance.     

I started this project by launching an EC2 instance because EC2 Insances are like virtual computers that live in the cloud! We want our web app to live enitirely in the cloud, so we're launching an EC2 instance to even develop our web app's code.

![Image](http://learn.nextwork.org/thoughtful_turquoise_happy_river_turtle/uploads/aws-devops-vscode_7852fbf3)

### I also enabled SSH

SSH is. the protocol that authorizers users (like ousrselves) to access remote servers (like EC2 Instance). It's also a type of traffice that lets us transfer data back and forth with our EC2 Instance once we're connected. I enabled SSH so that I can securely connect to our EC2 Instance later , and we made sure that it only allows SSH traffic from our IP address for securely.




### Key pairs

A key pair is a mechanism for us to connect and get access to EC2 instances we launch in AWS. we've created a key pair for the EC2 instance that we're launching. Key pairs work by having two havles- a public key that AWS keeps, and a private key that we download . AWS will authenticate our private key when we want to connect to our EC2 instance later in this project,  by matching it to the private key that it has.

### Downloaded key pair file

Once I set up my key pair, AWS automatically downloaded the private key file, called devops-keypair.pem. For safekeeping, we moved that private key file into a folder called " Devops " into our Desktop.

---

## Set up VS Code

### What I did in this step

In this step, I will install VS Code , which is a tool that lets us write and edit code (and it's free). We're also going o set up a terminal, and update the permission settings of our private key.

### What is VS Code?

VS Code is one of the most popular IDEs in the world; as an IDE, engineers use it to write code and manage their coding project. It also has handy extensions that let us directly connect to an EC2 instance.                                                                                                                                                                                            

I installed VS Code to write and edit our web app's code . We're also going to make the most out of the ability to connect directly with an EC2 instance!

![Image](http://learn.nextwork.org/thoughtful_turquoise_happy_river_turtle/uploads/aws-devops-vscode_53d05e68)

---

## My first terminal commands

A terminal is a place for us to send commands to our computer i.e. tell it what we want it to do. The difference betwwen a terminal and our usual click/drag interface is that we send text commands in the terminal. The first command we ran for this project cd "C:\Users\ABHIJEET PANDIT\OneDrive - Vidyalankar Polytechnic\Desktop\Devops" which navigates the terminal to the Devops Folder.

### Updating file permissions

I also updated my private key's permissions by running the command icacls devops-keypair.pem /inheritance:r
icacls devops-keypair.pem /remove "BUILTIN\Users"
icacls devops-keypair.pem /remove "BUILTIN\Administrators"
icacls devops-keypair.pem /remove "NT AUTHORITY\SYSTEM"
icacls devops-keypair.pem /grant:r "$($env:USERNAME):R" . This command gives ourselves access to use this file so we can connect to an EC2 instance later.

![Image](http://learn.nextwork.org/thoughtful_turquoise_happy_river_turtle/uploads/aws-devops-vscode_9328ada1)

---

## SSH connection to EC2 instance

### What I did in this step

In this step, I will try to connect to our EC2 instance! Once we  connected to the EC2 instance , we can start setting up our web app code inside.

### Connecting to EC2

To connect to my EC2 instance, I ran the command ' ssh -i [private key path] ec2-user@[IPV4 address of EC2 instance]'. This command sets up an SSH connection directly between our local computer and the instance

### This command required an IPv4 address

A server's IPV4 DNS is like its public address that identifies where the server lives in the cloud. In our case, an EC2 instance's IPV4 DNS is useful information to give to our local computer - it tells our local computer where to find the EC2 instance that we launched.

![Image](http://learn.nextwork.org/thoughtful_turquoise_happy_river_turtle/uploads/aws-devops-vscode_e3069dca)

---

## Maven & Java

### What I did in this step

In this step, I will install Maven and Java(Corretto 8)  in our EC2 instance! we're doing this because both tools are helpful for setting up a java web app from scratch. 

### Why I'm using Maven

Apache Maven is a tool that helps us with creating and organizing java projects (like this web app). It comes with lot of use cases, like being a package manager (downloading external pieces of code) and the tool that uses archetypes (templates) for spinning up project like web apps instantly.

Maven is required in this project because i want to use its ability to spin web apps using archetypes! We're about to set up our Java web app using the web app archetypes.

### Why I'm using Java

Java is programming language that we're using to develop our web app. Its a very popular and versatile choice , as you can use it to develop all different kinds of applications, including web apps and enterprise systems.

Java is required in this project because it lays the foundation of the writing our web app code. Its like needing to know a language in order to speak it. Maven also needs java in order to work.

---

## Create the Application

### What I did in this step

In this step, I will generate a web app inside our EC2 instance, using Maven and Java!

### Creating the Java web app

I generated a Java web app using the command ' mvn archetype : generate'. This command tells Maven to generate a web app using an existing template that it has. It also tells Maven to call the generate web app project ' Devops-webapp-project'.

### Installing Remote - SSH

I installed Remote - SSH, which is an extenstion within VS code. This Extension lets us connect VS code directly to a remote server , like  an EC2 instance.

### SSH configuration details

Configuration details required to set up a remote connection include the host name (i.e. the EC2 instance's address), the identity file (i.e. the location of our private key) and the user (i.e. the user that we're login into for our instance).

![Image](http://learn.nextwork.org/thoughtful_turquoise_happy_river_turtle/uploads/aws-devops-vscode_2939cf01)

---

## Create the Application

### Exploring the project structure

Using VS Code's file explorer, I could see a bunch of folders and subfolders that define our web app. Folder can be expanded by clicking on the angled brackets >.

 These folders organise different parts of the web app: for example , the resources sub-folder store connection details, while the web app sub- folder for the look and feel of the web app. src is the parent folder that contains all the source code for the web app.

![Image](http://learn.nextwork.org/thoughtful_turquoise_happy_river_turtle/uploads/aws-devops-vscode_45f91fd7)

---

## Using Remote - SSH

### What I did in this step

In this step, I will connect VS code with our EC2 instance! This is different from just connecting the terminal (i.e. our local computer ) to our instance.

### Updating the web app

The index.jsp is the file in our web app that defines both HTML content (i.e. the static elements that go into our web app's page), as well as any code for generating dynamic content(i.e. content that always changings).

I edited index.jsp by updating the HTML code to also sat hello ! We also  added a paragraph i.e. some text that says " this is my nextwork web app working.

![Image](http://learn.nextwork.org/thoughtful_turquoise_happy_river_turtle/uploads/aws-devops-vscode_7a1de541)

---

## Using nano

### Additional improvements

### Terminal vs IDE

### Verifying my work



---

---
