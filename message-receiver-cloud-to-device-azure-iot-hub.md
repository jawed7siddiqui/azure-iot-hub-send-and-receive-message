# Azure IoT Hub Cloud-to-Device (C2D) Communication - Node.js Example

## Install Dependencies

```bash
npm install azure-iot-device azure-iot-device-mqtt
```
# NodeJS code Example

```bash
# receiver.js

const Protocol = require('azure-iot-device-mqtt').Mqtt;
const Client = require('azure-iot-device').Client;
const Message = require('azure-iot-device').Message;

// Connection string for your device, use the device primary key obtained from Azure portal , iot_hub_name>device>device_name
const iotHubConnectionString = 'HostName=iot_hub_name.azure-devices.net;DeviceId=device_name;SharedAccessKey=***********';

// Create a client instance
const client = Client.fromConnectionString(iotHubConnectionString, Protocol);

// Set up the message handler
client.on('message', function (msg) {
    console.log('Received message: ' + msg.getData().toString('utf-8'));

    // Complete the message (remove it from the queue)
    client.complete(msg, function (err) {
        if (err) {
            console.error('Error completing message: ' + err.toString());
        } else {
            console.log('Message completed');
        }
    });
});

// Set up the error handler
client.on('error', function (err) {
    console.error('Error: ' + err.toString());
});

// Open the connection to the Azure IoT Hub
client.open(function (err) {
    if (err) {
        console.error('Could not connect: ' + err.toString());
    } else {
        console.log('Client connected to Azure IoT Hub');

        // Set up additional initialization or processing here

        // Set up a loop to keep the script running
        setInterval(function () {
            // Your main script logic here
        }, 5000); // Repeat every 5 seconds (adjust as needed)
    }
});

// Handle process termination
process.on('SIGINT', function () {
    console.log('Closing connection to Azure IoT Hub');
    client.close(function () {
        console.log('Connection closed');
        process.exit(0);
    });
});


```

# Contact Me
### Feel free to reach out if you have any questions or need further assistance:

Email: jawed7siddiqui@gmail.com
Phone/WhatsApp: +91 9142627909
