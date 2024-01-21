# Cloud-Cost-Optimisation

### Prerequisites:

* AWS Account

## Step 1:Launcgh an EC2 instance
_*Log in to the Amazon management console, open EC2 Dashboard, click on the Launch Instance drop-down list, and click on Launch Instance:*_
_*Once the Launch an instance window opens, provide the name of your EC2 Instance:*_

<img width="681" alt="Screenshot 2024-01-21 101521" src="https://github.com/Priyadhahrshini-s/Cloud-Cost-Optimisation/assets/157268341/785bf451-9317-4d89-994c-2e489c757996">

_Choose an Instance Type. Here you can select the type of machine, number of vCPUs, and memory that you want to have. Select t2.micro which is free-tier eligible._

<img width="599" alt="Screenshot 2024-01-21 101622" src="https://github.com/Priyadhahrshini-s/Cloud-Cost-Optimisation/assets/157268341/adb39f08-af16-4848-9c81-444830fe0f3a">

_Rest of the settings we will keep them at default and go ahead and click on Launch Instance_

_On the next screen you can see a success message after the successful creation of the EC2 instance:_

<img width="771" alt="Screenshot 2024-01-21 101903" src="https://github.com/Priyadhahrshini-s/Cloud-Cost-Optimisation/assets/157268341/05001033-17ee-44b6-a04d-a8f2b8ee0a62">

## Step 2:Create a snapshot
 _*Go to EC2 dashboard and click on snapshot and click on create snapshot*_
 _*Select the source type as volume and  click on the volume ID which is attached to EC2 instance*_
 
 <img width="638" alt="Screenshot 2024-01-21 102056" src="https://github.com/Priyadhahrshini-s/Cloud-Cost-Optimisation/assets/157268341/d4fee6c0-0ab2-4c34-95b9-6c184829be57">

_*Hence the snapshot is created*_

## Step 3:Create a Lambda Function
 _*Go to Lambda dashboard and click on create function*_
 
 _*Choose author from scratch to create a lambda function*_
 
 <img width="875" alt="Screenshot 2024-01-21 102351" src="https://github.com/Priyadhahrshini-s/Cloud-Cost-Optimisation/assets/157268341/6845f029-4e31-4d38-b9b2-a5d21a3a14f8">
 *_Choose python as the language to write the function*_
 
<img width="776" alt="Screenshot 2024-01-21 102414" src="https://github.com/Priyadhahrshini-s/Cloud-Cost-Optimisation/assets/157268341/07ce5ef8-c308-4362-8b74-da91394ef221">

*_Click on create function and hence we created a lambda function*_

*_Write the code on code source and click on deploy*_

<img width="843" alt="Screenshot 2024-01-21 102734" src="https://github.com/Priyadhahrshini-s/Cloud-Cost-Optimisation/assets/157268341/d888d3a5-f992-4858-b7a5-9508158c1d04">

*_Click on Test to check whether it is running or not*_
*_It will show snapshot ,volume ,instances are not described. So to allow this attach








