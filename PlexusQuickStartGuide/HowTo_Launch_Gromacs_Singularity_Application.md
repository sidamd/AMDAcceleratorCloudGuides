***

# How To Launch Gromacs Singularity Applications.

***
1. Login to **https://aac.amd.com/**.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/5ff0f361-8d9b-42ae-afc8-9c222b56bc63)

2. Click on Applications. Search for **Gromacs**.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/4e804fad-bd92-4fea-a186-a54cc9b8c1fd)

3. Select the desired Gromacs version with desired container type as **singularity**.

   **Note**: In this case, Gromacs 2022_3 version was seletced with container type as singularity.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/b77f64a1-6641-4a10-9829-090d223f1602)

4. Click on **'New Workload'** button available on the top right corner.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/84d85f53-80d7-48c6-a9ad-3743cbbf8ac8)

5. Click **'Next'** button available on the top right corner.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/2e1c452c-9e86-4723-b394-f9cc89fe9b26)

6. Choose the desired **benchmark** type

   **Note**: Uncomment the type of benchmark that needs to be run. Only "ONE" benchmark can be launched at a time. If more 
   than one benchmark, say Adh_Dodec and Cellulose, is uncommented and launched, then the application fails.

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
    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/d201159a-4298-4ba6-b118-9c04eb7c4f92)
    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/05a7bc0d-ecf2-4541-ac38-2ebb162be9a4)

8. Select the cluster and desired queue to run the job. In this case **1CN128C8G2H_2IB_MI210_RHEL8 (Pre-emptible)** was 
   selected. Click on **'Next'** button available on the top right corner.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/2c5d4b9d-d0b2-456b-b4f1-93c88f2d9dc0)

9. Review all the configurations selected and click on **'Run Workload'**.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/a81f1d26-ae41-4adb-9d31-d46ced6f228e)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/9a8df735-bb44-4a21-8566-57e60f63b6dc)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/f0d32676-61cd-49a1-8dca-743e08af14ed)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/b3d98c0a-5673-4f15-a41f-73fae6f830e0)

   **Note**: Please note that the payment information might be different from the above image because you might be added 
   to a different team.

10.  Once the application execution is successful then the status gets changed into **“Completed”**. The user can check the 
     **STDOUT** and **STDERR** logs by clicking on respective tabs. The Performace tab shows the telemetry collected.
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/6c267b20-dd8c-4e05-831d-dabdc1b729e4)

11.  The performace value in the **STDERR** tab is the performance of Gromacs singularity application.
      ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/4c73c929-8f36-4d10-8df4-9f696c2d4e88)
