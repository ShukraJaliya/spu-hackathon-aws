
# 🚀 Student Developer Portfolio Project

🎉 Welcome to your student/junior developer portfolio project, designed especially for showcasing your work at events, hackathons, or as an online resume! This project uses AWS CDK with TypeScript to make your portfolio easily deployable on AWS. 

NOTE 10/30: The provided AWS key has been deactivated, you will have to create your own (see [Optional: AWS Account Setup Instructions](#optional-aws-account-setup-instructions)).

## 🎓 Project Description

This project is tailored to help students and junior developers create an online portfolio hosted on AWS. It's the perfect chance to showcase your skills, experience, and education. The content can be quickly updated by editing `index.html` and `styles.css` in the `website` directory.

---

## Directory

- [Cloning the GitHub Repository](#cloning-the-github-repository)
- [Windows Setup Instructions](#windows-setup-instructions)
- [MacOS Setup Instructions](#macos-setup-instructions)
- [AWS CDK Setup (Platform Agnostic)](#aws-cdk-setup-platform-agnostic)
- [Optional: AWS Account Setup Instructions](#optional-aws-account-setup-instructions)
- [Deployment Instructions Using Provided .csv Credentials](#deployment-instructions-using-provided-csv-credentials)
- [Updating and Redeploying the Site](#updating-and-redeploying-the-site)
- [Further Steps (Optional): Domain Setup in Route 53](#further-steps-optional-domain-setup-in-route-53)

## 🔗 Cloning the GitHub Repository

1. **Download or Clone the GitHub Repository**:
   - Visit [GitHub Repository](https://github.com/pkimani/spu-hackathon-aws) to view and clone.
   - To clone using GitHub CLI:
     ```bash
     gh repo clone pkimani/spu-hackathon-aws
     ```
   - Alternatively, you can download a ZIP file of the repository.

2. **Customize Your Portfolio**:
   - Edit `index.html` to include your personal details such as name, biography, education, experience, and skills.
   - Update `styles.css` to adjust the style and branding to your preference.

---

## 🪟 Windows Setup Instructions

### Node.js Install Instructions for Windows

1. Install Fast Node Manager (fnm):
   ```powershell
   winget install Schniz.fnm
   ```
2. Restart your terminal (close and reopen it).

3. Configure the fnm environment:
   ```powershell
   fnm env --use-on-cd | Out-String | Invoke-Expression
   ```
4. Download and install Node.js:
   ```powershell
   fnm use --install-if-missing 22
   ```
5. Verify Node.js version (expected output: `v22.11.0`):
   ```powershell
   node -v
   ```
6. Verify npm version (expected output: `10.9.0`):
   ```powershell
   npm -v
   ```

### AWS CLI Install Instructions for Windows

1. Run the MSI installer to install AWS CLI:
   ```powershell
   msiexec.exe /i https://awscli.amazonaws.com/AWSCLIV2.msi
   ```
2. Restart terminal (close and reopen it).

3. Confirm the installation by checking the AWS CLI version:
   ```powershell
   aws --version  # Example: aws-cli/2.17.20
   ```

---

## 🍏 MacOS Setup Instructions

### Node.js Install Instructions for MacOS

1. Install Fast Node Manager (fnm):
   ```bash
   curl -fsSL https://fnm.vercel.app/install | bash
   ```
2. Activate `fnm`:
   ```bash
   source ~/.bashrc
   ```
3. Download and install Node.js:
   ```bash
   fnm use --install-if-missing 22
   ```
4. Verify Node.js version (expected output: `v22.11.0`):
   ```bash
   node -v
   ```
5. Verify npm version (expected output: `10.9.0`):
   ```bash
   npm -v
   ```

### AWS CLI Install Instructions for MacOS

1. Download the AWS CLI package:
   ```bash
   curl "https://awscli.amazonaws.com/AWSCLIV2.pkg" -o "AWSCLIV2.pkg"
   ```
2. Install AWS CLI:
   ```bash
   sudo installer -pkg ./AWSCLIV2.pkg -target /
   ```
3. Verify installation by running:
   ```bash
   which aws  # Expected: /usr/local/bin/aws
   aws --version  # Example: aws-cli/2.17.20
   ```

---

## 🛠 AWS CDK Setup (Platform Agnostic)

1. Install AWS CDK globally:
   ```bash
   npm install -g aws-cdk
   ```
2. Install necessary CDK libraries:
   ```bash
   npm install @aws-cdk/aws-s3 @aws-cdk/aws-s3-deployment @aws-cdk/aws-cloudfront @aws-cdk/aws-cloudfront-origins
   ```
3. Verify CDK installation:
   ```bash
   cdk --version
   ```

4. Apply AWS Credentials.
   - Open the access.csv
   - In console, run AWS configuration
   ```bash
   aws configure
   ```
   - When prompted, enter the ID token, and secret access token
   - Use "us-west-1" for region and "json" for output format (without quotes)

---

## OPTIONAL: 🔑 AWS Account Setup Instructions

1. **Visit AWS Signup Page**: [AWS Signup](https://signin.aws.amazon.com/signup?request_type=register).
2. **Enter your details**:
   - Email: your-email@spu.edu
   - Account name: admin
3. **Verify and Complete**:
   - Complete verification with a code sent to your email.
   - Provide payment info and verify your mobile.

### Budget Setup to Avoid Billing Issues

1. Click account name in top right of window.
2. Navigate to **Billing and Cost Management** in AWS Console.
3. Under **Budgets**, select **Create a Budget**.
4. Choose "Zero spend budget" and enter an email for notifications.

### IAM User Creation for Security

1. Access the **IAM Console** and create a new user (e.g., `hackathon-user`).
2. Select **Programmatic access**.
3. Choose **Attach existing policies directly** attach **AdministratorAccess** policy
4. Click **Next** through **Tags** and **Review** and select **Create User**.
5. Click on **hackathon-user** or user you made in IAM Console
6. Select **Create access key** and then select **Command Line Interface (CLI)**
7. Select **Create access key** and download the `.csv` with Access Key ID and Secret Access Key.

### AWS CLI Configuration with Credentials

1. Run:
   ```bash
   aws configure
   ```
2. Input Access Key, Secret Access Key, Region (`us-west-1`), and output format (`json`).
3. Verify by running:
   ```bash
   aws sts get-caller-identity
   ```

### AWS Account Initialization
1. To setup the account (needs only to be done once for the lifetime of the account)
   ```bash
   aws bootstrap
   ```

---

## 🚀 Deployment Instructions (Using Provided `.csv` Credentials)

This guide provides step-by-step instructions for deploying your project to AWS using pre-configured `.csv` credentials. Make sure the `access.csv` file is in the root directory to enable a seamless deployment process.

### Steps

1. **Change to the Project Directory**:
   ```bash
   cd "spu-hackathon-aws"
   ```

2. **Install NPM Dependencies**:
   ```bash
   npm install
   ```

3. **Build the Project**:
   ```bash
   npm run build
   ```

4. **Deploy to AWS**:
   ```bash
   cdk deploy --context studentId=<YOUR-STUDENT-ID-HERE>
   ```

5. **Verify Deployment**:
   - Once deployed, view your website link in the **Outputs** section of the terminal.

---

## 🔄 Updating and Redeploying the Site

1. **Edit Content**: Update `index.html` and `styles.css` with your latest portfolio changes.

2. **Rebuild and Deploy**:
   ```bash
   npm run build
   cdk deploy --context studentId=<YOUR-STUDENT-ID-HERE>
   ```

3. Access the updated link under **Outputs** in AWS or the AWS Console.

Happy building, and best of luck with your hackathon! 🎉

---

## 🌐 Further Steps (OPTIONAL): Domain Setup in Route 53

Create a domain name and attach to your website.

1. **Register a Domain in Route 53**:
   - Go to the **Route 53 Console**.
   - Select **Domains** > **Register Domain**.
   - Follow prompts to register a new domain.

2. **Configure a Hosted Zone**:
   - In **Route 53 Console**, select **Hosted Zones** and click **Create Hosted Zone**.
   - Enter your domain name, and Route 53 will create a DNS zone for you.

3. **Add an S3 Website Alias**:
   - Select the hosted zone you just created, click **Create Record Set**.
   - Set the record name (leave blank for root domain or use subdomain like `student1`).
   - For alias target, enter the **S3 Website Endpoint** (found in S3 bucket settings).
   - Click **Create** to save the record.

4. **Update the CDK Stack**:
   - Modify the CDK stack to output the custom domain URL by setting up an alias record in Route 53 for the S3 website.
