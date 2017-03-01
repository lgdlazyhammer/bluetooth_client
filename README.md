# bluetooth_client
bluetooth plugin of cordova
# this plugin works together with it's service side plugin https://github.com/lgdlazyhammer/bluetooth_server. two mobile device can connected with eachother and transfer data. before use the plugin, device must be paired with eachother and bluetooth must be set open.

# methods
<b>initialize service, which is necessary before using plugin</b><br></br>
mobile.bluetoothClient.init(function(data){
			},function(error){
			});

<b>start listening for incomming request -- remoteDeviceName is required</b><br></br>
mobile.bluetoothClient.startService(function(data){
},function(error){
},remoteDeviceName);

<b>stop connected socket and return to listening mode</b><br></br>
mobile.bluetoothClient.stopService(function(data){
},function(error){
});

<b>send message to remote device</b><br></br>
var message = document.getElementById("message").value;
mobile.bluetoothClient.sendMessage(function(data){
},function(error){
},message);

<b>get server state constantly after some millis second delay</b><br></br>
<b>return data: 0-initialized, 2-connecting, 3-connected</b><br></br>
mobile.bluetoothClient.startGetServerState(function(data){
},function(error){
},delay);

<b>get remote device sended message constantly after some milli seconds delay</b><br></br>
mobile.bluetoothClient.startGetInputStream(function(data){
},function(error){
},delay);

<b>stop get server state loop</b><br></br>
mobile.bluetoothClient.stopGetServerState();

<b>stop get remote device sended message loop</b><br></br>
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
