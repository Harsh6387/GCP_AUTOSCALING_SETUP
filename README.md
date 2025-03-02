# **Google Cloud Platform (GCP) Auto-Scaling and Security Configuration**

## **Overview**
This project demonstrates how to set up a **Managed Instance Group (MIG)** with **auto-scaling** in **Google Cloud Platform (GCP)**. It also covers **firewall configurations** and **IAM role assignments** for restricted access.

## **1. Instance Creation Steps**

### **Step 1: Create a Virtual Machine (VM) Instance**
1. Go to **Google Cloud Console** and create a new project.
2. Within the project, navigate to **Compute Engine > VM Instances**.
3. Click **Create Instance** and configure:
   - **Machine type**
   - **Region**
   - **Firewall policies**
   - **Disk size and OS image**
4. Click **Create** to launch the VM instance.

---

## **2. Setting Up Auto-Scaling with Managed Instance Groups (MIG)**

### **Step 1: Create a Managed Instance Group**
1. Navigate to **Compute Engine > Instance Groups**.
2. Click **Create Instance Group**.
3. Choose an existing **instance template** or create a new one.
4. Configure the **Firewall policies** and select the **machine type**.
5. Set the **minimum and maximum instances**:
   - **Min:** 1
   - **Max:** 5
6. Click **Create**.

### **Step 2: Configure Auto-Scaling**
1. Click on the created **Instance Group**.
2. Go to the **Autoscaling tab**.
3. Enable **Autoscaling** and set:
   - **Metric:** CPU Utilization
   - **Target CPU Utilization:** 60%
4. Click **Save**.

---

## **3. Configuring Firewall Rules**

1. Navigate to **VPC Network > Firewall**.
2. Click **Create Firewall Rule**.
3. Configure the rule:
   - **Name:** Allow HTTP/SSH Traffic
   - **Target:** All instances in the network
   - **Allowed Traffic:**
     - HTTP (Port 80)
     - SSH (Port 22)
4. Click **Create**.

---

## **4. Assigning IAM Roles for Restricted Access**

1. Navigate to **IAM & Admin > IAM**.
2. Click **Add** to assign a role.
3. Enter the **user email**.
4. Select **Role: Viewer** (Restricts editing capabilities).
5. Click **Save**.

---

## **5. Testing Auto-Scaling**

### **Step 1: Open SSH and Run the Stress Command**
1. Open **Compute Engine > VM Instances**.
2. Click **SSH** to open the terminal.
3. Run the following command to increase CPU usage:
   ```bash
   sudo apt update && sudo apt install stress -y
   stress --cpu 4 --timeout 300
   ```
4. Monitor the instance count under **Compute Engine > Instance Groups**.

---

## **6. Architecture Diagram**
This setup includes:
- **Managed Instance Group** with auto-scaling (1-5 instances)
- **Firewall rules** for security
- **IAM policies** for restricted access
- **Auto-scaling based on CPU load**



---

## **7. Conclusion**
- **Efficient resource utilization** through auto-scaling.
- **Secure access control** using IAM policies.
- **Controlled network traffic** via firewall rules.

---

## **8. Additional Notes**
- To monitor scaling activity, check **Operations > Logging** in GCP.
- Modify CPU utilization settings to fine-tune auto-scaling.

