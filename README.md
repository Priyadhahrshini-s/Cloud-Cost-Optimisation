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

_*Click on create function and hence we created a lambda function*_

_*Write the code on code source and click on deploy*_

<img width="843" alt="Screenshot 2024-01-21 102734" src="https://github.com/Priyadhahrshini-s/Cloud-Cost-Optimisation/assets/157268341/d888d3a5-f992-4858-b7a5-9508158c1d04">

_*Click on Test and name the event*_
<img width="611" alt="Screenshot 2024-01-21 102818" src="https://github.com/Priyadhahrshini-s/Cloud-Cost-Optimisation/assets/157268341/1d478329-7695-4c58-8749-d27211c6bfe1">


_*The test will be failed because the default lambda function exective time is 3 second and it also show snapshot ,volume ,instances are not described*_

_*To increase the execution time go to configuration tab and click on edit and increase the timeout to 10 second*_
 _*Now go to permission and click on role name*_

<img width="826" alt="Screenshot 2024-01-21 103455" src="https://github.com/Priyadhahrshini-s/Cloud-Cost-Optimisation/assets/157268341/90e72a71-b4c1-4f1a-83ca-29fb749719b1">

_*Now add permissions to the role *_
_*click on create inline policy *_

<img width="633" alt="Screenshot 2024-01-21 104028" src="https://github.com/Priyadhahrshini-s/Cloud-Cost-Optimisation/assets/157268341/20f0f9f4-f0da-428d-92eb-b96454025f08">

_*Choose EC2 as a service and add the actions that are shown below*_
* Delete snapshot
* Describe snapshot
* Describe instances
* Describe volumes

_*Select the resources for all*_

_*Click on Next and give the Policy name*_

<img width="633" alt="Screenshot 2024-01-21 104028" src="https://github.com/Priyadhahrshini-s/Cloud-Cost-Optimisation/assets/157268341/16a83aaa-e690-481d-9e70-70833bc5e5c1">

_*Now go and run the test*_

<img width="831" alt="Screenshot 2024-01-21 104939" src="https://github.com/Priyadhahrshini-s/Cloud-Cost-Optimisation/assets/157268341/788c04ac-2628-499e-8be0-385013fcbf04">

_*Hence the script got executed*_

_*Let's check whether it is working after deleting the instance. Go to EC2 dashboard and select the instance that we created and on action tab click terminate instace_*

<img width="763" alt="Screenshot 2024-01-21 105034" src="https://github.com/Priyadhahrshini-s/Cloud-Cost-Optimisation/assets/157268341/b090cd59-a01b-4edf-a3ac-2c738aa66734">

_*Hence the instance got termninated so the volume attached to the instance also got deleted.But the snapshot that we created is there*_
_*Now go to lambda function and to source code click on test_*

<img width="856" alt="Screenshot 2024-01-21 105220" src="https://github.com/Priyadhahrshini-s/Cloud-Cost-Optimisation/assets/157268341/ceb82f54-e372-4160-8644-02c3ceed8b60">

_*Now the EBS snapshot is deleted by exection the lambda function*_
 _*Go to cloud watch and go to rules and click on events*_

 _*Give the Rule name and click on schedule rule type and click on next*_
 <img width="841" alt="Screenshot 2024-01-21 105551" src="https://github.com/Priyadhahrshini-s/Cloud-Cost-Optimisation/assets/157268341/f612ef36-0939-44e5-9ac3-6d6a1ecdc46e">
<img width="599" alt="Screenshot 2024-01-21 105615" src="https://github.com/Priyadhahrshini-s/Cloud-Cost-Optimisation/assets/157268341/e91c067a-e52c-40b6-b569-4eef6d29d884">

_*On schedule pattern give the time and date and invoking duration*_
<img width="601" alt="Screenshot 2024-01-21 105825" src="https://github.com/Priyadhahrshini-s/Cloud-Cost-Optimisation/assets/157268341/27558eeb-69ee-4008-980b-7a7e6991ed21">

_*Click on next and Hence the cloud watch is created*_

_*So the cloud watch and Lambda function will work together to reduce the cost*_
