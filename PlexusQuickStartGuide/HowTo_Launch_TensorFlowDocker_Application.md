***

# How To Launch TensorFlow Docker Application

***

 **1.** Login to **https://aac.amd.com/.**
 
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/d62dc96e-e37a-42b3-9b0e-72445014a621)

 **2.** Click on Applications. Select **TensorFlow**
 
  ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/9c48d338-041a-46dc-8b49-f5bcd21629b1)
 

 3. In the **'Select An Application'** pop-up, select the desired TensorFlow version with container type as **docker**
    
   **Note**: In this case, we have selected **TensorFlow 2-10 ROCm 5-4-1** version and container as docker.
   
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/385bf611-e83e-497c-a6ff-a5b8a2fa6fd9)


 4. Click on **'New Workload'** button available on the top right corner.

  ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/37097a0d-2ac4-411f-8ff2-78c1f3cee08c)


 5. Click **Next** button to continue.

   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/84db90fe-9aac-43b8-85a3-4fb5961772df)

  
  6. In **Select Resources** page, specify the number of GPU's (e.g., 1 GPU) and max allowed runtime required for the workload. Click **Next** button.

  **Note:** The maximum number of GPUs should be 8.

  ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/793c2faf-9bcf-4502-a138-3e6281947300)


  7. Select the cluster and desired queue to run the job. In this case **1CN128C8G2H_2IB_MI210_SLES15 (Pre-emptible) - AAC Plano**  is selected. Click on **Next**

   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/96d3855e-1640-4820-b1f7-7dc5ea0dd9e8)


  8. Review all the configurations selected and click on **Run Workload** 

   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/240a4062-b530-4073-ab5a-2a8ea8cd01f1)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/9a75ccd5-2174-45f9-9663-e49cc704a3d2)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/8fb01621-d710-4b37-baa1-acb384a6deb5)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/87f96aee-0f11-48ca-8332-fa70d227f535)


   9. Once the workload is submitted, the workload status changes to **Running** when queue is available. Click on the running workload

  ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/4d19e6d9-1505-427d-b242-5f454ffeca5f)


   10. User can see the system logs in **SYSLOG**, output in **STDOUT** and errors in **STDERR** tabs.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/45fafbcf-0078-40e2-b6fe-f7cea81e111a)


   11. A token will be generated in **STDOUT** tab in yellow color as shown below. Copy the token.
    ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/e7595b72-def4-49a8-a1a6-2e02dedd9399)


   12. Once the interactive endpoints are enabled, click **'Connect'** to launch ML Studio(Jupyter lab).

   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/cac47a19-d778-47c2-953c-df444beef3d5)

   13.Jupyter lab opens. Paste the token in **'Password or token'** field. Click login.

   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/08e56d2c-83a8-4725-b092-ee96a16a391a)

   14. User can see Jupyter lab, which can be used for python based development work.

   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/bc1829da-8b48-42cb-9345-48474f95cbd4)

   15. Click on **Terminal** to open it.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/d53c6f3f-43bf-4b64-84dd-186acab33b8f)

   16. In terminal, enter the following benchmark:
   Benchmark - python3 /root/benchmarks/scripts/tf_cnn_benchmarks/tf_cnn_benchmarks.py --model=resnet50 --num_gpus=8 --batch_size=256 --num_batches=100 -- 
   print_training_accuracy=True --variable_update=parameter_server --local_parameter_device=gpu
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/a0504d7f-5b76-4b0b-9d7e-0660d53947b0)

   17. Collect **Performance Metrics**
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/156ee07e-e098-4098-9bcb-d930642e18ea)

   18. Once the work is done with Jupyter lab, Close it. 
   
   19. Click **'Finish Workload'** button.
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/34bd1134-4034-4a51-bf22-2981ecffc435)


   20. Logs can be downloaded from STDOUT tab by clicking **'Download Logs'** once workload is finished.
  ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/81fc7152-687b-4b38-9d3c-114718c1c419)
