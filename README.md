![image](https://github.com/user-attachments/assets/daf81032-16a6-4f8a-bc3a-a2c615ee00d3)# StaticWebsiteOnS3
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
* On the S3 dashboard, Click *Create bucket*
* Under General Configurations, Select *General Purpose* for Bucket type, input a *globally unique bucketname*.
* Under Object Ownership, Leave as Default ACLs Disabled(Recommended)
* Under Block Public Access settings for this bucket, *Unselect Block all public access*.  ![Screenshot (761)](https://github.com/user-attachments/assets/4ba79009-5460-4351-9a7a-460cc2731db5)
* Select the acknowledgement to turn off block public access. ![Screenshot (762)](https://github.com/user-attachments/assets/d85f1f8b-9ffa-499b-88e9-9539f5cca034)
* Leave other options as Default and Click *Create bucket*. This would take you to the bucket list on the S3 dashboard.
* Double-click on your bucket name. Click *Upload*, and on the new page, Click *Add Files*
* If the files are in a folder, open the folder, select all the items in the folder and click *Open*. Do this for all the necessary files. ![Screenshot (764)](https://github.com/user-attachments/assets/b43ae1e3-075e-4a4b-b5f1-2cdbc9609204)
* Scroll to the bottom and Click Upload.
* Wait a few seconds for the files to upload successfully ![Screenshot (765)](https://github.com/user-attachments/assets/48fa0729-2df0-4fdb-a089-7b31a62619d6)
* Click Close on the top right corner to return to the bucket dashboard.
* On the bucket dashboard, Click on the Properties tab, Scroll down to static website hosting and click edit.
* Select Enable static website hosting. Scroll down to Index document and type index.html, leave others as default and click Save Changes.
* Still on the Properties tab, Scroll down to Static Website hosting again. This time, the bucket URL would be available. Copy and paste on a new browser tab.![Screenshot (766)](https://github.com/user-attachments/assets/63c7fa6a-3e36-4aa1-80fa-306e51f7b756)
* 

* 

