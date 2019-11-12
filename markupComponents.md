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


