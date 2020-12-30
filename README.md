* Create Bucket
* Remove permission: Disabled with Block all public access, Public Access withACL
* Upload source html to root folder of s3, make public
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::buckket-name/*"
        }
    ]
}
```

* Enable Static Website in S3 (property)
(Optional) Redirect config rule:
```
[
    {
        "Condition": {
            "KeyPrefixEquals": "docs/"
        },
        "Redirect": {
            "ReplaceKeyPrefixWith": "documents/"
        }
    }
]
```
* Create Distribution (Cloudfront), point to S3
