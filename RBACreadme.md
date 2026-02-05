# Jenkins RBAC (Role-Based Access Control) using Role Strategy Plugin

This guide explains how to configure **user permissions in Jenkins** using  
the **Role-Based Authorization Strategy (RBAC)** so different users (Admin, Developer, Viewer) can access only what they are allowed to.

---

## Step 0 — Create Users (FIRST STEP)

Before assigning roles, Jenkins users must exist.

Navigate:

    Manage Jenkins → Manage Users → Create User

Fill the form:

    Username
    Password
    Confirm Password
    Full Name
    Email Address

Example users:

    bhawna     → Developer
    rajul      → Viewer
    rajulvish  → Another user

Click **Create User**

Important:
Roles cannot be assigned to users that do not exist yet.

---

## What is RBAC in Jenkins?

RBAC allows you to control:

    Who can open Jenkins
    Who can view jobs
    Who can run pipelines
    Who can configure jobs
    Who can administer Jenkins

Instead of giving everyone full admin access, we create roles and assign permissions.

---

## Plugin Required

Install plugin:

    Role-based Authorization Strategy

Navigate:

    Manage Jenkins → Plugins → Available Plugins
    Search: Role-based Authorization Strategy
    Install → Restart Jenkins

---

## Enable Role Strategy Security

Go to:

    Manage Jenkins → Configure Global Security

Under Authorization choose:

    Role-Based Strategy

Save.

Now new menu appears:

    Manage Jenkins → Manage and Assign Roles

---

## Permission Hierarchy (Very Important)

Jenkins checks permissions in order:

1) Overall/Read → Can open Jenkins UI
2) Job/Read → Can see jobs
3) Job/Build → Can run pipeline
4) Configure/Administer → Can change settings

If Overall/Read is missing → User cannot even login to dashboard.

---

## Step 1 — Create Roles

Navigate:

    Manage Jenkins → Manage and Assign Roles → Manage Roles

You will see two sections:

    Global Roles
    Item Roles

---

## Global Roles (System level access)

Create roles:

    admin
    dev
    viewer

### Admin Role (Full control)

Enable:

    Overall → Administer

(This automatically grants all permissions)

---

### Developer Role (Can build pipelines)

Enable:

    Overall → Read
    Overall → View

    Job → Read
    Job → Build
    Job → Workspace

    Run → Replay
    Run → Update

Purpose:
Developer can run and debug pipelines but cannot change system configuration.

---

### Viewer Role (Read only)

Enable:

    Overall → Read
    Overall → View
    Job → Read

Purpose:
User can see job status but cannot run builds.

Click Save.

---

## Step 2 — Item Roles (Optional Project Level Access)

Item roles restrict access to specific jobs.

Example:

    Role name: projectA-dev
    Pattern: projectA.*

Permissions:

    Job → Read
    Job → Build

Meaning:
User can only build jobs starting with "projectA".

---

## Step 3 — Assign Roles to Users

Go to:

    Manage Jenkins → Manage and Assign Roles → Assign Roles

Assign roles:

    bhawna → dev
    rajul → viewer
    admin → admin

Save.

---

## Common Error

### Access Denied — missing Overall/Read

Reason:
User has job permissions but no permission to open Jenkins UI.

Fix:

    Manage Roles → Enable Overall → Read for that role

Without this Jenkins blocks login completely.

---

## Recommended Permission Matrix

| Role | Access |
|----|----|
| Admin | Full Jenkins control |
| Developer | Run & debug pipelines |
| Viewer | Only view build status |

---

## How Jenkins Evaluates Permissions

    User logs in
        ↓
    Check Overall/Read
        ↓
    Show Dashboard
        ↓
    Check Job permissions
        ↓
    Allow build execution

If first check fails → Access Denied page appears.

---

## Best Practices

Do NOT give admin to developers  
Always give Overall/Read first  
Use Item roles for project isolation  
Separate DevOps and Developer privileges  

---

## Result

After configuration:

    Admin manages Jenkins
    Developers run pipelines
    Viewers monitor builds

Secure CI/CD environment is achieved.
