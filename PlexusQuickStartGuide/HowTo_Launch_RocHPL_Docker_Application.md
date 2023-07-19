***

# How To Launch RocHPL Docker Application

***

 1. Login to https://aac.amd.com/ and click on Applications. Select HPL.
    
    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/c38b250f-24bd-4a15-8f65-2cca6aeb5bc9)
    
 2. Select the desired RocHPL version with desired container type as docker/singularity.
    
    **Note**: In this case, we have selected RocHPL_5_0_5_49 version and container as docker.
    
    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/060103a0-9be8-4569-9b2c-c60fae091fb5)
    
 3. Click on 'New Workload' button available on the top right corner.
    
    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/ace07a67-c914-41a7-b69e-b7aa83eee7a8)

 4. Select input files if any and then click on Next

    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/9614e3fe-88b7-4914-9c08-595a775b9884)

 5. If any changes are required then modify the run script, else continue with default script and click on Next.

    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/5f151625-c7f8-4403-8626-adc4a87783ef)

 6. Select the allowed run time and the number of GPU’s required. Here, we have selected the run time as 1 hour, number of GPU’s as 8 and telemetry is enabled, click       on Next.

    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/c0b45582-c5ac-4b8f-88b9-ab234afba7af)

 7. Select the desired queue, In this case 1CN96C8G1H_4IB_MI250_Ubuntu22 was selected. Click on Next.

    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/07da4355-899b-4270-a992-17a6ece9f090)

 8. Review all the configurations selected and click on Run Workload.
    
    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/3ebc4951-3b8c-4354-be88-b4ea9c31b7ab)
    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/61295ad1-eb33-471d-884e-22b43d11c8ff)
    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/0f9484e1-239f-4d2c-b037-5b43704d9c02)
    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/fa0bd624-d914-4463-b594-6f8270fbef05)
    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/1ca97119-fa09-4a4a-a7fb-9e3cbc114ae0)

 9. Once the application execution is successful then the status gets changed into “Completed”.
     
    The user can check the STDOUT and STDERR logs by clicking on them.

    The performance can also be viewed if the telemetry option was enabled.

    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/680e1ada-fe12-4b78-82e3-9f8a2c692ff0)

 10. The final score and the status can be checked at the bottom of the STDOUT.

     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/c0b325e0-4707-40ed-8825-d8b7c67976df)
