# manifest.xml



```markup
<?xml version="1.0" encoding="UTF-8"?>
<ExtensionManifest Version="6.0" ExtensionBundleId="com.dpe.it" ExtensionBundleVersion="1.0.0" ExtensionBundleName="dpe" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
	<ExtensionList>
		<Extension Id="com.dpe.it" Version="1.0.2" />
	</ExtensionList>
	<ExecutionEnvironment>
		<HostList>
			<Host Name="PPRO" Version="9.0" />
		</HostList>
		<LocaleList>
			<Locale Code="All" />
		</LocaleList>
		<RequiredRuntimeList>
			<RequiredRuntime Name="CSXS" Version="6.0" />
		</RequiredRuntimeList>
	</ExecutionEnvironment>

	<DispatchInfoList>
		<Extension Id="com.dpe.it">
			<DispatchInfo >
				<Resources>
					<MainPath>./node_modules/@pietrop/digital-paper-edit-client/index.html</MainPath>
					<ScriptPath>./jsx/Premiere.jsx</ScriptPath>
					<CEFCommandLine>
						<Parameter>--allow-file-access</Parameter>
						<Parameter>--allow-file-access-from-files</Parameter>
						<Parameter>--enable-nodejs</Parameter>
						<Parameter>--mixed-context</Parameter>
						<Parameter>--enable-media-stream</Parameter>
					</CEFCommandLine>
				</Resources>
				<Lifecycle>
					<AutoVisible>true</AutoVisible>
				</Lifecycle>
				<UI>
					<Type>Panel</Type>
					<Menu>dpe</Menu>
					<Geometry>
						<Size>
							<Height>300</Height>
							<Width>300</Width>
						</Size>
					</Geometry>
				</UI>
			</DispatchInfo>
		</Extension>
	</DispatchInfoList>
</ExtensionManifest>
```

