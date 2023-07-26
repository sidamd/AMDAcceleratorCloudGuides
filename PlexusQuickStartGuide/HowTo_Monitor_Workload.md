***
# How to Understand and Monitor Workload
***

## **Workload Status and Details**
After submitting a workload, Workload Status and details of workload can be seen in **Workloads** page.

   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/8ff78b1e-027e-46a7-9166-b9a5a7056e40)

**Different types of Workload Status**<br/>  

Each workload goes through several different states after it is submitted 
* **Created** – The workload has been created in the system
* **Sent** – The workload has been sent to the queue that user selected in the workload submission process
* **Pending** – The workload is in a waiting state in the queue
* **Running** – The workload has started running in the selected queue
* **Completed** – The workload has successfully finished processing
* **Failed** – A problem has occurred which has prevented the workload from completing successfully
* **Cancelled** – The workload has been canceled by the user and stopped running
* **Finished** - The interactive job that has been finished by user.

## **Workload Overview Page**

Workload Overview page has the following tabs.
1. **Overview tab**  
   * The details in overview tab can be viewed while the workload is running.
   * It has details like the node on which the workload is running, real time cpu utilization, memory etc.
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/3fed5764-adb1-41c7-8cd3-b3c6487ff77c)
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/842e4eea-3666-4d56-b516-328a964bd559)
   * Once the workload completes, Overview tab will be disabled.
    
2. **Parameters tab**
   * This tab has the details entered while submitting the workload like application launched, queue selected, app configuration, number of GPUs, CPUs, memory etc.
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/da856773-47c6-4af2-afb2-bbde93e54c37)
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/e4ba9d23-58e7-438b-a541-9f191a802c3c)
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/a6bdb4f6-220c-4e6f-badc-7288e2041afe)
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/b1f08736-4ba9-429a-b94b-79d7fb13d468)
     
3. **SYSLOG tab**
    * The system logs can be seen in SYSLOG tab while workload is running.
    * Once workload finishes, syslog can be downloaded by clicking 'Show historical logs' button.
      ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/fe86eef0-e24b-4777-a6a1-ff576fdb4b82)
      
4. **STDOUT tab**
    * The output logs can be seen in STDOUT tab while workload is running.
    * Once workload finishes, stdout log can be downloaded by clicking 'Download logs' button.
      ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/66b13e07-108f-4c3c-83ed-49bd815e9167)
      
5. **STDERR tab**
    * The error logs can be seen in STDERR tab while workload is running.
    * Once workload finishes, stderr log can be downloaded by clicking 'Download logs' button.
      ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/4306f322-31ca-42a3-800d-c06ca60f453a)
      
6. **Performance tab**
    * Performance tab shows the telemetry
      ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/9a145a6d-ae41-41a6-98aa-40d3b7e0d785)
      ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/0e41cd29-a453-4021-9a0d-357b914c7a46)
