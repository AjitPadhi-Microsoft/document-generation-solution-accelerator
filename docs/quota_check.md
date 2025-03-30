## Check Quota Availability Before Deployment

Before deploying the accelerator, **ensure sufficient quota availability** for the required model.  \

## 📌 Default Models & Capacities:
```
gpt-4o:30, text-embedding-ada-002:80, gpt-4:30
```
## 📌 Default Regions:
```
eastus, uksouth, eastus2, northcentralus, swedencentral, westus, westus2, southcentralus, canadacentral
```
## Usage Scenarios:
- No parameters passed → Default models and capacities will be checked in default regions.
- Only model(s) provided → The script will check for those models in the default regions.
- Only region(s) provided → The script will check default models in the specified regions.
- Both models and regions provided → The script will check those models in the specified regions.
  
## **Input Formats**
✔️ Run without parameters to check default models & regions:
   ```
  ./quota_check_params.sh
   ```
✔️ Model name and required capacity in the format:
  ```
  ./quota_check_params.sh gpt-4o:30
  ```
✔️ Multiple models can be passed, separated by commas:
  ```
  ./quota_check_params.sh gpt-4o:30,text-embedding-ada-002:80
  ```
✔️ Specify region(s) (comma-separated):  
  ```
  ./quota_check_params.sh gpt-4o:30 eastus,westus2
  ```
✔️ Check default models in specific regions:
  ```
  ./quota_check_params.sh "" eastus,westus2
  ```

#### **Sample Output**
The final table lists regions with available quota. You can select any of these regions for deployment.

![quota-check-ouput](images/quota-check-output.png)

---
## **If using Azure Portal and Cloud Shell**

1. Navigate to the [Azure Portal](https://portal.azure.com).
2. Click on **Azure Cloud Shell** in the top right navigation menu.
3. Run the appropriate command based on your requirement:  

   **To check quota for a specific model and capacity:**  

    ```sh
    curl -L -o quota_check_params.sh "https://raw.githubusercontent.com/microsoft/document-generation-solution-accelerator/main/scripts/quota_check_params.sh"
    chmod +x quota_check_params.sh
    ./quota_check_params.sh <model_name:capacity> [<model_region>] (e.g., gpt-4o-mini:30,text-embedding-ada-002:20 eastus)
    ```

   **To check available quota across all regions for supported models:**  

    ```sh
    curl -L -o quota_check_all_regions.sh "https://raw.githubusercontent.com/microsoft/document-generation-solution-accelerator/main/scripts/quota_check_all_regions.sh"
    chmod +x quota_check_all_regions.sh
    ./quota_check_all_regions.sh
    ```
    
## **If using VS Code or Codespaces**
1. Open the terminal in VS Code or Codespaces.  
2. Navigate to the `scripts` folder where the script files are located:
   ```sh
    cd scripts
    ```
3. Run the appropriate script based on your requirement:  

   **To check quota for a specific model and capacity:**  

    ```sh
    ./quota_check_params.sh <model_name:capacity> [<model_region>] (e.g., gpt-4o-mini:30,text-embedding-ada-002:20 eastus)
    ```

   **To check available quota across all regions for supported models:**  

    ```sh
    ./quota_check_all_regions.sh
    ```
4. If you see the error `_bash: az: command not found_`, install Azure CLI:  

    ```sh
    curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash
    az login
    ```
5. Rerun the script after installing Azure CLI.
