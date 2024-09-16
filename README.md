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
