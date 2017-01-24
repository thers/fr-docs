# Introduction to events system

So you've got a resource and want the server script to communicate with client script and vice versa.

The solution is events system.

Let's assume that you need to send string `ping` from client to server
and we're expecting server to answer `pong` so that client will receive that "message".
It's an essential example of both-ways communication.

Flow diagram of what we want to accomplish:
```
   Server  |  Client
-----------------------
     |<-------"ping"
     |          |
  "pong"------->|
```

Now lets look at the commented code that will do the trick.

### Server
```lua
-- First of all we need to register server event name
-- It's preferrable for you to name it after your resource name
-- So "myResourceName" is, well, your's resource actual name
-- And the "ping" is an actual event name
-- If you will follow this simple rule you will probably never encounter errors when other resource using same event name
RegisterServerEvent("myResourceName:ping")

-- Now we're adding a handler function that will be invoked when server receive such event
-- function arguments may vary as you wish
AddEventHandler("myResourceName:ping", function(message)
  -- Just print the message to the server's console so you can see that event has been received
  print("Received myResourceName:ping event with message: " .. message)
  
  -- Now we need to send "ping" event back to client
  -- Again, number of arguments and arguments itself may vary as you wish
  -- Just remember that first argument for function TriggerClientEvent is always an event name
  TriggerClientEvent("myResourceName:pong", "It's me! Server!");
end)
```

### Client
```lua
-- Like on the server side, we need to register such event
RegisterNetEvent("myResourceName:pong")

-- And add an event handler functionfor that event, same as on the server side :)
AddEventHandler("myResourceName:pong", function(message)
  -- Printing fancy message to the client's log, you can open it in game pressing F8
  Citizen.Trace("Received myResourceName:pong event with message: " .. message)
end)

-- Now we're actually triggering server event "ping"!
-- You really want to do that after registering all event handlers
-- Or chances are that server will response earlier than you add corresponding event handler ;p
TriggerServerEvent("myResourceName:ping", "It's me! Client!")
```
