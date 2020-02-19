##Lex Worker Baas

```
{
  "Persona": "/images/blueprints/Amazon-Lex.png",
  "Organization": "stgvhi",
  "Description": "Handles password reset queries",
  "RequestMapping": {
    "convId": {
      "type": "requestBody",
      "requestBodyPath": "$.inputStream",
      "inputPath": "$.message"
    },
    "userId": {
      "type": "requestBody",
      "requestBodyPath": "$.userId",
      "inputPath": "$.userId"
    }
  },
  "ResponseMapping": {},
  "Type": "aws-sdk",
  "Body": {
    "contentType": "text/plain; charset=utf-8",
    "botAlias": "vhifaqpassword",
    "botName": "vhiFaqPassword",
    "accept": "text/plain; charset=utf-8"
  },
  "Created": 1581951317517,
  "Credentials": "srn:vault::stgvhi:aws-cross-account-role:bb-stgvhi-lex-worker",
  "Tags": [
    "AWS"
  ],
  "Method": "postContent",
  "Endpoint": "LexRuntime",
  "Alias": "vhifaqpasswordresetAWSConnectorName",
  "Updated": 1582040308736,
  "Srn": "srn:baas:eu-1:stgvhi:api-connector:vhifaqpasswordresetawsconnectorname"
}
```
