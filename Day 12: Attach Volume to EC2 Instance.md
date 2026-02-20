Question:
The Nautilus DevOps team has been creating a couple of services on AWS cloud. They have been breaking down the migration into smaller tasks, allowing for better control, risk mitigation, and optimization of resources throughout the migration process. Recently they came up with requirements mentioned below.

An instance named nautilus-ec2 and a volume named nautilus-volume already exists in us-east-1 region. Attach the nautilus-volume volume to the nautilus-ec2 instance, make sure to set the device name to /dev/sdb while attaching the volume.

## ✅ Attach `nautilus-volume` to `nautilus-ec2` (Console Steps – No Coding)

Service Used: **Amazon Web Services**

Region: **us-east-1**

---

### 🔹 Step 1: Login to AWS Console

1. Open AWS Console.
2. Select region → **us-east-1** (top right corner).

---

### 🔹 Step 2: Verify EC2 Instance

1. Go to **EC2 Dashboard**.
2. Click **Instances**.
3. Confirm instance named **nautilus-ec2** is available.
4. Note its **Availability Zone** (very important).

---

### 🔹 Step 3: Verify EBS Volume

1. In EC2 Dashboard → Click **Volumes** (under Elastic Block Store).
2. Find volume named **nautilus-volume**.
3. Ensure:

   * State = **Available**
   * Availability Zone = Same as `nautilus-ec2`

⚠️ If AZ is different, attachment is not possible.

---

### 🔹 Step 4: Attach the Volume

1. Select **nautilus-volume**.
2. Click **Actions** → **Attach volume**.
3. In the popup:

   * Choose Instance → **nautilus-ec2**
   * Device name → enter:

     ```
     /dev/sdb
     ```
4. Click **Attach volume**.

---

### 🔹 Step 5: Verify Attachment

1. Refresh the volume page.
2. Status should change to:

   * **In-use**
3. Under “Attached instances” you should see:

   * Instance ID of `nautilus-ec2`
   * Device: `/dev/sdb`

---

# 🔥 Important Interview Points

### 1️⃣ Can we attach a volume to any instance?

No. Volume and instance must be in the **same Availability Zone**.

---

### 2️⃣ What happens after attachment?

The volume becomes a block storage device for the EC2 instance.

---

### 3️⃣ Can one EBS volume be attached to multiple instances?

Normally ❌ No.
Except when using **Multi-Attach** (only supported for specific volume types like io1/io2).

---

### 4️⃣ Can we detach while instance is running?

Yes, but it should be unmounted properly inside OS to avoid data corruption.

## 🔥 Interview Questions – EBS Volume Attached to EC2 Project

Project Context: Attached **`nautilus-volume` (EBS)** to **`nautilus-ec2` (EC2 Instance)** in **us-east-1** using **Amazon Web Services**

---




# 🟢 Basic Interview Questions

### 1️⃣ What is EBS?

**Amazon Elastic Block Store** is block-level storage used with EC2 instances.

---

### 2️⃣ What are the prerequisites before attaching a volume?

* Same **Availability Zone**
* Volume state must be **Available**
* Instance must exist (running or stopped)

---

### 3️⃣ What happens if AZ is different?

Attachment will fail.
EBS volumes are **AZ-specific**.

---

### 4️⃣ What is the purpose of `/dev/sdb`?

It is the device name used by the OS to identify the attached disk.

---

### 5️⃣ What happens after attaching volume?

* Status changes to **In-use**
* It appears as a new block device inside the EC2 OS

---

# 🟡 Intermediate Interview Questions

### 6️⃣ Difference between EBS and Instance Store?

| EBS                 | Instance Store         |
| ------------------- | ---------------------- |
| Persistent          | Temporary              |
| Network attached    | Physically attached    |
| Can detach/reattach | Lost on stop/terminate |

---

### 7️⃣ Can we attach one volume to multiple instances?

Only with **Multi-Attach** (supported for io1/io2 volumes).

---

### 8️⃣ What are different EBS volume types?

* gp2 / gp3 (General Purpose SSD)
* io1 / io2 (Provisioned IOPS SSD)
* st1 (Throughput optimized HDD)
* sc1 (Cold HDD)

---

### 9️⃣ How do you increase volume size?

Modify volume → Increase size → Extend filesystem inside OS.

---

### 🔟 What happens if you detach volume without unmounting?

Possible **data corruption**.

---

# 🔴 Advanced / Scenario-Based Questions

### 1️⃣ Your volume is attached but not visible inside OS. Why?

* Need to rescan
* NVMe mapping difference
* Incorrect device name assumption

---

### 2️⃣ Production server disk is full. What will you do?

* Create snapshot
* Increase volume size
* Extend filesystem
* No downtime if properly done

---

### 3️⃣ How does EBS achieve durability?

* Replicated automatically within the same AZ
* Designed for 99.999% availability

---

### 4️⃣ What is EBS Snapshot?

* Incremental backup
* Stored in S3 internally

---

### 5️⃣ How do you migrate volume to another AZ?

* Create Snapshot
* Create new volume in target AZ
* Attach to instance

---

### 6️⃣ What is IOPS and why important?

IOPS = Input/Output Operations Per Second
Critical for database workloads.

---

# 🏗 Real-Time Project-Based Questions

### ✅ How would you design storage for:

* Database server → Use io2
* Web server logs → gp3
* Backup storage → sc1

---

### ✅ How do you secure EBS volume?

* Enable encryption (KMS)
* IAM policies
* Restrict attachment permissions

---

### ✅ What monitoring would you configure?

Use:

* **Amazon CloudWatch**

  * Monitor IOPS
  * Throughput
  * Burst balance

---

# 🎯 Direct Interview Summary Answer

> “In this project, I attached an existing EBS volume to an EC2 instance ensuring both were in the same Availability Zone. I verified volume state, attached it with a specific device name, and validated the attachment. I understand volume types, performance tuning, snapshots, and production-level storage best practices.”

Instances:
<img width="1919" height="808" alt="Screenshot 2026-02-20 145524" src="https://github.com/user-attachments/assets/c4eba3fa-17ff-4503-a06c-cadeb769dbdb" />
------------------------------------------------------------------------------------------------------------------------------------------------------------------
Volumes:
<img width="1903" height="802" alt="Screenshot 2026-02-20 145540" src="https://github.com/user-attachments/assets/773e557e-51e8-42af-9763-e02ca70448d9" />
-----------------------------------------------------------------------------------------------------------------------------------------------------------------
Attached Volumes:
<img width="1919" height="806" alt="Screenshot 2026-02-20 145509" src="https://github.com/user-attachments/assets/b39b8aea-311d-44ec-9b30-3e6936be61e0" />
-----------------------------------------------------------------------------------------------------------------------------------------------------------------
complaction :
<img width="1864" height="911" alt="Screenshot 2026-02-20 145606" src="https://github.com/user-attachments/assets/de7e3a72-c796-46db-b6b4-2baf479d37b3" />






