***

# How To Launch TensorFlow Singularity Multinode Application

***

 **1. Login to https://aac.amd.com/.**
 
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/d62dc96e-e37a-42b3-9b0e-72445014a621)
  
<br/>    

 **2. Click on Applications. Select 'TensorFlow'.**
 
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/b6e3af4a-0aed-4394-92dd-0c29c5778923)


**3. In the 'Select An Application' pop-up, select the TensorFlow multinode version. The container type is singularity**
    
   **Note**: In this case, we have selected **Tensorflow 2-11 Rocm 5-4 Multinode** version and container is singularity.

  ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/78aa3714-8532-455d-83f7-82a11f311999)

    
**4. Click on 'New Workload' button available on the top right corner.**

  ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/b111bda6-e269-447a-9b38-a5bf5c0b12ad)


**5. Click 'Next' button to continue.**

   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/5a650b4e-8867-4c78-a143-67b5c9967319)



 **6. Click 'Next' button to continue.**

   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/e340a121-43cb-48be-a022-a50ee24f27bf)


 **7. In *Select Resources* page, specify the number of GPU's (e.g., 1 GPU) and max allowed runtime required for the workload. Click Next button.**

  **Note:** The maximum number of GPUs should be 8. 
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/9e04814d-18c3-46cf-a1db-32892e81f777)


 **8. Select the cluster and desired queue to run the job. In this case **1CN128C8G2H_2IB_MI210_SLES15 (Pre-emptible) - AAC Plano**  is selected. Click on Next.**

   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/96d3855e-1640-4820-b1f7-7dc5ea0dd9e8)

**9. Review the configurations. Cick 'Run Workload'.**

   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/83aadab5-7390-4763-a483-8d9e0bad9070)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/64bfc5a7-b9f3-431b-ba48-1e45b2864fe6)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/6271faf0-9697-4b8f-b87b-711752a827b3)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/3a523d4b-dc7f-4e15-88f4-f9e075fccc20)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/c78864c7-6de1-450d-a315-6f23e01824bb)


**10. User will be navigated to Workloads page. The status of workload changes to 'Running' once queue is available.**

![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/f3708fd7-3915-45cb-a718-992fa5684313)


**11. User can see the system logs in SYSLOG, output in STDOUT and errors in STDERR tabs.**

![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/e9ef3fe0-739f-4c2f-a43f-0acca7fcdf34)

 
**12. Once workload completes, User can download the output logs from STDOUT tab by clicking 'Download Logs'. The Performance tab shows the telemetry**

![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/e5f18a78-cfa5-4405-a3a3-0cca87f3922a)

 
