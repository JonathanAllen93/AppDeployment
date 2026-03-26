
# AWS EC2 Image Builder — Create an Image Pipeline (eu‑west‑1)

Use this guide to create a custom AMI using **EC2 Image Builder**.  
The Image Builder pipeline automates building, testing, and distributing an Amazon Machine Image (AMI). :contentReference[oaicite:1]{index=1}

---

## 1. Open the EC2 Image Builder Console

Go to the **Image Builder** section in the AWS Management Console:


---

## 2. Step 1 — Specify Pipeline Details

- Click **Create image pipeline**.
- Enter **Pipeline name** and (optionally) a description.
- Configure the build **schedule**:
  - Manual builds
  - Scheduled builds (daily, weekly, etc.)



**Tip:** Enhanced metadata collection is enabled by default — leave it on for better component compatibility. :contentReference[oaicite:2]{index=2}

---

## 3. Step 2 — Choose a Recipe

- Choose **Create new recipe**.
- Set the **Image type** to **AMI**.
- Enter:
  - **Recipe name**
  - **Version** (e.g., `1.0.0`)
- Choose a base AMI (e.g., Amazon Linux 2).


Add components (like security updates or software packages) if needed. :contentReference[oaicite:3]{index=3}

---

## 4. Step 3 — Infrastructure Configuration (Optional)

- You can use AWS **defaults** to create build instances automatically.
- Or customize:
  - Instance type (e.g., `t3.medium`)
  - Subnet and VPC
  - IAM role
  - Logging settings



If you skip this section, Image Builder uses defaults. :contentReference[oaicite:4]{index=4}

---

## Distribution Settings

This defines where your **final AMI** will be available:

- Target AWS **Regions** (e.g., eu‑west‑1)
- Encryption settings
- Launch permissions (accounts, organizations)



Skip or customize as needed. :contentReference[oaicite:5]{index=5}

---

##   Review & Create

Review all settings:

- Pipeline name
- Recipe and components
- Infrastructure settings
- Distribution configuration

Then click **Create pipeline**



After creation, you’ll see success messages and your pipeline listed. :contentReference[oaicite:6]{index=6}

---

##  Run the Pipeline

Once the pipeline is created:

- Select the pipeline.
- Click **Run pipeline**.
- Wait while Image Builder builds and tests your AMI.


> The status will transition from **Pending** → **Building** → **Available** once finished. :contentReference[oaicite:7]{index=7}

---

## Deploy the AMI

When the pipeline completes:

1. Go to **EC2 → AMIs**.
2. Find your newly created AMI.
3. Click **Launch Instance**.
4. Choose instance type, configure networking & security.
5. Launch the EC2 instance using your custom AMI.

---

## Notes & Tips

- The pipeline may take ~20–40 minutes depending on components and configuration. :contentReference[oaicite:8]{index=8}  
- Image Builder temporarily launches EC2 instances to build the AMI; these cost standard EC2 pricing. :contentReference[oaicite:9]{index=9}  
- You can automate future builds by setting a schedule during pipeline setup. :contentReference[oaicite:10]{index=10}

---

##Useful AWS Docs

- **Create an image pipeline tutorial** — step‑by‑step console walkthrough. :contentReference[oaicite:11]{index=11}  
- **What is Image Builder?** — conceptual overview of features and workflow. :contentReference[oaicite:12]{index=12}

