# Backup-Elastic-Cloud-Snapshot-to-GCP-Bucket

Objective:

This document provides a step-by-step guide to backup Elastic Cloud snapshots to a Google Cloud Platform (GCP) bucket. The backup process is scheduled to run every day at 3:30 AM. To achieve this, we will create a GCP bucket, set up a service account with appropriate permissions, configure Elastic Cloud to use the service account key, create a repository, and set up a backup policy.

Prerequisites:

-  Access to Elastic Cloud deployment.
-  Access to Google Cloud Platform console.
-  Permissions to create buckets and manage service accounts.

Procedure:

1. Create GCP Bucket:

-  Log in to the Google Cloud Platform console.
-  Navigate to the Storage section.
-  Click on "Create Bucket".
-  Provide a unique name for the bucket and configure any additional settings as needed.
-  Click "Create" to create the bucket.

2. Create Service Account Key:

-  Navigate to the IAM & Admin section in the GCP console.
-  Click on "Service Accounts".
-  Create a new service account or select an existing one.
-  Set Storage admin or Storage Object creator permission
-  Under "Actions", click on "Create Key" and select JSON format.
-  Save the JSON file securely as it contains sensitive information.

3. Configure Elastic Cloud:

-  Navigate to your Elastic Cloud deployment.
-  Go to the "Security" section and click on "Keystore".
-  Add a new setting with the name "gcs.client.default.credentials_file" and upload the JSON
-  key file obtained in the previous step.

4. Create Repository:

-  Go to the "Snapshot and Restore" section in Elastic Cloud.
-  Click on "Repositories" and then "Create Repository".
-  Select "Google Cloud Storage" as the repository type.
-  Provide a name for the repository.
-  Configure the repository settings including the GCP bucket name and folder path.
-  Click "Register" to create the repository.

5. Verify Repository Connection:

-  Once the repository is created, verify that Elastic Cloud can connect to the GCP bucket successfully.

6. Create Backup Policy:

-  In the "Snapshot and Restore" section, click on "Policies" and then "Create Policy".
-  Provide a name for the policy.Select the repository created earlier.
-  Configure snapshot settings(enable all options here) (e.g., frequency, time).
-  Set retention time for snapshots.
-  Save the policy.

7. Repeat for Other Projects:

-  Repeat the above steps for other Elastic Cloud deployments or projects as needed.

Conclusion:

By following the steps outlined in this document, Elastic Cloud snapshots will be automatically backedup to the specified GCP bucket according to the defined schedule. This ensures data resilience and disaster recovery for your Elastic Cloud deployments.
