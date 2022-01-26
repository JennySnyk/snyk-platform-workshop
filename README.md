# Introduction to Snyk Open Source Workshop

Snyk (pronounced sneak) is a developer security platform for securing code, dependencies, containers, and infrastructure as code. Snyk tests for vulnerabilities in your own code, open source dependencies, container images and infrastructure as code configurations, and offers context, prioritization, and remediation.

## What languages does Snyk support?
At the time of this workshop Snyk supports: JavaScript, Java (Gradle, Maven), .NET, Python, Golang, Swift, Objective-C (CocoaPods), Scala, Ruby, PHP, and Bazel. Learn about Snyk’s language coverage in our support documentation ([Snyk Open Source](https://docs.snyk.io/products/snyk-open-source/language-and-package-manager-support), [Snyk Code](https://docs.snyk.io/products/snyk-code/snyk-code-language-and-framework-support)).

## What products and platforms does Snyk offer?
Snyk’s developer security platform integrates four key products: Snyk Open Source, Snyk Code, Snyk Container, and Snyk Infrastructure as Code (Kubernetes, Terraform, etc.).

## Which tools, IDEs, and platforms does Snyk integrate with?
Taking a developer-first approach to security, Snyk integrates with leading IDE, repository, CI/CD, runtime, registry, and issue management tools.

## How does Snyk’s security and vulnerability data compare to other vulnerability databases?
Our security intelligence database, also known as the Snyk Intel Vulnerability Database is maintained by a dedicated research team that combines public sources, contributions from the developer community, proprietary research, and machine learning to continuously adapt to the changing and expanding nature of security threats.

## Does Snyk have a CLI?
You can use the CLI for scanning and monitoring on your local machine, and integrate it into your pipeline. You can use the Snyk CLI to scan your applications, containers, and infrastructure as code for security vulnerabilities.You can install the CLI via npm, Homebrew, Scoop, or manually. Learn more in our Snyk CLI documentation.

## What we will do in this hands-on workshop?
In this hands-on workshop we will achieve the follow:
* [Step 1 Fork the highly vulnerable Juice-Shop Application](#step-1-fork-the-highly-vulnerable-goof-application)
* [Step 2 Configure GitHub Integration](#step-2-configure-github-integration)

Snyk Code steps
* [Step 3 Enable Snyk Code within Snyk App](#step-3-enable-snyk-code-within-snyk-app)
* [Step 4 Add project to find Snyk Code Vulnerabilities](#step-4-add-project-to-find-snyk-code-vulnerabilities)

Snyk Open Source steps
* [Step 5 Find vulnerabilities](#step-5-find-vulnerabilities)
* [Step 6 Fix using a Pull Request](#step-6-fix-using-a-pull-request)

Snyk Container steps
* [Step 7 Find vulnerabilities in Juice-shop’s Dockerfile](#step-7-find-vulnerabilities-in-juice-shops-dockerfile)
* [Step 8 Fix the Dockerfile FROM tag using a Pull Request](#step-8-fix-the-dockerfile-from-tag-using-a-pull-request)

Snyk IaC steps
* [Step 9 Find vulnerabilities in Juice-Shop’s Kubernetes.yml](#step-9-find-vulnerabilities-in-juice-shops-kubernetesyml)
* [Step 10 View Snyk IaC Rules](#step-10-view-snyk-iac-rules)

## Prerequisites

* public GitHub account - http://github.com
* Registered account on Snyk App - http://app.snyk.io

_NOTE: Please ensure you have meet the Prerequisites prior to starting this workshop_ 

# Workshop Steps

_Note: It is assumed your using a mac for these steps but it should also work on windows or linux with some modifications to the scripts potentially_

## Step 1 Fork the highly vulnerable Goof Application

_NOTE: You may have already forked the Goof application in that case go ahead and skip this step_

Navigate to the following GitHub repo - https://github.com/juice-shop/juice-shop

* Click on the "**Fork**" button
* Ensure you are forking this repo to your public GitHub account 
* Click done

![alt tag](https://i.ibb.co/PYCX43Q/Juice-Shop-Github.png)

## Step 2 Configure GitHub Integration

_NOTE: You may have already setup GitHub integration in that case go ahead and skip this step_

First we need to connect Snyk to GitHub so we can import our Repository. Do so by following these steps below:

* Login to http://app.snyk.io Sign up if you haven't already.
* Navigating to Integrations -> Source Control -> GitHub
* Fill in your Account Credentials to Connect your GitHub Account.

![alt tag](https://i.ibb.co/bPqqybM/snyk-starter-open-source-1.png)

<br />
<br />
<br />

# Snyk Code Steps

Snyk Code is developer-first, embedding SAST as part of the development process, enabling developers to build software securely during development, not trying to find and fix problems after the code is compiled. Snyk Code works in the IDEs and SCMs developers use to build and review software and provides fast, actionable, meaningful results to fix issues in real-time

## Step 3 Enable Snyk Code within Snyk App

* Click on the "**Settings**" button on the top most navigation bar as shown below

![alt tag](https://i.ibb.co/3fS4VCd/snyk-code-1.png)

* Click on "**Snyk Code**", then enable it and click "**Save Changes**" as shown below

![alt tag](https://i.ibb.co/bP2FpGx/snyk-code-2.png)

## Step 4 Add project to find Snyk Code Vulnerabilities

Now that Snyk is connected to your GitHub Account, import the Forked Repo "**juice-shop**" into Snyk as a Project.

* Navigate to Projects
* Click "**Add Project**" then select "**GitHub**"
* Click on the Repo you forked "**juice-shop**"
* Click "**Add Selected Repositories**"

![alt tag](https://i.ibb.co/ngxDfvw/Import-Juice-Shop.png)

* Once complete you should see a "**Code Analysis**" project as shown below

![alt tag](https://i.ibb.co/RpScxJ2/Snyk-Code-Results.png)

* Click on "**Code Analysis**" to view our SAST scan results

For each Vulnerability, Snyk displays the following:

1. Each Vulnerability grouped by severity
2. Each Vulnerability links to the CWE category code
3. Each Vulnerability shows the CWE category name
4. Displays the line of code where the security issue exists
5. Description for the issue and the code file name it exists in
6. A link to a Snyk Learn module on how to fix these type of vulnerabilities if available
7. The ability to ignore issues you wish to remove from the list

![alt tag](https://i.ibb.co/yk83tyP/Snyk-Code-vuln.png)

* Click on the "**Full Details**" button as shown below

Snyk products all provide a developer-friendly experience, so Snyk Code helps developers to quickly understand the problem, learn the background, and how to approach it. Snyk Code helps you understand the dangerous code flow step-by-step. For every issue, Code also provides a link to the lines in the relevant files, to view more details on the problem like the CWE, and how to approach it.

![alt tag](https://i.ibb.co/HnL22t7/Cross-site-scripting-Dataflow.png)

* Click on "**Fix Analysis**" to see how you can fix the issue based on other open source project. On this page you get not just source code example fixes but also the following detailed information

1. Details
2. Types Of Attacks
3. Affected Environments
4. How to prevent

![alt tag](https://i.ibb.co/M21xScH/Cross-site-scripting-Fix-Analysis.png)

## To Go Further with Snyk Code - Snyk Code workshop

Finally, to go further, feel free to look at this workshop https://github.com/papicella/snyk-code-workshop where additional steps are available (Snyk Code CLI Test and Snyk Code Test using VS Code)

<br />
<br />
<br />
<hr />

# Snyk Open Source Steps

Snyk Open Source is a Software Composition Analysis took which seamlessly and proactively finds, prioritizes and fixes vulnerabilities and license violations in open source dependencies

## Step 5 Find vulnerabilities

* Since Juice-Shop project had been imported in the Step 3, you should see a "**package.json**" project as shown below. 

![alt tag](https://i.ibb.co/d4Qb3TV/Snyk-OS-vuln.png)

* Click on the second "**package.json**" to view our Open Source scan results

First let's explore the Juice-Shop project risks by clicking on the "**package.json**" file which is the manifest file where the open source dependencies are declared.

![alt tag](https://i.ibb.co/ZhN6tXY/Package-json-view.png)

Thenk go back on the Snyk WebUI and let's have a look at the vulnerabilities.

For each Vulnerability, Snyk displays the following ordered by our [Proprietary Priority Score](https://docs.snyk.io/features/fixing-and-prioritizing-issues/starting-to-fix-vulnerabilities/snyk-priority-score) :
1. The module that introduced it and, in the case of transitive dependencies, its direct dependency,
1. Details on the path and proposed Remediation, as well as the specific vulnerable functions
1. Overview
1. Exploit maturity
1. Links to CWE, CVE and CVSS Score
1. Plus more ...

![alt tag](https://i.ibb.co/xq2GWCs/Snyk-OS-vuln.png)

## Step 6 Fix using a Pull Request

When using the GitHub integration, and if a fix is available, Snyk can automatically upgrade the vulnerable dependency to a non-vulnerable version through a Pull Request. 

* Click on "**Fix this vulnerability**" for "**Prototype Pollution**" issue as shown below

![alt tag](https://i.ibb.co/9NHPmn2/Snyk-OS-Fix-this-vuln.png)

* On the next screen, you'll be able to confirm the issue to fix with this PR. Click "**Open a Fix PR**"

![alt tag](https://i.ibb.co/y5PHhhT/Vulns-to-fix-pr-view.png)
![alt tag](https://i.ibb.co/p2Lx5Rd/Open-fix-pr-button.png)

* Once it's ready, you'll be taken to the PR in GitHub, where you can review the changes in the file diff view:

Snyk integrates with your preferred Git repository to scan your manifest files for any new code and potential vulnerabilities whenever you submit a pull request (PR), protecting the security of your code before you ever merge it with the main branch

![alt tag](https://i.ibb.co/ySc72zN/Fix-PR-Github.png)

* We see that CI checks completed successfully, assuring us we didn't introduce a breaking change

![alt tag](https://i.ibb.co/BzrNHvg/Files-changed-Github.png)

* Optionally now, go ahead and merge the PR!
* Back in Snyk we can appreciate that our package.json file has 1 less Critical Severity Vulnerability if you did fix it

## To Go Further with Snyk Open Source - Snyk Open Source workshop

Finally, to go further, feel free to look at this workshop https://github.com/papicella/snyk-open-source-workshop where additional steps are guided (Testing using the Snyk CLI and the IDE Integration with VS Code)

<br />
<br />
<br />

# Snyk Container Steps

Snyk Container helps you find and fix vulnerabilities in container images. With snyk container you can scale your security capabilities by enabling developers to quickly eliminate a multitude of vulnerabilities by upgrading to a more secure base image or rebuilding when the base image is outdated

You may not always have access to the original source code that runs in your containers, but vulnerabilities in your code dependencies are still important. Snyk can detect and monitor open source dependencies for popular languages as part of the container scan

## Step 7 Find vulnerabilities in Juice-Shop’s Dockerfile

Snyk detects vulnerable base images by scanning your Dockerfile when importing a Git repository. This allows you to examine security issues before building the image, so helps solve potential problems before they land in your registry or in production.

* Since Juice-Shop project had been imported in the Step 3, you should see a reference for the Dockerfile as shown below. 

![alt tag](https://i.ibb.co/3F6v7x7/Snyk-Container-results.png)

In a Dockerfile project, you can find the relevant metadata of the Dockerfile and the base image used. If the base image is an [Official Docker image](https://docs.docker.com/docker-hub/official_images/), the results include recommendations for upgrades to resolve some of the discovered vulnerabilities.
This is handy as we can remove a substantial amount of issues just by using an alternative base image from minor upgrades to major upgrades if available will be shown including what issues will remain if the basde image is changed and the container re-built.  

![alt tag](https://i.ibb.co/myJ2Yf4/Snyk-Container-recommendations-base-image.png)

The supported base images can be found at this [link](https://snyk.io/docker-images/)

For each Vulnerability, Snyk displays the following ordered by our [Proprietary Priority Score](https://docs.snyk.io/features/fixing-and-prioritizing-issues/starting-to-fix-vulnerabilities/snyk-priority-score) :

1. The module (O/S, base image) that introduced it and, in the case of transitive dependencies, its direct dependency
1. Details on the path and proposed Remediation, as well as the specific vulnerable functions
1. Overview
1. Exploit maturity
1. Links to CWE, CVE and CVSS Score
1. Social Trends
1. Plus more ...

![alt tag](https://i.ibb.co/X72chjn/Snyk-Container-vuln.png)

## Step 8 Fix the Dockerfile FROM tag using a Pull Request

Here we will go ahead and fix our Dockerfile using the "**Open a Fix PR**" button as follows:

* Click on "**Open a Fix PR**" for the base image "**node:17.4-slim**" as per below

![alt tag](https://i.ibb.co/1ftgqXL/Open-a-fix-PR-image.png)

* Click on "**Open a Fix PR**" on the resulting page as shown below

![alt tag](https://i.ibb.co/nkfQ6nY/Open-a-fix-PR-Image-2.png)

* A PR is then created as show below. 

![alt tag](https://i.ibb.co/sCP7Fk3/Github-fix-PR-base-image.png)

"**Files Changed**" will show you what it's updating in the Dockerfile itself

![alt tag](https://i.ibb.co/Sfzxm6s/Github-fix-PR-base-image-files-changed.png)

* Click on "**Merge Pull Request**" 

* Return to the projects dashboard and you will see a new scan has occurred automatically and now our Dockerfile shows much less issues than previously. 

![alt tag](https://i.ibb.co/vzndsKy/Snyk-Container-new-base-image.png)

## To Go Further with Snyk Container - Snyk Container workshop

Finally, to go further, feel free to look at this workshop https://github.com/papicella/snyk-container-workshop where you will be able to scan a container image from a Docker Hub integration and do Container test using the Snyk CLI. 

<br />
<br />
<br />

# Snyk Infrastructure as Code Steps

Snyk Infrastructure as Code allows you to find and fix vulnerabilities in your Kubernetes, Helm, Terraform, ARM and CloudFormation configuration files

Developer-focused infrastructure as code security with Snyk allows you to test and monitor Terraform modules and Kubernetes YAML, JSON, and Helm charts to detect configuration issues that could open your deployments to attack and malicious behavior.

## Step 9 Find vulnerabilities in Juice-Shop’s Kubernetes.yml

* Since Juice-Shop project had been imported in the Step 3, you should see a reference for the deployment file as shown below. 

![alt tag](https://i.ibb.co/zRB8dqY/Snyk-Ia-C-results.png)

For each Vulnerability, Snyk displays the following ordered by Line no:

1. Each Vulnerability grouped by line number and severity 
1. Each Vulnerability links to the Snyk policy it was defined against including the path to the issue, what the issue is, the impact and how to resolve it
1. The ability to ignore issues you wish to remove from the list

![alt tag](https://i.ibb.co/MMFXpwc/Screenshot-2022-01-25-at-20-49-45.png)

## Step 10 View Snyk IaC Rules

Snyk IaC has a comprehensive set of security rules across AWS, Azure, GCP & Kubernetes with support for Terraform, CloudFormation, Kubernetes, and Helm configuration formats. The details of these issues, their impact, and how to fix them are all built-in to Snyk IaC, so developers get feedback directly in their own tools. For reference, we have also documented the security rules that we support for each provider below, along with relevant benchmarks and authoritative third-party references

Navigate to [Snyk Infrastructure as Code list of rules](https://snyk.io/security-rules)

## To Go Further with Snyk IaC - Snyk Infrastructure as Code workshop

Finally, to go further, feel free to look at this workshop https://github.com/papicella/snyk-iac-workshop where you will be able to test different IaC files and test using the Snyk CLI.

Thanks for attending and completing this workshop

![alt tag](https://i.ibb.co/7tnp1B6/snyk-logo.png)

<hr />
This workshop is a compliation of Workshops provided by Pas Apicella [pas at snyk.io] a Principal Solution Engineer at Snyk APJ
