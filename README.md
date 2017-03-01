# bluetooth_client
bluetooth plugin of cordova
# this plugin works together with it's service side plugin
# two mobile device can connected with eachother and transfer data
# before use the plugin, device must be paired with eachother and bluetooth must be set open

# initialize service, which is necessary before using plugin
mobile.bluetoothClient.init(function(data){
			},function(error){
			});

# start listening for incomming request -- remoteDeviceName is required
mobile.bluetoothClient.startService(function(data){
},function(error){
},remoteDeviceName);

# stop connected socket and return to listening mode
mobile.bluetoothClient.stopService(function(data){
},function(error){
});

# send message to remote device
var message = document.getElementById("message").value;
mobile.bluetoothClient.sendMessage(function(data){
},function(error){
},message);

# get server state constantly after some millis second delay
# return data: 0-initialized, 2-connecting, 3-connected
mobile.bluetoothClient.startGetServerState(function(data){
},function(error){
},delay);

# get remote device sended message constantly after some milli seconds delay
mobile.bluetoothClient.startGetInputStream(function(data){
},function(error){
},delay);

# stop get server state loop
mobile.bluetoothClient.stopGetServerState();

# stop get remote device sended message loop
mobile.bluetoothClient.stopGetInputStream();



# for example

<b>build the connection</b><br></br>
mobile.bluetoothClient.init(function(data){
			},function(error){
			});
      
mobile.bluetoothClient.startService(function(data){
},function(error){
},"AAA-SSS");

<b>monitor the connection state</b><br></br>
mobile.bluetoothClient.startGetServerState(function(data){
    console.log(data);
},function(error){
},1000);

<b>stop monitor</b><br></br>
mobile.bluetoothClient.stopGetServerState();

<b>get remote message</b><br></br>
mobile.bluetoothClient.startGetInputStream(function(data){
    console.log(data);
},function(error){
},delay);

<b>stop getting remote message</b><br></br>
mobile.bluetoothClient.stopGetInputStream();

<b>send message</b><br></br>
mobile.bluetoothClient.sendMessage(function(data){
},function(error){
},"hello there");

<b>stop connection</b><br></br>
mobile.bluetoothClient.stopService(function(data){
},function(error){
});
