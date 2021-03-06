### NurApi Mimimal UWP sample

This folder contains very simple UWP sample for NurApi.

### Requirements
- Windows 10 machine
- Visual Studio 2017 with UWP support
- At least Windows 10 SDK Build 15063

### NurApi for UWP
NurApi UWP is basically same as other C# targets, except transport layers are different.

Documentation: [NurApi UWP Documentation.chm](https://github.com/NordicID/nur_sdk/blob/master/dotnet/docs/NurApi%20UWP%20Documentation.chm)

###### Needed app capabilities
Depending on your needs, you need to enable desired app capabilities in order to connect to nur devices.
For example:
```
<Capabilities>
	<Capability Name="internetClient" />
	<Capability Name="internetClientServer" />
	<Capability Name="privateNetworkClientServer" />
	<DeviceCapability Name="bluetooth" />
	<DeviceCapability Name="serialcommunication">
		<Device Id="any">
			<Function Type="name:serialPort" />
		</Device>
	</DeviceCapability>
</Capabilities>
```

###### UWP async programming
Normally in UWP apps in order to keep your app responsive, async APIs are used.
However, most of the NurApi method are synchronous, thus it is recommended to wrap them inside Task:
```
await Task.Run(async () => {
  try {
    // Call NurApi synchronous funtion here
  } catch (Exception e) {
    // Handle error here
  }
});
```

### Sample content
- Connection handling to single reader.
- Basic tag inventory functionality.
