***

# How To Launch Gromacs Singularity Applications.

***
**1.** Login to **https://aac.amd.com/**.
    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/d62dc96e-e37a-42b3-9b0e-72445014a621)

**2.** Click on Applications. Search for **Gromacs**.
    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/604d39d8-e532-4ba6-8710-fde299532a09)

**3.** Select the desired Gromacs version with desired container type as **singularity**.

   **Note**: In this case, Gromacs 2022_3 version was seletced with container type as singularity.
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/59d310df-98af-4510-85a8-9bbcd6d2aae6)

**4.** Click on **'New Workload'** button available on the top right corner.
    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/f537e6c2-7d75-433f-a497-038b1e5153a5)

**5.** Click **'Next'** button available on the top right corner.
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/2323ea6f-ea88-4281-bd5f-4115c0dc05bf)

**6.** Choose the desired **benchmark** type

   **Note**: Uncomment the type of benchmark that needs to be run. Only "ONE" benchmark can be launched at a time. If more 
   than one benchmark, say Adh_Dodec and Cellulose, is uncommented and launched, then the application fails.

   Benchmark type 1 : **Adh_Dodec**

   Uncomment the Adh_Dodec benchmark command from the run script to execute the Adh_Dodec benchmark.
   nstlist=180; ntomp=16; cd /benchmarks/adh_dodec; tar -xvf adh_dodec.tar.gz
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/d7d5b24b-528a-4f19-85a1-513dfba6da33)

   Benchmark type 2 : **Cellulose**
   
   Uncomment the Cellulose benchmark command from the run script to execute the Cellulose benchmark.
   nstlist=320; ntomp=16; cd /benchmarks/cellulose_nve; tar -xvf cellulose_nve.tar.gz
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/0cce3cf4-3ac3-4b3e-a824-e16cda772fc1)
   
   Benchmark type 3 : **STMV**

   Uncomment the STMV benchmark command from the run script to execute the STMV benchmark.
   Here nstlist=400; ntomp=8; cd /benchmarks/stmv; tar -xvf stmv.tar.gz; was uncommented.
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/ce295445-de0b-49fd-a229-47f405e19262)
   
**7.** In the following image, the maximum run time is selected as **'1 hour'** with telemetry enabled. The number of **GPU's** are selected as **'8'**.
    Click on **'Next'** button available on the top right corner.
      ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/a49a1a9e-8ebd-4d05-924a-94a8fc196a21)
      ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/0310dc93-9766-4ece-9d69-02207101a265)

**8.** Select the cluster and desired queue to run the job. In this case **1CN128C8G2H_2IB_MI210_RHEL8 (Pre-emptible)** was 
   selected. Click on **'Next'** button available on the top right corner.
   The availables queues are **AAC Plano**, **AAC Plano RHEL** and **CirraScale.**
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/633f304b-e706-4c0f-87fb-1ef28850f621)

**9.** Review Workload Submission. Review the information that has entered for this workload. If any change is needed, it can 
   be changed by clicking in the appropriate sections to make revisions.
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/342586f0-f873-4583-aa0b-d01ecacfc09d)
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/94e21c69-acef-4d49-96e1-67a99938506e)
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/07443e53-068e-4dcd-9bf3-06b8e644779f)
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/dac0df0d-eede-450a-ace3-37715f7fe91d)
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/b291e7fe-88f8-44b7-a5ba-7dfc6f5def21)
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/e1d4c47d-9940-4278-9abd-6d2cf9ff8a59)

   **Note**: Please note that the payment information might be different from the above image because you might be added 
   to a different team.

**10.** After submitting a workload, user can monitor how the workload is performing by checking the Workload Status 
    on the Workloads page and the Workload Information page.Each workload goes through several different states after it is submitted -

  **Created** – The workload has been created in the system.

  **Sent** – The workload has been sent to the queue that you selected in the workload submission process.

  **Pending** – The workload is in a waiting state in the queue.

  **Running** – The workload has started running in the selected queue.

  **Completed** – The workload has successfully finished processing.

  **Failed** – A problem has occurred which has prevented the workload from completing successfully.

  **Cancelled** – The workload has been canceled by the user and stopped running.

**11.**  Once the application execution is successful then the status gets changed into **“Completed”**. The user can check the 
     **STDOUT** and **STDERR** logs by clicking on respective tabs. The Performace tab shows the telemetry collected.
View Log Click on the links shown on the Workload Information screen to view the job log, stdout log and stderr log:

  **View SysLog** - Information about the workload throughout the entire process

  **View Stdout** - Standard output that presents the output of a workload and sometimes includes the results of the 
     workload.

  **View Stderr** - Standard Error that helps you understand why you may have encountered certain issues during the 
     process.

  **Download log files** - Download all information about the Log, STDOUT and STDERR log files.

    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/1b4744ae-ef6d-4e88-9876-a84c7e3fb315)

**12.**  The performace value in the **STDERR** tab is the performance of Gromacs singularity application.
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/44421288-3098-4071-84bb-d5495da7dbc9)
