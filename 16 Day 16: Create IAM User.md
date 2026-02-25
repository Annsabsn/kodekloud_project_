# 🔐 AWS IAM – Create User **iamuser_mariyam**

## 📌 What is IAM?

![Image](https://d2908q01vomqb2.cloudfront.net/22d200f8670dbdb3e253a90eee5098477c95c23d/2022/06/09/Console-homepage-5.png)

![Image](https://d2908q01vomqb2.cloudfront.net/22d200f8670dbdb3e253a90eee5098477c95c23d/2016/11/02/RMoncur1Phase0.png)

![Image](https://miro.medium.com/0%2A2qvQJOBLk8HEDQNd)

![Image](https://www.hava.io/hs-fs/hubfs/IAM_Policy_JSON.png?name=IAM_Policy_JSON.png\&width=1452)

**IAM (Identity and Access Management)** is a global AWS service that helps you:

* Create **users**
* Create **groups**
* Assign **roles**
* Attach **policies**
* Control who can access what in AWS

It is the **first service configured** when setting up AWS infrastructure.

---

# 🛠 Task: Create IAM User – `iamuser_mariyam`

---

## ✅ Step-by-Step with Explanation (AWS Console)

### 🔹 Step 1: Login to AWS Console

* Open AWS Management Console.
* Search for **IAM**.
* Click on **IAM service**.

👉 IAM is a **global service** (not region-specific).

---

### 🔹 Step 2: Go to Users

* In the left panel → Click **Users**
* Click **Create user**

👉 IAM users represent **individual people or applications**.

---

### 🔹 Step 3: Enter User Details

* User name:

  ```
  iamuser_mariyam
  ```

* Select access type:

  * ✅ **Management Console access** → If user needs login access
  * ✅ **Programmatic access** → If user needs CLI/API access

👉 Choose based on requirement.

Click **Next**.

---

### 🔹 Step 4: Set Permissions

You have 3 options:

1. Add user to group (Recommended)
2. Attach policies directly
3. Copy permissions from existing user

👉 Best practice: **Assign permissions using Groups**.

(For this task, if not mentioned, skip permissions.)

Click **Next**.

---

### 🔹 Step 5: Review and Create

* Verify username
* Click **Create user**

---

## ✅ Verification

Go to:
IAM → Users → Confirm `iamuser_mariyam` is listed.

✔ Task Completed.

---

# 🎯 Important Interview Questions (Basic)

### 1️⃣ What is IAM?

IAM is a service that controls authentication and authorization in AWS.

---

### 2️⃣ Is IAM regional or global?

IAM is **global**.

---

### 3️⃣ Difference between IAM User and IAM Role?

| IAM User                  | IAM Role                   |
| ------------------------- | -------------------------- |
| Permanent identity        | Temporary identity         |
| Used by people            | Used by services           |
| Has long-term credentials | Uses temporary credentials |

---

### 4️⃣ What is IAM Policy?

A JSON document that defines **Allow or Deny permissions**.

---

### 5️⃣ What is the principle of least privilege?

Giving only the minimum permissions required to perform a task.

---

# 🚀 Advanced Interview Questions

### 1️⃣ Explain IAM Policy Evaluation Logic

AWS evaluates:

* Explicit Deny → Highest priority
* Allow
* Default Deny

👉 Explicit Deny always wins.

---

### 2️⃣ What is the difference between Inline and Managed Policy?

| Inline Policy             | Managed Policy               |
| ------------------------- | ---------------------------- |
| Attached to single user   | Can attach to multiple users |
| Deleted when user deleted | Separate reusable policy     |

---

### 3️⃣ What are IAM Roles used for in DevOps?

* EC2 access to S3
* Lambda access to DynamoDB
* Cross-account access
* Temporary credentials

---

### 4️⃣ How to secure IAM users?

* Enable MFA
* Rotate access keys
* Use strong password policy
* Avoid root user usage
* Use IAM roles instead of access keys

---

### 5️⃣ What is STS?

Security Token Service provides **temporary credentials**.

---

### 6️⃣ How do you give cross-account access?

Using:

* IAM Role
* Trust relationship policy

---

# 🔥 Real DevOps Scenario Question

👉 If an EC2 instance needs access to S3, will you create IAM user or role?

✔ Correct Answer: **IAM Role**

Because roles provide temporary credentials and are more secure.

Complection:
<img width="1879" height="906" alt="Screenshot 2026-02-25 213051" src="https://github.com/user-attachments/assets/62997175-9932-4531-9bac-955da438b030" />

