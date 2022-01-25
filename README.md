# Introduction to Snyk Open Source Workshop

Snyk (pronounced sneak) is a developer security platform for securing code, dependencies, containers, and infrastructure as code. Snyk tests for vulnerabilities in your own code, open source dependencies, container images and infrastructure as code configurations, and offers context, prioritization, and remediation.

## What languages does Snyk support?
At the time of this workshop Snyk supports: JavaScript, Java (Gradle, Maven), .NET, Python, Golang, Swift, Objective-C (CocoaPods), Scala, Ruby, PHP, and Bazel. Learn about Snyk’s language coverage in our support documentation.

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
* [Step 2 Configure GitHub Integration](#step-2-configure-gitHub-integration)

Snyk Code steps
* [Step 3 Enable Snyk Code within Snyk App](#step-3-enable-snyk-code-within-snyk-app)
* [Step 4 Add project to find Snyk Code Vulnerabilities](#step-4-add-project-to-find-snyk-code-vulnerabilities)

Snyk Open Source steps
* [Step 5 Find vulnerabilities](#step-3-find-vulnerabilities)
* [Step 6 Fix using a Pull Request](#step-4-fix-using-a-pull-request)

Snyk Container steps
* [Step 7 Find vulnerabilities in Goof’s Dockerfile](#step-5-find-vulnerabilities-in-goofs-dockerfile)
* [Step 8 Fix the Dockerfile FROM tag using a Pull Request](#step-6-fix-the-dockerfile-from-tag-using-a-pull-request)

Snyk IaC steps
* [Step 9 Find vulnerabilities in Goof’s Kubernetes yaml](#step-5-find-vulnerabilities-in-goofs-dockerfile)

## Prerequisites

* public GitHub account - http://github.com
* snyk CLI - https://support.snyk.io/hc/en-us/articles/360003812538-Install-the-Snyk-CLI
* Registered account on Snyk App - http://app.snyk.io

_NOTE: Please ensure you have meet the Prerequisites prior to starting this workshop_ 

# Workshop Steps

_Note: It is assumed your using a mac for these steps but it should also work on windows or linux with some modifications to the scripts potentially_

## Step 1 Fork the highly vulnerable Goof Application

_NOTE: You may have already forked the Goopf application in that case go ahead and skip this step_

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
* Click on the Repo you forked "*juice-shop**"
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

### Do you think you could fix this issue now?

Finally, to go further, feel free to look at this workshop https://github.com/papicella/snyk-code-workshop where additional steps are available (Snyk Code CLI Test and Snyk Code Test using VS Code)


# Snyk Open Source Steps

Snyk Open Source is a Software Composition Analysis took which seamlessly and proactively finds, prioritizes and fixes vulnerabilities and license violations in open source dependencies

## Step 5 Find vulnerabilities

* Since Juice-Shop project had been imported in the Step 3, you should see a "**package.json**" project as shown below. 

![alt tag](https://i.ibb.co/d4Qb3TV/Snyk-OS-vuln.png)

* Click on the second "**package.json**" to view our Open Source scan results

First let's explore the Juice-Shop project risks by clicking on the "**package.json**" file which is the manifest file where the open source dependencies are declared.

![alt tag](https://i.ibb.co/ZhN6tXY/Package-json-view.png)

Thenk go back on the Snyk WebUI and let's have a look at the vulnerabilities.

For each Vulnerability, Snyk displays the following ordered by our [Proprietary Priority Score](https://snyk.io/blog/snyk-priority-score/) :
1. The module that introduced it and, in the case of transitive dependencies, its direct dependency,
1. Details on the path and proposed Remediation, as well as the specific vulnerable functions
1. Overview
1. Exploit maturity
1. Links to CWE, CVE and CVSS Score
1. Plus more ...

![alt tag](https://i.ibb.co/xq2GWCs/Snyk-OS-vuln.png)

## Step 6 Fix using a Pull Request

When using the GitHub integration, and if a fix is available, Snyk can automatically upgrade the vulnerable dependency to a non-vulnerable version through a Pull Request. 

* Click on "**Fix this vulnerability**" for "**typeorm Prototype Pollution**" issue as shown below

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

Finally, to go further, feel free to look at this workshop https://github.com/papicella/snyk-open-source-workshop where additional steps are available (Testing using the Snyk CLI and the IDE Integration with VS Code)


## Step 5 Find vulnerabilities in Goof’s Dockerfile

Snyk detects vulnerable base images by scanning your Dockerfile when importing a Git repository. This allows you to examine security issues before building the image, so helps solve potential problems before they land in your registry or in production.

Now that Snyk is connected to your GitHub Account, import the Repo into Snyk as a Project as this contains a Dockerfile.

* Navigate to Projects
* Click "**Add Project**" then select "**GitHub**"
* Click on the Repo "goof" that you forked earlier at Step 1.

![alt tag](https://i.ibb.co/q9Rsxsh/snyk-starter-open-source-3.png)

_Note: The import can take up to one minute, so you can view the import log while it's running as shown below_

![alt tag](https://i.ibb.co/RQsX6jZ/snyk-starter-open-source-14.png)

* Once imported you should see a reference for the Dockerfile as shown below. 

![alt tag](https://i.ibb.co/1rNMFhC/snyk-container-9.png)

* Go ahead and click on the Dockerfile this is similar to what a scan of a container from a registry looks like BUT this tim we are scanning a Dockerfile itself versus the full container image.

In a Dockerfile project, you can find the relevant metadata of the Dockerfile and the base image used. If the base image is an [Official Docker image](https://docs.docker.com/docker-hub/official_images/), the results include recommendations for upgrades to resolve some of the discovered vulnerabilities

## Step 6 Fix the Dockerfile FROM tag using a Pull Request

Here we will go ahead and fix our Dockerfile using the "**Open a Fix PR**" button as follows:

* Click on "**Open a Fix PR**" for the base image "**node:16.6.0-slim**" as per below

![alt tag](https://i.ibb.co/5kY26FR/snyk-container-13.png)

* Click on "**Open a Fix PR**" on the resulting page as shown below

![alt tag](https://i.ibb.co/C0tn01C/snyk-container-14.png)

* A PR is then created as show below. "**Files Changed**" will show you what it's updating in the Dockerfile itself

![alt tag](https://i.ibb.co/py4GdJS/snyk-container-15.png)

* Click on "**Merge Pull Request**" button as shown below

![alt tag](https://i.ibb.co/hCwDCFP/snyk-container-16.png)

* Return to the projects dashboard and you will see a new scan has occurred automatically and now our Dockerfile shows much less issues than previously. Of course until we build a new container and add it to the registry the container itself will still have the old base image in place.

![alt tag](https://i.ibb.co/pbqmR1v/snyk-container-17.png)
