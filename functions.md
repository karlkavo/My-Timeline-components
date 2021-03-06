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

validator

```
const transactionIdRegex = /\d{8}/;
const txid = msg.payload.user.message.match(transactionIdRegex);

if (txid){
    msg.payload.user.TransactionId = txid[0];
    return msg;
}
return [null,msg];
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
Counter flow
```
[{"id":"27a37a59.54e126","type":"dialogue","z":"2b92a578.58c9ea","name":"","message":"You've hit the limit, you hit $num","messageType":"str","displayTimer":1.5,"enableDisplay":false,"x":1240,"y":200,"wires":[[]]},{"id":"15ef18d0.bc2897","type":"function","z":"2b92a578.58c9ea","name":"counter ++","func":"msg.payload.user.counter = msg.payload.user.counter +1;\nreturn msg;","outputs":1,"noerr":0,"x":610,"y":300,"wires":[["65d5642f.47c35c"]]},{"id":"3e9a3c1a.6df514","type":"function","z":"2b92a578.58c9ea","name":"counter","func":"msg.payload.user.counter = 0;\nreturn msg;","outputs":1,"noerr":0,"x":140,"y":300,"wires":[["c6fdd737.61b138"]]},{"id":"b512241.3cd51d8","type":"switch","z":"2b92a578.58c9ea","name":"","property":"payload.user.counter","propertyType":"msg","rules":[{"t":"eq","v":"3","vt":"num"},{"t":"lt","v":"3","vt":"num"}],"checkall":"true","repair":false,"outputs":2,"x":930,"y":300,"wires":[["580272d3.d2a82c"],["dfe75bd4.78d778"]]},{"id":"dfe75bd4.78d778","type":"link out","z":"2b92a578.58c9ea","name":"counterOut","links":["ad64caf3.f84d48"],"x":1115,"y":420,"wires":[]},{"id":"ad64caf3.f84d48","type":"link in","z":"2b92a578.58c9ea","name":"counterIn","links":["dfe75bd4.78d778"],"x":235,"y":220,"wires":[["c6fdd737.61b138"]]},{"id":"65d5642f.47c35c","type":"dialogue","z":"2b92a578.58c9ea","name":"","message":"payload.user.counter","messageType":"msg","displayTimer":1.5,"enableDisplay":false,"x":760,"y":300,"wires":[["b512241.3cd51d8"]]},{"id":"c6fdd737.61b138","type":"dialogue","z":"2b92a578.58c9ea","name":"","message":"enter something","messageType":"str","displayTimer":1.5,"enableDisplay":false,"x":300,"y":300,"wires":[["124f43e2.df2fcc"]]},{"id":"5f4b72d4.f1237c","type":"start","z":"2b92a578.58c9ea","name":"Start","x":90,"y":180,"wires":[["3e9a3c1a.6df514"]]},{"id":"124f43e2.df2fcc","type":"input","z":"2b92a578.58c9ea","name":"","x":450,"y":300,"wires":[["15ef18d0.bc2897"]]},{"id":"580272d3.d2a82c","type":"change","z":"2b92a578.58c9ea","name":"num","rules":[{"t":"set","p":"payload.user.num","pt":"msg","to":"payload.user.counter","tot":"msg"}],"action":"","property":"","from":"","to":"","reg":false,"x":1070,"y":240,"wires":[["27a37a59.54e126"]]}]
```

Date validation DD/MM/YYY
```
[{"id":"bafa3bbb.9a80a8","type":"function","z":"fa69bba7.7d4fc8","name":"verify DOB format","func":"  const dateString = msg.payload.user.message;\n  \n\n const regex = /(((0|1)[0-9]|2[0-9]|3[0-1])\\/(0[1-9]|1[0-2])\\/((19|20)\\d\\d))$/;\nif (regex.test(dateString)) \n  return msg;\n  \n else\n  return [null, msg];\n    \n\n","outputs":2,"noerr":0,"x":470,"y":520,"wires":[["39e02ad2.056f66"],["ecb3f3fe.fac16"]]},{"id":"1b1d977f.db3eb9","type":"dialogue","z":"fa69bba7.7d4fc8","name":"","message":"enter DOB","messageType":"str","displayTimer":1.5,"enableDisplay":false,"x":100,"y":520,"wires":[["6d270d19.9e6164"]]},{"id":"6d270d19.9e6164","type":"input","z":"fa69bba7.7d4fc8","name":"","x":270,"y":520,"wires":[["bafa3bbb.9a80a8"]]},{"id":"39e02ad2.056f66","type":"dialogue","z":"fa69bba7.7d4fc8","name":"","message":"Valid","messageType":"str","displayTimer":1.5,"enableDisplay":false,"x":720,"y":480,"wires":[[]]},{"id":"ecb3f3fe.fac16","type":"dialogue","z":"fa69bba7.7d4fc8","name":"","message":"Invalid","messageType":"str","displayTimer":1.5,"enableDisplay":false,"x":720,"y":560,"wires":[[]]}]
```

