## Identity and access management (IAM)
1. Core Aws service that helps you control access to **Resources**.
2. Resources are the entities you create in Aws i.e **S3** bucket or object.
3. Users attempts to perform **Actions** on resources i.e **S3**::createBucket
4. Authorization to perform an **Action** depends

## Policy Doc
'''
{
 version:2012-10-17
 statement:[
       {
       sid: Create Function,
       effect: Allow,
       Action: [lambda: Create Function,],
       Resources:"*",
}

'''
