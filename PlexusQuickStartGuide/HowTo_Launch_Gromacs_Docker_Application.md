***

  # How To Launch Gromacs Docker Applications.

***
1. Login to **https://aac.amd.com/**.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/d62dc96e-e37a-42b3-9b0e-72445014a621)

2. Click on Applications. Search for **Gromacs**.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/da7077e0-1488-4495-808d-9d6655f668c4)

3. Select the desired Gromacs version with desired container type as **docker**.

   **Note**: In this case, Gromacs 2022_3 version was selected with container type as docker.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/6023ef04-29df-463d-b244-5e41a5d4dd74)

4. Click on **'New Workload'** button available on the top right corner.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/626a0b85-b92d-4215-affe-ae3e4c9c194c)

5. Click **'Next'** button available on the top right corner.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/5d461b07-04ed-485e-ae97-aebb5c7a6e64)

6. Choose the desired **benchmark** type

   **Note**: Uncomment the type of benchmark that needs to be run. Only **"ONE"** benchmark can be launched at a time. If 
   more than one benchmark, say Adh_Dodec and Cellulose, is uncommented and launched, then the application fails.

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
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/bcd11877-7409-40f9-84f6-18e937eae28b)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/ef020fb3-c314-40ee-8bfe-3497e6df4afc)

8. Select the cluster and queue that are assigned to the team and are available to run the job.
   In this case **1CN128C8G2H_2IB_MI210_SLES15 (Pre-emptible)** was selected. Click on **'Next'** button available on the 
   top right corner.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/2b6e04b2-3328-4d00-8848-8f19ff1be57a)

9. Review Workload Submission. Review the information that has entered for this workload. If any change is needed, it can 
   be changed by clicking in the appropriate sections to make revisions.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/3950c8d3-6ff4-41a0-863c-066d2f5c8d01)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/ecab61af-b816-4ed4-8d2b-74dcd43d8635)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/8171a7ac-8bd0-46d7-9296-65802d410f55)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/c084e5b0-bc25-482c-87b3-09eea4eeb451)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/ff8bb2db-4b5f-4f7f-87dc-cb58aa2755be)

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
     View Log Click on the links shown on the Workload Information screen to view the job log, stdout log and stderr log:
     **View SysLog** - Information about the workload throughout the entire process
     **View Stdout** - Standard output that presents the output of a workload and sometimes includes the results of the 
     workload.
     **View Stderr** - Standard Error that helps you understand why you may have encountered certain issues during the 
     process.
    **Download log files** - Download all information about the Log, STDOUT and Stderr log files.
    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/f35223f7-2789-4de0-a64a-728d3527037b)


13.  The performace value in the **STDERR** tab is the performance of Gromacs docker application.
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/8705664b-491c-475c-be86-5e5ea96662e5)

