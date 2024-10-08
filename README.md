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
* Navigate to ***Amazon Route53*** to purchase a domain name
* Click on ***Registered Domains*** > Register domain > input desired domain name in the Contact Details, for example EbuwaJulia.com, then click search
* Under ***search result***, if chosen domain name is available, click ***Select*** > ***Proceed to checkout*** ![Screenshot (784)](https://github.com/user-attachments/assets/8a72ea77-b673-4d52-81f7-0fdef4279f65)
* Optionally ***Unclick Auto-Renew*** > Click ***Next***
* fill in your contact details.
* Accept terms and conditions and complete order.
* Once the domain name has been created, Navigate to Amazon S3.
* Type S3 in the search bar at the top of the console dashboard and click S3. This leads to the S3 dashboard.![Screenshot (760)](https://github.com/user-attachments/assets/e84f5cf8-a6c9-47ae-8767-04fd2edc3c01)
* On the S3 dashboard, Click ***Create bucket***
* Under General Configurations, Select ***General Purpose*** for Bucket type, input *your domain name*.
* Under Object Ownership, Leave as Default ACLs Disabled(Recommended)
* Under Block Public Access settings for this bucket, ***Uncheck Block all public access***.  ![Screenshot (761)](https://github.com/user-attachments/assets/4ba79009-5460-4351-9a7a-460cc2731db5)
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
* You have successfully deployed a static website. But at this point, the website is yet to reflect the domain website.
**How to Change S3 bucket url to custom Domain name**
* Navigate to ***Route 53***
* Click on ***hosted zones*** > ***Registered domain name***
* Click ***Create record***. This record ensures the S3 url is routed to our domain name
* Under ***Record name***, Enter a subdomain or leave blank to create a record for the root domain
* Under ***Record type***, Select CNAME - Routes traffic to another domain name and to some AWS resources
* For ***Value***, input the S3 bucket endpoint without the ***http://*** prefix
* Leave the ***TTL*** as default 
* Click ***Create records*** ![Screenshot (785)](https://github.com/user-attachments/assets/a13190c7-53bb-46e4-83b2-6e56bb7cf449)
*  Wait a few minutes for the changes to be effected
*  Reload the static website.
*  Voila! the Static website now reflects the custom domain name

**OOPPS!!! one more hurdle, the custom domain is Not Secure!!!**

**How to Secure Custom Domain with TLS and distribute with CloudFront**
* Navigate to ***Cloudfront*** from the search bar
* Click ***New Distribution***
* Under ***Origin Domain***, select the initial s3 bucket url > select ***Use website endpoint***
* Scroll down to ***Default cache behaviour*** > ***viewer*** > Select ***Redirect HTTP to HTTPS***
* Scroll down to ***Settings***, Select your preferred price class
* Under ***Alternative domain name(CNAME)***, input the custom domain name
* Under ***custom SSL Certificate***, if you dont have a certificate, click on ***Request Certificate***(This navigates you to Certificate Manager)
**The steps below are to create a new SSL Certificate.**
  * Select ***Request a public Certificate*** and Click ***Next***
  * Enter custom domain name of S3 bucket under Fully Qualified domain name
  * Under ***Validation method***, Select ***DNS validation***
  * Leave everything else as default and click on ***Request***.
  * Click ***Refresh*** to see the newly created certificate on the list of certificates.
  * Click on the ***Certificate ID*** and under ***Domains***, click on ***Create records*** in Route53 > click ***Create Record***.
  * The above navigates to the ***Certificate status page***.
  * To confirm the DNS has been verified
  * open ***Route 53*** on a new tab
  * navigate to ***hosted zones*** > click on the domain name
  * On the list of records, you should now see the newly created CNAME
  * Back in ***Certificate manager***, wait till status shows Success and the Certificate ID status shows issued. You can keep refreshing till this happens

**Now the Certificate has been issued**
* Go back to ***custom SSL Certificate*** under ***Settings*** under ***Distribution***
* Click ***REfresh*** next to the certificate drop-down box
* Select the newly issued certificate
* Select ***enable security protections***
* Leave everything else to default and Click ***Create Distribution***
* Wait for distribution to be created
* You can go back to distributions dashboard and click refresh button beside the Enable button till the last modified tab changes from Deploying
* While waiting for the distribution to be created, you can go ahead and modify the Domain name provided by Cloudfront.
* Right click and copy the Cloudfront ***Domain name***
* Navigate back to ***Route 53***
* Click on the CNAME created for the S3 endpoint > Click ***Edit Record***
* Change the value from the S3 endpoint to the Copied CloudFront endpoint
* Click ***Save***.
* Go back to the distribution dashboard and keep refreshing till it is deployed.
* After it is deployed, verify the static website endpoint can be accessed using https://custom-domain-name

**If your website renders, Voila!!! you have successfully deployed a secured static website with custom domain and TLS and distributed it using CloudFront**

**You can also try accessing the website using http://custom-domain-name. This should redirect to https://custom-domain-name since it was configured in the settings.**


