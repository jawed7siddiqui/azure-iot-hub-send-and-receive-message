# Send Message from Device to Cloud - Azure IoT Hub

## Using REST API

## POST Method

Endpoint:
https://esp32commadiothub.azure-devices.net/devices/device_name/messages/deviceBound?api-version=2020-09-30


### Header

- **Authorization**: sas-token
- **Content-Type**: application/json
- **Content-Encoding**: utf-8

### Body

Send message as raw data:

```json
{
    "data": "Hello Im from device"
}
```
# Generate SAS-Token

Generate SAS-token using the following command:

```bash
# Generate SAS-Token using Azure CLI
az iot hub generate-sas-token --hub-name iothub_name --policy-name iothubowner --duration 3600

# Example sas-token Output:
# SharedAccessSignature sr=iot_hub_name.azure-devices.net&sig=**********&se=1709331345&skn=iothubowner

# Alternatively, generate SAS-Token using any supported programming language (e.g., Node.js, Python, PHP, Java, etc.)

```

# Contact Me
### Feel free to reach out if you have any questions or need further assistance:

Email: jawed7siddiqui@gmail.com
Phone/WhatsApp: +91 9142627909



