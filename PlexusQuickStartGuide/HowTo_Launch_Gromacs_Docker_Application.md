***

  # How To Launch Gromacs Docker Applications.

***
1. Login to **https://aac.amd.com/**.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/5ff0f361-8d9b-42ae-afc8-9c222b56bc63)

2. Click on Applications. Search for **Gromacs**.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/4e804fad-bd92-4fea-a186-a54cc9b8c1fd)

3. Select the desired Gromacs version with desired container type as **docker**.

   **Note**: In this case, we have selected Gromacs 2022_3 version and container as docker.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/a5a1e84e-399e-4a55-83ed-891f642a9782)

4. Click on **'New Workload'** button available on the top right corner.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/626a0b85-b92d-4215-affe-ae3e4c9c194c)

5. Click **'Next'** button available on the top right corner.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/6c67dee6-b99f-474a-8032-8c277054009a)

6. Choose the desired **benchmark** type

   **Note**: Uncomment the type of benchmark that needs to be run. Only **"ONE"** benchmark can be launched at a time. If 
   more than one benchmark, say Adh_Dodec and Cellulose, is uncommented and launched, then the application fails.

   Benchmark type 1 : **Adh_Dodec**

   Here nstlist=180; ntomp=16; cd /benchmarks/adh_dodec; tar -xvf adh_dodec.tar.gz; was uncommented.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/ba3d4919-7df5-48d9-b716-b321ee8c8acf)

   Benchmark type 2 : **Cellulose**

   Here nstlist=320; ntomp=16; cd /benchmarks/cellulose_nve; tar -xvf cellulose_nve.tar.gz; was uncommented.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/86825b7e-8f8a-43e3-b5a5-58c315062bb8)

   Benchmark type 3 : **STMV**

   Here nstlist=400; ntomp=8; cd /benchmarks/stmv; tar -xvf stmv.tar.gz; was uncommented.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/27378131-740c-4351-97d7-d39e31deddcd)

7. Here the run time is selected as **'1 hour'** with telemetry enabled. The number of **GPU's** are selected as **'8'**.

    Click on **'Next'** button available on the top right corner.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/bcd11877-7409-40f9-84f6-18e937eae28b)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/ef020fb3-c314-40ee-8bfe-3497e6df4afc)

8. Select the cluster and desired queue to run the job. In this case **1CN128C8G2H_2IB_MI210_SLES15 (Pre-emptible)** was 
   selected. Click on **'Next'** button available on the top right corner.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/2b6e04b2-3328-4d00-8848-8f19ff1be57a)

9. Review all the configurations selected and click on **'Run Workload'**.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/3950c8d3-6ff4-41a0-863c-066d2f5c8d01)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/ecab61af-b816-4ed4-8d2b-74dcd43d8635)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/8171a7ac-8bd0-46d7-9296-65802d410f55)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/c084e5b0-bc25-482c-87b3-09eea4eeb451)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/ff8bb2db-4b5f-4f7f-87dc-cb58aa2755be)

    **Note**: Please note that the payment information might be different from the above image because you might be added 
   to a different team.

10.  Once the application execution is successful then the status gets changed into **“Completed”**. The user can check the 
    **STDOUT** and **STDERR** logs by clicking on respective tabs. The Performace tab shows the telemetry collected.
    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/eea60fef-c8f2-4d68-befb-b1c306baf004)

11.  The performace value in the **STDERR** tab is the performance of Gromacs docker application.
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/99aa2189-5f70-4196-a1e2-5e90a251800f)
