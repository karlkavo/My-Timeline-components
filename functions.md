## Useful Functions

Phone Number validator

```
msg.payload.user.customerPhone = msg.payload.user.message.split(' ').map(w => w.slice(0,1).toUpperCase()+ w.slice(1)).join(' ')
function validatecustomerPhone(CP) {
   var re = /^[=+\s]*(?:[0-9][=+\s]*){8,}$/;
     return re.test(CP.toLowerCase());
}
var CP = msg.payload.user.message
var isValid = validatecustomerPhone(CP)
if(isValid) {
  msg.payload.user.CP = CP
  return [null,msg];
}
return msg;
```

Random Number

```
    const min=0;
    const max=3;

    const random =Math.floor(Math.random() * (max - min)) + min;

    msg.payload.random = random;
return msg;
```

Save Name

```
const name = msg.payload.user.message.split(/ (.+)/);
msg.payload.user.firstName = name[0];
msg.payload.user.lastName = name[1] || "";
return msg;
```

Sleep Timer

```
setTimeout(()=>{
    node.send(msg);
}, 2000)
```

Switch

```
const docType = msg.event.event.contents.data.conversationState.docUploaded
switch(docType) {
    case 'Prop_Driv_Lic_Status':
        msg.thankYouResponse = 'Thank you for uploading your Driving Licence'
        break;
    case 'Proof_Of_NCB_Status':
        msg.thankYouResponse = 'Thank you for uploading your Proof of NCB document'
        break;
    case 'NCT_Status':
        msg.thankYouResponse = 'Thank you for uploading your NCT'
        break;
    case 'Nam_Driv_Lic_Status':
        msg.thankYouResponse = 'Thank you for uploading your Named Driver Licence'
        break;
    case 'Ltr_Of_Driv_Exp_Status':
        msg.thankYouResponse = 'Thank you for uploading your Proof of Driver Experience'
        break;
    case 'Finance_Form_Status':
        msg.thankYouResponse = 'Thank you for uploading your Bank Details'
        break;
    case 'Sign_Prop_Status':
        msg.thankYouResponse = 'Thank you for uploading your Signed Proposal Form'
        break;
    case 'Gap_In_Cov_Ltr_Status':
        msg.thankYouResponse = 'Thank you for uploading your Gap In Cover Letter'
        break;
    case 'PPS_Num_Status':
        msg.thankYouResponse = 'Thank you for uploading your Proof of PPSN'
        break;
    case 'Irish_Reg_Status':
        msg.thankYouResponse = 'Thank you for providing your Irish Registration'
        break;
    case 'Engineers_Rpt_Status':
        msg.thankYouResponse = 'Thank you for uploading your Engineers Report'
        break;
    default:
        msg.thankYouResponse = 'Thank you for uploading your Document'
}
```

Format Phone Number for Voice

```
const convertingFunction = function(phoneVoice) {
  const mapNumbers = {
    0: 'zero',
    1: 'one',
    2: 'two',
    3: 'three',
    4: 'four',
    5: 'five',
    6: 'six',
    7: 'seven',
    8: 'eight',
    9: 'nine',
  };
  let result = phoneVoice;
  Object.keys(mapNumbers).forEach((number) => {
    let voiceNumber = mapNumbers[number];
    result = result.split(voiceNumber).join(number);
  });
  result = result.split(' ').join('');
  return result;
}
msg.payload.user.phoneNumber = convertingFunction(msg.payload.user.message);
return msg;
```
Birth Date Check

```
function convertTimestamp(timestamp) {
    if (!timestamp) {
        return {}
    }

    let re = /\d+/
    let parsed = timestamp.match(re);
    let unix_timestamp = parseInt(parsed[0])

    let date = new Date(unix_timestamp)
    let day = date.getUTCDate()
    let month = date.getUTCMonth() + 1

    return {
        "day": day,
        "month": month
    }
}
const birthDates = convertTimestamp(msg.payload.user.person.BIRTHDATE);
if (birthDates.day.toString() === msg.payload.user.birthDay && birthDates.month.toString() === msg.payload.user.birthMonth) {
    return [msg, null];
}
return [null, msg];
```

Post code mapper

```
// intentionally lowercased to ease handling by voice
const postCodesMap = {
  "8266165":	"t2n1m5",
  "8276997":	"t2p6x7",
  "822234":	    "t2a2d4",
  "8594444":	"t5w4h4",
  "87555972":	"t7l9p2",
  "882181":	    "t8a1t1",
  "89555494":	"t9l4w4",
  "81223882":	"t1b3u3",
  "8533433":	"t5e4d3",
  "828122":	    "t2t1a2",
  "8822215553":	"t8c1l3"
}
msg.postCodesMap = postCodesMap;
return msg;
```

Split Name

```
const name = msg.payload.user.message.split(/ (.+)/);
msg.payload.user.firstName = name[0];
msg.payload.user.lastName = name[1] || "";
return msg;
```

Modifying payload using context

```
msg.payload.userId =  msg.payload.context.userId;
msg.payload.user.name =  msg.payload.context.firstName;
return msg;
```

