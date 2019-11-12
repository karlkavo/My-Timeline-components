

## Phone Number validator
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

##
Random Number
```
    const min=0; 
    const max=3; 
    
    const random =Math.floor(Math.random() * (max - min)) + min;
    
    msg.payload.random = random;
return msg;
```

