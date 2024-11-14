
![[jigsaw-platform.jpg]]
Infrastructure Overview

- Developers write code and commit changes to the GitLab repository.

- The code is pushed to the GitLab repository. GitLab CI/CD can be configured to trigger builds, tests, and deployment pipelines.

- Jenkins is integrated with GitLab to trigger jobs based on events like code commits or merge requests. GitLab webhooks notify Jenkins of new commits or merges, triggering the CI pipeline.The Jenkinsfile in the repository defines the pipeline stages and steps.

- Jenkins uses service principal credentials to authenticate with Azure. The build artifacts (e.g. application package) are transferred to the Azure VM.

- The MySQL database is hosted within the Azure Virtual Machine (VM), providing a robust and flexible environment for database management.

- The Azure Virtual Machine (VM) is secured and managed within a Virtual Network (VNet).It ensures that the VM is shielded from unauthorized access by controlling inbound and outbound traffic through network security groups (NSGs).

