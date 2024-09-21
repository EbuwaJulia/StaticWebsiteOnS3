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
* On the S3 dashboard, Click *Create bucket*
* Under General Configurations, Select *General Purpose* for Bucket type, input a *globally unique bucketname*.
* Under Object Ownership, Leave as Default ACLs Disabled(Recommended)
* Under Block Public Access settings for this bucket, *Unselect Block all public access*.  ![Screenshot (761)](https://github.com/user-attachments/assets/4ba79009-5460-4351-9a7a-460cc2731db5)

