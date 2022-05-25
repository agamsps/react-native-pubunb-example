# react-native-pubunb-example

1. import pubnub and pubnub-react sdk
2. create pubnub client instance in App.js class using your subscibeKey, publishKey
3. create PubnubProvider component in App.js class and pass pubnub client argument which your created in step2 as an argument to PubnubProvider
4. Create a dynamic channel by entering channelName and userId
5. usePubNub hook in Chatroom class that let you interact with Pubnub.
6. Set userId in pubnub using "pubnub.setUUID(userId)" which is login userId
7. Now subscribe to channel using channelName, while subscribing to channel withPresence represent user online status.
8. Add listener to listen to particular events like message: (used to receive message), file: (used to receive file) etc.

All the functions below are used in ChatRoom file
9. if you want to send message then use  pubnub.publish({
        channel: messageChannel,
        message: messageSend,
        storeInHistory: true
      })
10. In you want to send file (image, video, pdf, doc..etc) then use pubnub.sendFile({
      channel: channelName,
      storeInHistory: true,
    
      file: {
        name: fileName,
        uri: fileUri,
        mimeType: fileType (image, video.. etc ),
      },
     })
11. When you send message other user will receive that message using listener that is in point 8.
12. To show message in ui use react-native-gifted-chat sdk 
13. To fetch previous message history of particular channel use       
         pubnub.fetchMessages({
          channels: [channelName],
          count: 15,
          includeMessageType: true,
          start: start, 
          includeMeta: true,
          includeUUID: true
        },
        async (status, response) => {
            }
            )

    start represent to startTimeToken in nano millisec, if you send start then it will retrieve messages upto startTimeToken