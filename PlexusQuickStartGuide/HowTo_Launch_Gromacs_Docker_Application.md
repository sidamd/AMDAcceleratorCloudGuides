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

6. Click **'Next'** to continue with default script.

   **Note**: Uncomment the type of benchmark that needs to be run.

   Here nstlist=180; ntomp=16; cd /benchmarks/adh_dodec; tar -xvf adh_dodec.tar.gz; was uncommented.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/470d1134-22ed-48d9-8cfc-3b628f47c8dc)

7. Here the run time is selected as **'1 hour'** with telemetry enabled. The number of **GPU's** are selected as **'8'**.

    Click on **'Next'** button available on the top right corner.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/bcd11877-7409-40f9-84f6-18e937eae28b)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/ef020fb3-c314-40ee-8bfe-3497e6df4afc)

8. Select the cluster and desired queue to run the job. In this case **1CN128C8G2H_2IB_MI210_SLES15 (Pre-emptible)** was selected. Click on **'Next'** button available on the top right corner.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/2b6e04b2-3328-4d00-8848-8f19ff1be57a)

9. Review all the configurations selected and click on **'Run Workload'**.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/2bb9ba4c-338f-470f-9a13-046ccdba490f)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/6792df60-55d3-499c-9fa8-a89c4a65f23f)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/dc4c3610-ad74-456d-bde1-ca5b7391eaf8)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/7c5b07d9-08d8-4129-a189-10177f624f2b)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/71eb276a-ff88-4a6a-bf15-b1ca3d4920bb)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/4150f290-6b00-4562-b6a6-857d28d7aacc)

    **Note**: Please note that the payment information might be different from the above image because you might be added to a different team.

10.  Once the application execution is successful then the status gets changed into **“Completed”**. The user can check the **STDOUT** and **STDERR** logs by clicking on respective tabs. The Performace tab shows the telemetry collected.
    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/eea60fef-c8f2-4d68-befb-b1c306baf004)

11.  The performace value in the **STDERR** tab is the performance of Gromacs docker application.
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/99aa2189-5f70-4196-a1e2-5e90a251800f)
