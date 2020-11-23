# Different components

### Option Card as Menu

```
<TimelineMessage>
  <OptionCard  subtitle="PLEASE CHOOSE ONE OF THE OPTIONS BELOW "
   preventRetries="true">
    <Option title="OPTION 1" id="1" />
    <Option title="OPTION 2" id="2" />
    <Option title="OPTION 3" id="3" />
    <Option title="View Order Self" id="ViewOrderSelf" url="http://servisbot.com" urlTitle="SERVISBOT" linkOpenTarget="self" />
    <Option title="View Order Tab" id="ViewOrderTab" url="http://servisbot.com" urlTitle="SERVISBOT" linkOpenTarget="tab" />
    <Option title="View Order Messenger" id="ViewOrderMessenger" url="https://lovindublin.com/food" urlTitle="LOVIN FOOD" linkOpenTarget="messenger" />
  </OptionCard>
</TimelineMessage>
```

![alt text](https://i.ibb.co/xmWwVw8/cardlist.png)

### Button Prompt

```
<TimelineMessage>
  <ButtonPromptContainer interactionType="event" preventRetries="true">
    <ButtonPrompt label="Yes" id="0"/>
    <ButtonPrompt label="No" id="1"/>
  </ButtonPromptContainer>
</TimelineMessage>
```

![alt text](https://i.ibb.co/MVP5W5P/Screenshot-2019-11-12-at-14-09-29.png)

### Suggestion Prompt

```
<TimelineMessage minimumDisplayTime='3'>
  <SuggestionPrompt>
    <Option title=' Amount due?' id='1' />
    <Option title='next payment due date?' id='2' />
    <Option title='Check Account Status' id='3' />
  </SuggestionPrompt>
</TimelineMessage>
```

### Selectable list

```
<TimelineMessage>
<List title='Try one of the below' selectable='true' preventRetries='true'>
   <Item title='How much is due' id='1'/>
   <Item title='When is the next payment due' id='2'/>
   <Item title='What is the Account Status' id='3'/>
   <Item title='What is eft' id='4'/>
   <Item title='How to enroll in eft' id='5'/>
</List>
</TimelineMessage>
```

```
<TimelineMessage minimumDisplayTime='3'>
  <TextMsg>Hey there! 👋. I'm your Hanover Insurance Bot! I can help you with your insurance queries.</TextMsg>
  <TextMsg>What can I do for you?</TextMsg>>
</TimelineMessage>
```

```
 <TimelineMessage minimumDisplayTime='2'>
 <TextMsg>
 Customers can also mail in a payment to:
 The Hanover Insurance Company
 PO Box 580045
 Charlotte, NC 28258-0045
 </TextMsg>
 </TimelineMessage>
```

```
 <TimelineMessage>
    <TextMsg> Please fill out and sign the EFT Authorization Form and email it to hanovereft@hanover.com or fax to 508-926-5438</TextMsg>
    <TextMsg>EFT [Form](https://tapuat.allmerica.com/wps/wcm/myconnect/791744004305d8b3b09bf6d0260804a8/112-2141A.pdf?MOD=AJPERES)</TextMsg>
</TimelineMessage>
```

### Date and Time Picker

```
<TimelineMessage>
 <DateTime componentType="dateOnly" />
</TimelineMessage>
```

#### function for recent dates

```
const milisInDay = 86400000;
const date = new Date();
msg.payload.user.tomorrowDate = date.getTime() + milisInDay;
return msg;
```

## Broadcast Error

```
  <TimelineMessage>
    <BroadcastMsg
        style="error"
        title="Something's gone wrong!"
        body="Please provide a first name. Please provide a valid email address. Error uploading image. Please try again."
        displayTime="5"
      />
  </TimelineMessage>
```

## Broadcast Warning

```
<TimelineMessage>
 <BroadcastMsg interactionType="event"
   title="Warning"
   body="Will Liverpool win the Premier League in 2020?"
   style="warning">
     <Option title="YES" id="1" />
     <Option title="No" id="2" />
  </BroadcastMsg>
</TimelineMessage>
```

![alt text](https://i.ibb.co/KjKphwn/Screenshot-2019-11-12-at-15-14-42.png)

## Baas Carousel output

```
<TimelineMessage>
    <List
        title=""
        horizontal="true"
        style="large-icon">
        #foreach( $item in $data )
           <Item
               title="$item.first_name  $item.last_name"
               subtitle="$item.email"
               id="$velocityCount"
               imageUrl="$item.avatar"/>
        #end
    </List>
</TimelineMessage>
```

## Link in message

```
<TimelineMessage  minimumDisplayTime='3'>
    <TextMsg>Your current payment method is **${DescriptionOfPlan}**.
    Please click **[here](https://www.hanover.com/billing/state-specific-plans.html)** for more information.</TextMsg>

</TimelineMessage
```

## Video in a Card Element

```
<TimelineMessage>
    <Card 
        title="Refrigerator: Measure Twice, Deliver Once" 
        imgUrl="https://bb-dump-image-eu.s3-eu-west-1.amazonaws.com/Screenshot+2019-11-28+at+10.34.39.png" 
        selectable="true" 
        url="http://ecdn.liveclicker.net/8079A8/origin/videos/1937/1906068079_1_liveclicker.mp4"
        linkOpenTarget="detail"
        />
</TimelineMessage>
```

## Feedback rating

![alt text](https://i.ibb.co/QXhPv0J/Screenshot-2020-01-28-at-14-32-38.png)

```
<TimelineMessage>
  <List title="How would you rate this service?" selectable="true" preventRetries="true" interactionType="event">
     <Item title="😊 Excellent " id="1"/>
     <Item title="😀 Very Good " id="2"/>
     <Item title="🤨 Fair" id="3"/>
     <Item title="😞 Poor" id="4"/>
  </List>
</TimelineMessage>
```

## Email Validation Switch node
```
[{"id":"8ab73853.f72828","type":"switch","z":"b257ae9f.4ae68","name":"email Validation","property":"payload.user.message","propertyType":"msg","rules":[{"t":"regex","v":"^[\\w-\\.]+@([\\w-]+\\.)+[\\w-]{2,4}$","vt":"str","case":false},{"t":"else"}],"checkall":"true","repair":false,"outputs":2,"x":1260,"y":200,"wires":[["6c151797.dd7c78"],["8cec9b97.2b5958"]]}]
```
## Dat Time picker

```
[{"id":"e4b9d717.2ff5b8","type":"dialogue","z":"c13180eb.e7162","name":"what day?","message":"Pick a day from the calendar when you would like to receive a callback.","messageType":"str","displayTimer":"2.1","enableDisplay":true,"x":325,"y":520,"wires":[["e8b9d182.170c9"]]},{"id":"6477091b.f23ff8","type":"input","z":"c13180eb.e7162","name":"","x":645,"y":600,"wires":[["2d27d918.0f2826"]]},{"id":"4c312f9a.b332a","type":"dialogue","z":"c13180eb.e7162","name":"morning","message":"OK! 👍 We will Schedule Your callback sometime in the morning.","messageType":"str","displayTimer":1.5,"enableDisplay":false,"x":1115,"y":580,"wires":[["b2e7e05.91f9a2"]]},{"id":"e8b9d182.170c9","type":"function","z":"c13180eb.e7162","name":"set date","func":"const milisInDay = 86400000;\nconst date = new Date();\nmsg.payload.user.tomorrowDate = date.getTime() + milisInDay;\nreturn msg;","outputs":1,"noerr":0,"x":315,"y":600,"wires":[["2ce11d11.a681c2"]]},{"id":"2ce11d11.a681c2","type":"markup","z":"c13180eb.e7162","name":"calendar","markup":"<TimelineMessage>\n <Calendar dateTime=\"${tomorrowDate}\"/>\n</TimelineMessage>","markupType":"str","syntax":"markdown","x":455,"y":600,"wires":[["6477091b.f23ff8"]]},{"id":"a4f732c1.ba41b","type":"dialogue","z":"c13180eb.e7162","name":"afternoon","message":"OK! 👍 We will Schedule Your callback sometime in the afternoon.","messageType":"str","displayTimer":1.5,"enableDisplay":false,"x":1115,"y":620,"wires":[["b2e7e05.91f9a2"]]},{"id":"ad97dc4b.55d79","type":"dialogue","z":"c13180eb.e7162","name":"evening","message":"OK! 👍 We will Schedule your callback sometime in the evening.","messageType":"str","displayTimer":1.5,"enableDisplay":false,"x":1115,"y":660,"wires":[["b2e7e05.91f9a2"]]},{"id":"b2e7e05.91f9a2","type":"dialogue","z":"c13180eb.e7162","name":"","message":"Anything else?","messageType":"str","displayTimer":"2","enableDisplay":false,"x":1115,"y":720,"wires":[["36937421.feecfc"]]},{"id":"2d27d918.0f2826","type":"markupInteraction","z":"c13180eb.e7162","name":"","markup":"<TimelineMessage>\n  <Dropdown description=\"Great, what time?\" value=\"Morning\" interactionType=\"event\">\n    <DropdownItem id=\"Morning\" title=\"8-12am (Morning)\" />\n    <DropdownItem id=\"Afternoon\" title=\"12-5pm (Afternoon)\" />\n    <DropdownItem id=\"Evening\" title=\"5-8pm (Evening)\" />\n  </Dropdown>\n</TimelineMessage>","syntax":"markdown","outputs":4,"x":845,"y":600,"wires":[["4c312f9a.b332a"],["a4f732c1.ba41b"],["ad97dc4b.55d79"],["b2e7e05.91f9a2"]]}]
```


