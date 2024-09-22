# StaticWebsiteOnS3
### Skills
* Static Web Hosting
* Basic Web development
### Objective
To learn how to upload files, configure S3 for static hosting, and making the site public.
### Amazon S3 Bucket Policy
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::Bucket-Name/*"
            ]
        }
    ]
}
```
### Procedure
**Note: Follow the Green Arrow in the Visual Aids**
* Sign-in to AWS Management Console
* Type S3 in the search bar at the top of the console dashboard and click S3. This leads to the S3 dashboard.![Screenshot (760)](https://github.com/user-attachments/assets/e84f5cf8-a6c9-47ae-8767-04fd2edc3c01)
* On the S3 dashboard, Click ***Create bucket***
* Under General Configurations, Select ***General Purpose*** for Bucket type, input a *globally unique bucketname*.
* Under Object Ownership, Leave as Default ACLs Disabled(Recommended)
* Under Block Public Access settings for this bucket, ***Unselect Block all public access***.  ![Screenshot (761)](https://github.com/user-attachments/assets/4ba79009-5460-4351-9a7a-460cc2731db5)
* Select the acknowledgement to turn off block public access. ![Screenshot (762)](https://github.com/user-attachments/assets/d85f1f8b-9ffa-499b-88e9-9539f5cca034)
* Leave other options as Default and Click ***Create bucket***. This would take you to the bucket list on the S3 dashboard.
* Double-click on your bucket name. Click ***Upload***.
* On the next page, you have two options to uploading files. First is to drag and drop the files and folders in the root dirctory. Please note, do not drag and drop the root directory itself, but the content of the root directory ![Screenshot (768)](https://github.com/user-attachments/assets/60bfd73a-ba0d-4d7d-9762-d59dc238bb23)
* Second option is to upload the files and folders in the root directory separately.
* Select ***Add Files***, navigate to the root directory, select all files and click Open.
* Select ***Add Folders***, navigate to the root directory, select all folders and click Open.
* Scroll to the bottom and Click ***Upload***.
* Wait a few seconds for the files to upload successfully ![Screenshot (769)](https://github.com/user-attachments/assets/d2029640-dfac-4c1e-8872-2a8390bd07fb)
* Click ***Close*** on the top right corner to return to the bucket dashboard.
* On the bucket dashboard, Click on the ***Properties tab***, Scroll down to static website hosting and click edit.
* Select ***Enable static website hosting***. Scroll down to Index document and type ***index.html***, leave others as default and click ***Save Changes***.
* Still on the Properties tab, Scroll down to Static Website hosting again. This time, the bucket URL would be available. Copy and paste on a new browser tab.![Screenshot (766)](https://github.com/user-attachments/assets/63c7fa6a-3e36-4aa1-80fa-306e51f7b756)
* The bucket url should display ***403 Forbidden error*** at this point.
* To display the content of the bucket, Scroll up and Click on the ***Permissions tab***.
* Scroll down to ***Bucket policy*** and click ***Edit***
* Copy and paste the bucket policy stated above [Amazon S3 Bucket Policy](https://github.com/EbuwaJulia/StaticWebsiteOnS3/edit/main/README.md#amazon-s3-bucket-policy)
* Replace Bucket-Name with your actual bucket name. ![Screenshot (767)](https://github.com/user-attachments/assets/df403e73-e1c1-4a00-97ea-001b7f06008c)
* Scroll down and click ***Save changes***.
* Refresh the website tab. Voila!!! Content is rendered.
* You have successfully deployed a static website.


