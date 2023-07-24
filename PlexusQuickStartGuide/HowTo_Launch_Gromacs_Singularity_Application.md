***

# How To Launch Gromacs Singularity Applications.

***
1. Login to **https://aac.amd.com/**.
  ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/d62dc96e-e37a-42b3-9b0e-72445014a621)

2. Click on Applications. Search for **Gromacs**.
  ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/da7077e0-1488-4495-808d-9d6655f668c4)

3. Select the desired Gromacs version with desired container type as **singularity**.

   **Note**: In this case, Gromacs 2022_3 version was seletced with container type as singularity.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/17a60c0f-7836-489c-8ba9-107f82479d8e)

4. Click on **'New Workload'** button available on the top right corner.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/84d85f53-80d7-48c6-a9ad-3743cbbf8ac8)

5. Click **'Next'** button available on the top right corner.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/2e1c452c-9e86-4723-b394-f9cc89fe9b26)

6. Choose the desired **benchmark** type

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
   
7. Here the run time is selected as **'1 hour'** with telemetry enabled. The number of **GPU's** are selected as **'8'**.

    Click on **'Next'** button available on the top right corner.
    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/d201159a-4298-4ba6-b118-9c04eb7c4f92)
    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/05a7bc0d-ecf2-4541-ac38-2ebb162be9a4)

8. Select the cluster and desired queue to run the job. In this case **1CN128C8G2H_2IB_MI210_RHEL8 (Pre-emptible)** was 
   selected. Click on **'Next'** button available on the top right corner.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/2c5d4b9d-d0b2-456b-b4f1-93c88f2d9dc0)

9. Review Workload Submission. Review the information that has entered for this workload. If any change is needed, it can 
   be changed by clicking in the appropriate sections to make revisions.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/a81f1d26-ae41-4adb-9d31-d46ced6f228e)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/9a8df735-bb44-4a21-8566-57e60f63b6dc)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/f0d32676-61cd-49a1-8dca-743e08af14ed)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/b3d98c0a-5673-4f15-a41f-73fae6f830e0)

   **Note**: Please note that the payment information might be different from the above image because you might be added 
   to a different team.

10. After submitting a workload, user can monitor how the workload is performing by checking the Workload Status 
    on the Workloads page and the Workload Information page:
    Each workload goes through several different states after it is submitted -
    **Created** – The workload has been created in the system.
    **Sent** – The workload has been sent to the queue that you selected in the workload submission process.
    **Pending** – The workload is in a waiting state in the queue.
    **Running** – The workload has started running in the selected queue.
    **Completed** – The workload has successfully finished processing.
    **Failed** – A problem has occurred which has prevented the workload from completing successfully.
    **Cancelled** – The workload has been canceled by the user and stopped running.

11.  Once the application execution is successful then the status gets changed into **“Completed”**. The user can check the 
     **STDOUT** and **STDERR** logs by clicking on respective tabs. The Performace tab shows the telemetry collected.
    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/1b4744ae-ef6d-4e88-9876-a84c7e3fb315)

12.  The performace value in the **STDERR** tab is the performance of Gromacs singularity application.
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/44421288-3098-4071-84bb-d5495da7dbc9)
