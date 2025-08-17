# Security-project
# Task 1: Create a Custom IAM Policy
- In the AWS Console, search for IAM, then choose Policies → Create policy.
- Switch to the JSON editor and replace the default code by right-clicking to Select all and Paste the provided JSON for nano/micro EC2 instance management.
- Scroll down, click Next, name the policy EC2-Admin-Policy, and choose Create policy.

# Task 2: Create User Groups with Permissions
- Go to User groups → Create group → name it EC2-Admin.
- In Attach permissions policies, search for EC2-Admin-Policy, select it, and Create user group.
- Repeat to create EC2-Support with the AmazonEC2ReadOnlyAccess policy.
- Repeat to create S3-Support with the AmazonS3ReadOnlyAccess policy.

# Task 3: Create IAM Users and Assign to Groups
- Create user-1:
- Enable console access, set custom password Sim-Password1, clear “must reset” checkbox.
- Add to S3-Support group → Create User.
- Create user-2:
- Enable console access, set custom password Sim-Password2, clear “must reset.”
- Add to EC2-Support group → Create User.
- Create user-3:
- Enable console access, set custom password Sim-Password3, clear “must reset.”
- Do not assign to any group → Create User.

# Task 4: Add user-3 to a Group via the Group
- Navigate to User groups → select EC2-Admin → Add users.
- Check user-3 and choose Add users.

# Task 5: Review Policies Attached to user-2
- Go to Users → select user-2 → Permissions pane.
- Click AmazonEC2ReadOnlyAccess → view its JSON under Permissions defined in this policy.

# Task 6: Test user-1’s S3 Read-Only Access
- In IAM Dashboard, copy the Sign-in URL for IAM users.
- Open a private/incognito browser window, paste the URL, sign in as user-1 (Sim-Password1).
- Go to S3 → open a bucket → confirm you can list and view objects but get an error when attempting Upload.

# Task 7: Test user-2’s EC2 Read-Only Access
- In a second incognito tab, sign in as user-2 (Sim-Password2).
- Open EC2 → Instances → attempt to Stop instance → confirm you receive a “not authorized” error.

# Task 8: Test and Extend user-3’s Permissions
- In a third incognito tab, sign in as user-3 (Sim-Password3).
- In EC2, successfully Stop and Start the instance.
- Try S3 → confirm “no permissions” to list buckets.
- Back in IAM console, add user-3 to S3-Support group.
- Return to the incognito tab and Refresh; verify user-3 now has S3 read-only access.

