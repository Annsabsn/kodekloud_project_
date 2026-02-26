Question:
The Nautilus DevOps team has been creating a couple of services on AWS cloud. They have been breaking down the migration into smaller tasks, allowing for better control, risk mitigation, and optimization of resources throughout the migration process. Recently they came up with requirements mentioned below.

Create an IAM group named iamgroup_mariyam.

Answer:
## ✅ Task: Create IAM Group `iamgroup_mariyam`

Service Used:

* Amazon Web Services
* AWS Identity and Access Management

---

# 🔹 Steps to Create IAM Group (Console)

1. Login to AWS Console
2. Search **IAM** → Open IAM Dashboard
3. Click **User groups** (left panel)
4. Click **Create group**
5. Enter Group name:

   ```
   iamgroup_mariyam
   ```
6. Attach policies (optional as per requirement)
7. Click **Create group**

✅ Group created successfully.

---

# 🔹 AWS CLI Command (Interview Important)

```bash
aws iam create-group --group-name iamgroup_mariyam
```

Verify:

```bash
aws iam get-group --group-name iamgroup_mariyam
```

---

# 🎯 Interview Questions with Answers (Direct)

### 1️⃣ What is IAM?

IAM is a service in AWS that helps manage users, groups, roles, and permissions securely.

---

### 2️⃣ What is an IAM Group?

An IAM Group is a collection of IAM users. Permissions are attached to the group, and all users in that group inherit those permissions.

---

### 3️⃣ Difference between IAM User and IAM Group?

| IAM User                               | IAM Group                                    |
| -------------------------------------- | -------------------------------------------- |
| Individual identity                    | Collection of users                          |
| Has login credentials                  | Cannot login                                 |
| Gets permissions directly or via group | Used to assign permissions to multiple users |

---

### 4️⃣ Can a user belong to multiple groups?

✅ Yes, a user can belong to multiple IAM groups.

---

### 5️⃣ What is an IAM Policy?

A JSON document that defines permissions (Allow or Deny actions on AWS resources).

---

### 6️⃣ What are Managed Policies vs Inline Policies?

* **Managed Policy:** Reusable policy attached to multiple users/groups/roles.
* **Inline Policy:** Directly attached to one user/group/role (not reusable).

---

### 7️⃣ Is IAM Global or Regional?

✅ IAM is a **Global Service**.

---

# 🚀 Advanced Interview Questions with Answers

### 1️⃣ How does IAM evaluate policies?

Order:

1. Explicit Deny
2. Explicit Allow
3. Default Deny

Explicit Deny always overrides Allow.

---

### 2️⃣ Difference between IAM Role and IAM Group?

| IAM Role                    | IAM Group                       |
| --------------------------- | ------------------------------- |
| Assumed temporarily         | Contains users                  |
| Used by services/EC2/Lambda | Used to manage user permissions |
| No long-term credentials    | Cannot be assumed               |

---

### 3️⃣ What is Least Privilege Principle?

Giving only minimum required permissions to perform a task.

---

### 4️⃣ What are Service Control Policies (SCP)?

SCPs are used in AWS Organizations to control maximum permissions for accounts.

---

### 5️⃣ How to enforce MFA for IAM users?

By adding a policy condition:

```json
"Condition": {
  "Bool": {
    "aws:MultiFactorAuthPresent": "true"
  }
}
```

---

### 6️⃣ How to restrict access by IP address?

Using policy condition:

```json
"Condition": {
  "IpAddress": {
    "aws:SourceIp": "192.168.1.0/24"
  }
}
```

---

### 7️⃣ Real Scenario Question

**Q:** User is added to group but still cannot access S3. Why?
**Answer:**

* Policy not attached
* Explicit Deny exists
* SCP blocking access
* Missing required permission
* Resource policy restriction
---------------------------------------------------------------------------------------------------------------------------------------------------------
Created usergroup:
<img width="1919" height="848" alt="Screenshot 2026-02-26 060236" src="https://github.com/user-attachments/assets/5947dff2-fc93-4b25-8923-713c6858bb3b" />
----------------------------------------------------------------------------------------------------------------------------------------------------------
final check:
<img width="1878" height="895" alt="Screenshot 2026-02-26 060215" src="https://github.com/user-attachments/assets/3f97eb3d-450d-4e31-83d8-99b6df07be60" />

