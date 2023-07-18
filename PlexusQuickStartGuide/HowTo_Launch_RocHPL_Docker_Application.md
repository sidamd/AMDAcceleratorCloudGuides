***

# How To Launch RocHPL Docker Application

***

 1. Login to https://aac.amd.com/ and click on Applications. Here select RocHPL.

![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/naimisha/PlexusQuickStartGuide/assets/selected_hpl.PNG)

 2. Select the version as RocHPL_5_0_5_49 with desired container type as docker/singularity.
Note: In this case, container type was selected as docker.

![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/naimisha/PlexusQuickStartGuide/assets/rocHPL_Versions.PNG)

 3. Click on New Workload on the right top.

![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/naimisha/PlexusQuickStartGuide/assets/newWorkload_rocHPL.PNG)

 4. Select input files if any and then click on Next

![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/naimisha/PlexusQuickStartGuide/assets/inputFiles_rocHPL.PNG)

 5.If any changes are required then modify the run script, else continue with default and click on Next.

![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/naimisha/PlexusQuickStartGuide/assets/rocHPL_defaultScript.PNG)

6.Select the allowed run time and the number of GPU’s required, here select the run time as 1 hour and the number of GPU’s as 8 .Here Telemetry was enabled, click on Next.

![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/naimisha/PlexusQuickStartGuide/assets/gpusSelect_rocHPL.PNG)


7.Select the queue required, In this case 1CN128C8G2H_2IB_MI210_SLES15 (Pre-emptible) was selected. Click on Next.

![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/naimisha/PlexusQuickStartGuide/assets/queueSelection.PNG)

8.Review all the configurations selected and click on Run Workload.

![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/naimisha/PlexusQuickStartGuide/assets/reviewAppConfig.PNG)

9.Once the application execution is successful then the status gets changed into “Completed”.
The user can check the STDOUT and STDERR logs by clicking on them.
The performance can also be viewed if the telemetry option was enabled.

![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/naimisha/PlexusQuickStartGuide/assets/rocHPL_parameters.PNG)

10.The final score and the status can be checked at the bottom of the STDOUT.

![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/naimisha/PlexusQuickStartGuide/assets/rocHPL_stdout.PNG)
