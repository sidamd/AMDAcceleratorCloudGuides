***

# How To Run Workload

***

Login to **https://aac.amd.com/**.
    
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/d62dc96e-e37a-42b3-9b0e-72445014a621)

A workload can be launched by following the below 6 steps.

## 1. **Select the desired Application**.

The application for which the workload has to be run can be selected in this step. It can be done in two ways as mentioned below.

&emsp; a. Navigate to **Applications** page. Select desired application for which workload has to be run.
   
&emsp; **Note**: In this case, we have selected Application as **HPCG**.
 
&emsp; ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137474607/5d521fdb-046e-4963-9068-db42f71a59c9)

&emsp; c. Select desired version if prompted. It can be either docker or singularity.

&emsp; **Note**: In this case, we have selected rocHPCG 3.1.0_97 version and container as **docker**.

&emsp; <img src="https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/ee067057-d622-4418-a6ac-1faa977f61c0" width="900">

&emsp; d. Click on **New workload** button

&emsp; <img src="https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/39adef02-85a7-47bf-aee6-41fee259cc0d" width="900">


### &emsp; &emsp; &emsp; &emsp; &emsp; &emsp; &emsp; &emsp; &emsp; &emsp; &emsp; &emsp; &emsp; &emsp;**(or)**


&emsp; a. Navigate to **Workloads** Page. Click **New Workload** button

&emsp; <img src="https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/c926eef4-9f2c-4770-867c-90fb7ad8ddbd" width="900">

&emsp; b. Select desired application for which workload has to be run.

&emsp; **Note**: In this case, we have selected Application as **HPCG**.

&emsp; <img src="https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/ae1c9519-6a84-4d90-88bc-057b7dd69924" width="900">

&emsp; c. Select desired version if prompted. It can be either docker or singularity.

&emsp; **Note**: In this case, we have selected rocHPCG 3.1.0_97 version and container as **docker**.

&emsp; <img src="https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/ee067057-d622-4418-a6ac-1faa977f61c0" width="900">

&emsp; d. Click **Next** button.

&emsp; <img src="https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/b5f29f92-4981-42b6-b060-69774211f756" width="900">

## Select Input Files

The files required for the workload can be uploaded in this step.

&emsp; a. Click **Upload files**.

&emsp; <img src="https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/82bb7a15-2a04-4685-a4c6-94eeeba38553" width="900">

&emsp; b. Click **Browse Files**

&emsp; <img src="https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/1eb244df-3cd0-465a-b67e-1633a1387ba7" width="900">

&emsp; c. Maximum of 5 files can be uploaded at one time. 

&emsp; d. Select the required files. Click **Next**.

&emsp; <img src="https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137474607/e420e08e-5b7b-4a48-819d-fea3d1f8dc7b" width="900">

 6. Click **Next** to continue with default script.
 
    **Note**: Default script is for 8 GPUs

   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137474607/ce2ccd72-1286-458b-a28c-1939d5dd2669)


 7. Select the allowed run time. The number of GPUs should be 8. Here, we have selected the run time as 1 hour, number of GPU’s as 8 and telemetry is enabled.
    Click on **Next**

  ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137474607/0605bc6f-7136-4b7b-9d79-3faf33a444d0)
   

 8. Select the cluster and desired queue to run the job. In this case **1CN128C8G2H_2IB_MI210_SLES15** is selected. Click on **Next**

  ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137474607/6063268b-227c-4a2f-8967-456f69ed1b41)
  

 9. Review all configurations and click on **Run Workload**
 
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137474607/1953602c-4d0f-481d-b42e-5ddfc8ecae39)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137474607/854b206a-c5a8-452a-b2cc-16e99dbadb94)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137474607/854f7e2e-2c5b-47de-a453-6b2ea7ff3728)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137474607/de586d6f-87ad-4e9d-8c4e-b6ebd9a3e49c)


 10. Once the application execution is successful then the status gets changed to **'Completed'**
     
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137474607/4f113aa6-f7ba-4c26-b62e-c3c22df8b552)
   
