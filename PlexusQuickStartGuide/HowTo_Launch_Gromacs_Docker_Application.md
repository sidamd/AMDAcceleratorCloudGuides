***

  # How To Launch Gromacs Docker Applications.

***
**1.** Login to **https://aac.amd.com/**.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/d62dc96e-e37a-42b3-9b0e-72445014a621)

**2.** Click on Applications. Search for **Gromacs**.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/49596b39-38af-4463-91c4-19baacebe5c4)

**3.** Select the desired Gromacs version with desired container type as **docker**.

   **Note**: In this case, Gromacs 2022_3 version was selected with container type as docker.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/38eb9c67-348c-4e8a-9b44-ae769d01d52c)

**4.** Click on **'New Workload'** button available on the top right corner.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/849b86b9-f774-4da9-a13e-850d56cb1a66)

**5.** Click **'Next'** button available on the top right corner.
  ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/b6df3888-dd95-4fac-a481-850c0c224fe4)

**6.** Choose the desired **benchmark** type

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


**7.** In the following image,  the maximum run time is selected as **'1 hour'** with telemetry enabled. The number of **GPU's** are selected as **'8'**.
Click on **'Next'** button available on the top right corner.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/287248f5-0fb3-42d1-a1e0-9c97c3e660ed)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/d35a9410-4113-454c-bd6c-3d0359a0b361)

**8.** Select the cluster and queue that are assigned to the team and are available to run the job.
   In this case **1CN128C8G2H_2IB_MI210_SLES15 (Pre-emptible)** was selected. Click on **'Next'** button available on the 
   top right corner.
   The availables cluters are **AAC Plano**, **AAC Plano RHEL** and **CirraScale.**
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/83320bca-3143-4653-8f5e-8a4e88a8ebde)

**9.** Review Workload Submission. Review the information that has entered for this workload. If any change is needed, it can 
   be changed by clicking in the appropriate sections to make revisions.Click on **'Run Workload**.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/a3a479db-87ac-42a0-a6d1-1488eba9965c)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/63dd2d83-e460-4fdc-b0e1-fafc020d9a30)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/5c672b93-080b-4f00-b4ad-7663b7672967)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/f34d03a4-a152-4580-b577-67bb2c87097b)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/ad967d89-b71f-4e43-9c5a-4dee6bab19cf)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/14d0e9dd-c2e0-4b31-b635-c93eccd343cd)

  **Note**: Please note that the payment information might be different from the above image because you might be added 
   to a different team.

**10.** After submitting a workload, user can monitor how the workload is performing by checking the Workload Status 
    on the Workloads page and the Workload Information page.
   Each workload goes through several different states after it is submitted -

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
    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/f35223f7-2789-4de0-a64a-728d3527037b)


**12.**  The performance value in the **STDERR** tab is the performance of Gromacs docker application.
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/8705664b-491c-475c-be86-5e5ea96662e5)

