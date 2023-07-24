***

# How To Check Metrics with Telemetry (enabled/disabled)

***
1. Login to **https://aac.amd.com/**.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/d62dc96e-e37a-42b3-9b0e-72445014a621)
   
2. Search for the required application, here HPL was selected.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/c38b250f-24bd-4a15-8f65-2cca6aeb5bc9)

3. Select the desired RocHPL version with desired container type as **docker**.
   **Note**: In this case, RocHPL_5_0_5_49 version was selected with container type as docker.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/060103a0-9be8-4569-9b2c-c60fae091fb5)

4. Click on **'New Workload'** button available on the top right corner.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/ace07a67-c914-41a7-b69e-b7aa83eee7a8)
   
5. Click **'Next'** button available on the top right corner.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/b090385d-1af1-4790-a1f3-19a34512f29a)

6. Click Next to continue with default script.

    Note: Default script is for **8 GPU's**.
    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/729722c4-39fa-4217-93ed-24e5dd27eefe)

7. Here the run time is selected as '1 hour' with telemetry enabled. The number of GPU's are selected as '8'.

   Click on 'Next' button available on the top right corner.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/fa82475d-8460-43d3-aa9a-8abfe786e4e0)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/959d6b49-dfc3-41eb-96d8-f39846ae32f0)

8. Select the cluster and desired queue to run the job. **In this case 1CN128C8G2H_2IB_MI210_SLES15 (Pre-emptible)** was 
   selected. Click on 'Next' button available on the top right corner.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/63f7f363-2436-4e68-9ddd-4e60f7e8568d)

9. Review all the configurations selected and click on **'Run Workload'**.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/393f2e0f-1304-4a4e-8985-94beadf35bb7)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/33d76934-ba39-493a-8781-d55f31eaaf31)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/c87f6872-5c3c-4ce1-9122-e4f041c3b173)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/c441b72b-e9b5-4229-8855-607386dcda9b)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/65addce6-2433-495e-aab1-6aa788a0a3a3)

   **Note**: Please note that the payment information might be different from the above image because you might be added 
   to a different team.

10. Once the application execution is successful then the status gets changed into **“Completed”**. The user can check the 
    **STDOUT** and **STDERR** logs by clicking on respective tabs. The Performace tab shows the telemetry collected.
    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/b8eba2d2-e619-41e2-8370-e2e0f90ab588)

11.  The performace value in the **STDOUT** tab is the performance of RocHPL docker application.
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/17798bfd-b78f-47b8-b966-e59f2b3d9a6b)

12. Since the **telemetry** was **enabled** in the Step 7 here the user can see the **performace tab**.
    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/1f06e979-ef78-4e8f-8d95-aee2583c0f36)
    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/21d4629a-bef8-46b2-a4f2-c38da821a783)

13. If the **telemetry** is **disabled**, then the performance tab does not appear after the workload launch is successful.
    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/2ba807f7-cc1a-4edc-9c7d-6175e8d6af20)

14. The same RocHPL was re-ran after **disabling** the **telemetry**. Here the performace tab is not visible.
    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475004/713ecad9-6796-40db-97be-72ef225a711b)
