---
external help file: PSITPro4_Management.xml
online version: http://go.microsoft.com/fwlink/p/?linkid=293914
schema: 2.0.0
---

# Set-WmiInstance
## SYNOPSIS
Creates or updates an instance of an existing Windows Management Instrumentation (WMI) class.

## SYNTAX

### UNNAMED_PARAMETER_SET_1
```
Set-WmiInstance [-Class] <String> [[-Arguments] <Hashtable>] [-AsJob] [-Authentication] [-Authority <String>]
 [-ComputerName <String[]>] [-Credential <PSCredential>] [-EnableAllPrivileges] [-Impersonation]
 [-Locale <String>] [-Namespace <String>] [-PutType] [-ThrottleLimit <Int32>] [-Confirm] [-WhatIf]
```

### UNNAMED_PARAMETER_SET_2
```
Set-WmiInstance [[-Arguments] <Hashtable>] [-AsJob] [-PutType] [-ThrottleLimit <Int32>]
 -InputObject <ManagementObject> [-Confirm] [-WhatIf]
```

### UNNAMED_PARAMETER_SET_3
```
Set-WmiInstance [[-Arguments] <Hashtable>] [-AsJob] [-Authentication] [-Authority <String>]
 [-ComputerName <String[]>] [-Credential <PSCredential>] [-EnableAllPrivileges] [-Impersonation]
 [-Locale <String>] [-Namespace <String>] [-PutType] [-ThrottleLimit <Int32>] -Path <String> [-Confirm]
 [-WhatIf]
```

### UNNAMED_PARAMETER_SET_4
```
Set-WmiInstance [-AsJob] [-Authentication] [-Authority <String>] [-ComputerName <String[]>]
 [-Credential <PSCredential>] [-EnableAllPrivileges] [-Impersonation] [-Locale <String>] [-Namespace <String>]
 [-PutType] [-ThrottleLimit <Int32>] [-Confirm] [-WhatIf]
```

### UNNAMED_PARAMETER_SET_5
```
Set-WmiInstance [-AsJob] [-Authentication] [-Authority <String>] [-ComputerName <String[]>]
 [-Credential <PSCredential>] [-EnableAllPrivileges] [-Impersonation] [-Locale <String>] [-Namespace <String>]
 [-PutType] [-ThrottleLimit <Int32>] [-Confirm] [-WhatIf]
```

### UNNAMED_PARAMETER_SET_6
```
Set-WmiInstance [-AsJob] [-Authentication] [-Authority <String>] [-ComputerName <String[]>]
 [-Credential <PSCredential>] [-EnableAllPrivileges] [-Impersonation] [-Locale <String>] [-Namespace <String>]
 [-PutType] [-ThrottleLimit <Int32>] [-Confirm] [-WhatIf]
```

## DESCRIPTION
The Set-WmiInstance cmdlet creates or updates an instance of an existing WMI class.
The created or updated instance is written to the WMI repository.

New CIM cmdlets, introduced Windows PowerShell 3.0, perform the same tasks as the WMI cmdlets.
The CIM cmdlets comply with WS-Management (WSMan) standards and with the Common Information Model (CIM) standard, which enables the cmdlets to use the same techniques to manage Windows computers and those running other operating systems.
Instead of using Set-WmiInstance, consider using the Set-CimInstancehttp://go.microsoft.com/fwlink/?LinkId=227962 or New-CimInstancehttp://go.microsoft.com/fwlink/?LinkId=227963 cmdlets.

## EXAMPLES

### -------------------------- EXAMPLE 1 --------------------------
```
PS C:\>Set-WMIInstance -class Win32_WMISetting -argument @{LoggingLevel=2}

__GENUS                        : 2
__CLASS                        : Win32_WMISetting
__SUPERCLASS                   : CIM_Setting
__DYNASTY                      : CIM_Setting
__RELPATH                      : Win32_WMISetting=@
__PROPERTY_COUNT               : 27
__DERIVATION                   : {CIM_Setting}
__SERVER                       : SYSTEM01
__NAMESPACE                    : root\cimv2
__PATH                         : \\SYSTEM01\root\cimv2:Win32_WMISetting=@
ASPScriptDefaultNamespace      : \\root\cimv2
ASPScriptEnabled               : False
AutorecoverMofs                : {%windir%\system32\wbem\cimwin32.mof, %windir%\system32\wbem\ncprov.mof, %windir%\syst
em32\wbem\wmipcima.mof, %windir%\system32\wbem\secrcw32.mof...}
AutoStartWin9X                 :
BackupInterval                 :
BackupLastTime                 :
BuildVersion                   : 6001.18000
Caption                        :
DatabaseDirectory              : C:\Windows\system32\wbem\repository
DatabaseMaxSize                :
Description                    :
EnableAnonWin9xConnections     :
EnableEvents                   : False
EnableStartupHeapPreallocation : False
HighThresholdOnClientObjects   :
HighThresholdOnEvents          : 20000000
InstallationDirectory          : C:\Windows\system32\wbem
LastStartupHeapPreallocation   :
LoggingDirectory               : C:\Windows\system32\wbem\Logs\
LoggingLevel                   : 2
LowThresholdOnClientObjects    :
LowThresholdOnEvents           : 10000000
MaxLogFileSize                 : 65536
MaxWaitOnClientObjects         :
MaxWaitOnEvents                : 2000
MofSelfInstallDirectory        :
SettingID                      :
```

This command sets the WMI logging level to 2.
The command passes the property to be set and the value (together considered a value pair) in the argument parameter.
The parameter takes a hash table that is defined by the @{property = value} construction.
The class information that is returned reflects the new value.

### -------------------------- EXAMPLE 2 --------------------------
```
PS C:\>set-wmiinstance -class win32_environment -argument @{Name="testvar";VariableValue="testvalue";UserName="<SYSTEM>"}

__GENUS          : 2
__CLASS          : Win32_Environment
__SUPERCLASS     : CIM_SystemResource
__DYNASTY        : CIM_ManagedSystemElement
__RELPATH        : Win32_Environment.Name="testvar",UserName="<SYSTEM>"
__PROPERTY_COUNT : 8
__DERIVATION     : {CIM_SystemResource, CIM_LogicalElement, CIM_ManagedSystemElement}
__SERVER         : SYSTEM01
__NAMESPACE      : root\cimv2
__PATH           : \\SYSTEM01\root\cimv2:Win32_Environment.Name="testvar",UserName="<SYSTEM>"
Caption          : <SYSTEM>\testvar
Description      : <SYSTEM>\testvar
InstallDate      :
Name             : testvar
Status           : OK
SystemVariable   : True
UserName         : <SYSTEM>
VariableValue    : testvalue
```

This command creates the testvar environment variable that has the value "testvalue".
It does this by creating a new instance of the Win32_Environment WMI class.
Note that this operation requires appropriate credentials and that you may need to restart Windows PowerShell to see the new environment variable.

### -------------------------- EXAMPLE 3 --------------------------
```
PS C:\>Set-WMIInstance -class Win32_WMISetting -argument @{LoggingLevel=2} -computername system01, system02, system03

__GENUS                        : 2
__CLASS                        : Win32_WMISetting
__SUPERCLASS                   : CIM_Setting
__DYNASTY                      : CIM_Setting
__RELPATH                      : Win32_WMISetting=@
__PROPERTY_COUNT               : 27
__DERIVATION                   : {CIM_Setting}
__SERVER                       : SYSTEM01
__NAMESPACE                    : root\cimv2
__PATH                         : \\SYSTEM01\root\cimv2:Win32_WMISetting=@
ASPScriptDefaultNamespace      : \\root\cimv2
ASPScriptEnabled               : False
AutorecoverMofs                : {%windir%\system32\wbem\cimwin32.mof, %windir%\system32\wbem\ncprov.mof, %windir%\syst
em32\wbem\wmipcima.mof, %windir%\system32\wbem\secrcw32.mof...}
AutoStartWin9X                 :
BackupInterval                 :
BackupLastTime                 :
BuildVersion                   : 6001.18000
Caption                        :
DatabaseDirectory              : C:\Windows\system32\wbem\repository
DatabaseMaxSize                :
Description                    :
EnableAnonWin9xConnections     :
EnableEvents                   : False
EnableStartupHeapPreallocation : False
HighThresholdOnClientObjects   :
HighThresholdOnEvents          : 20000000
InstallationDirectory          : C:\Windows\system32\wbem
LastStartupHeapPreallocation   :
LoggingDirectory               : C:\Windows\system32\wbem\Logs\
LoggingLevel                   : 2
LowThresholdOnClientObjects    :
LowThresholdOnEvents           : 10000000
MaxLogFileSize                 : 65536
MaxWaitOnClientObjects         :
MaxWaitOnEvents                : 2000
MofSelfInstallDirectory        :
SettingID                      :
...
```

This command sets the WMI logging level to 2.
The command passes the property to be set and the value (together considered a value pair) in the argument parameter.
The parameter takes a hash table that is defined by the @{property = value} construction.
The returned class information reflects the new value.

## PARAMETERS

### -Arguments
Specifies the name of the property to be changed and the new value for that property.
The name and value must be  in a name-value pair.
The name-value pair is passed on the command-line  as a hash table.
For example:

-argument @{Setting1=1; Setting2=5; Setting3="test"}.

```yaml
Type: Hashtable
Parameter Sets: UNNAMED_PARAMETER_SET_1, UNNAMED_PARAMETER_SET_2, UNNAMED_PARAMETER_SET_3
Aliases: Args,Property

Required: False
Position: 3
Default value: 
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsJob
Runs the command as a background job.
Use this parameter to run commands that take a long time to finish.

When you use the AsJob parameter, the command returns an object that represents the background job and then displays the command prompt.
You can continue to work in the session while the job finishes.
If Set-WmiObject is used against a remote computer, the job is created on the local computer, and the results from remote computers are automatically returned to the local computer.
To manage the job, use the cmdlets that contain the Job noun (the Job cmdlets).
To get the job results, use the Receive-Job cmdlet.

Note: To use this parameter with remote computers, the local and remote computers must be configured for remoting.
Additionally, you must start Windows PowerShell by using the "Run as administrator" option in Windows Vista and later versions of Windows,.
For more information, see about_Remote_Requirements.

For more information about Windows PowerShell background jobs, see  about_Jobs and about_Remote_Jobs.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authentication
Specifies the authentication level to be used with the WMI connection.
Valid values are:

-1: Unchanged

0: Default

1: None (No authentication in performed.)

2: Connect (Authentication is performed only when the client establishes a relationship with the application.)

3: Call (Authentication is performed only at the beginning of each call when the application receives the request.)

4: Packet (Authentication is performed on all the data that is received from the client.)

5: PacketIntegrity (All the data that is transferred between the client  and the application is authenticated and verified.)

6: PacketPrivacy (The properties of the other authentication levels are used, and all the data is encrypted.)

```yaml
Type: SwitchParameter
Parameter Sets: UNNAMED_PARAMETER_SET_1, UNNAMED_PARAMETER_SET_3, UNNAMED_PARAMETER_SET_4, UNNAMED_PARAMETER_SET_5, UNNAMED_PARAMETER_SET_6
Aliases: 
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authority
Specifies the authority to use to authenticate the WMI connection.
You can specify standard NTLM or Kerberos authentication.
To use NTLM, set the authority setting to ntlmdomain:\<DomainName\>, where \<DomainName\> identifies a valid NTLM domain name.
To use Kerberos, specify kerberos:\<DomainName\>\\\<ServerName\>".
You cannot include the authority setting when you connect to the local computer.

```yaml
Type: String
Parameter Sets: UNNAMED_PARAMETER_SET_1, UNNAMED_PARAMETER_SET_3, UNNAMED_PARAMETER_SET_4, UNNAMED_PARAMETER_SET_5, UNNAMED_PARAMETER_SET_6
Aliases: 

Required: False
Position: Named
Default value: 
Accept pipeline input: False
Accept wildcard characters: False
```

### -Class
Specifies the name of a WMI class.

```yaml
Type: String
Parameter Sets: UNNAMED_PARAMETER_SET_1
Aliases: 

Required: True
Position: 1
Default value: 
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName
Runs the command on the specified computers.
The default is the local computer.

Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more computers.
To specify the local computer, type the computer name, a dot (.), or "localhost".

This parameter does not rely on Windows PowerShell remoting.
You can use the ComputerName parameter even if your computer is not configured to run remote commands.

```yaml
Type: String[]
Parameter Sets: UNNAMED_PARAMETER_SET_1, UNNAMED_PARAMETER_SET_3, UNNAMED_PARAMETER_SET_4, UNNAMED_PARAMETER_SET_5, UNNAMED_PARAMETER_SET_6
Aliases: Cn

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential
Specifies a user account that has permission to perform this action.
The default is the current user.
Type a user name, such as "User01", "Domain01\User01", or User@Contoso.com.
Or, enter a PSCredential object, such as an object that is returned by the Get-Credential cmdlet.
When you type a user name, you will be prompted for a password.

```yaml
Type: PSCredential
Parameter Sets: UNNAMED_PARAMETER_SET_1, UNNAMED_PARAMETER_SET_3, UNNAMED_PARAMETER_SET_4, UNNAMED_PARAMETER_SET_5, UNNAMED_PARAMETER_SET_6
Aliases: 

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableAllPrivileges
Enables all the privileges of the current user before the command makes the WMI call .

```yaml
Type: SwitchParameter
Parameter Sets: UNNAMED_PARAMETER_SET_1, UNNAMED_PARAMETER_SET_3, UNNAMED_PARAMETER_SET_4, UNNAMED_PARAMETER_SET_5, UNNAMED_PARAMETER_SET_6
Aliases: 

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Impersonation
Specifies the impersonation level to use.
Valid values are:

0: Default (Reads the local registry for the default impersonation level, which is usually set to "3: Impersonate".)

1: Anonymous (Hides the credentials of the caller.)

2: Identify (Allows objects to query the credentials of the caller.)

3: Impersonate (Allows objects to use the credentials of the caller.)

4: Delegate (Allows objects to permit other objects to use the credentials of the caller.)

```yaml
Type: SwitchParameter
Parameter Sets: UNNAMED_PARAMETER_SET_1, UNNAMED_PARAMETER_SET_3, UNNAMED_PARAMETER_SET_4, UNNAMED_PARAMETER_SET_5, UNNAMED_PARAMETER_SET_6
Aliases: 
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
Specifies a ManagementObject object to use as input.
When this parameter is used, all other parameters ,except the Arguments parameter, are ignored.

```yaml
Type: ManagementObject
Parameter Sets: UNNAMED_PARAMETER_SET_2
Aliases: 

Required: True
Position: Named
Default value: 
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Locale
Specifies the preferred locale for WMI objects.
The Locale parameter is specified in an array in the MS_\<LCID\> format in the preferred order.

```yaml
Type: String
Parameter Sets: UNNAMED_PARAMETER_SET_1, UNNAMED_PARAMETER_SET_3, UNNAMED_PARAMETER_SET_4, UNNAMED_PARAMETER_SET_5, UNNAMED_PARAMETER_SET_6
Aliases: 

Required: False
Position: Named
Default value: 
Accept pipeline input: False
Accept wildcard characters: False
```

### -Namespace
When used with the Class parameter, this parameter specifies the WMI repository namespace where the referenced WMI class is located.

```yaml
Type: String
Parameter Sets: UNNAMED_PARAMETER_SET_1, UNNAMED_PARAMETER_SET_3, UNNAMED_PARAMETER_SET_4, UNNAMED_PARAMETER_SET_5, UNNAMED_PARAMETER_SET_6
Aliases: NS

Required: False
Position: Named
Default value: 
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path
Specifies a WMI object path to the instance that you want to create or update.

```yaml
Type: String
Parameter Sets: UNNAMED_PARAMETER_SET_3
Aliases: 

Required: True
Position: Named
Default value: 
Accept pipeline input: False
Accept wildcard characters: False
```

### -PutType
Indicates whether the WMI instance should be created or updated.
Valid values are:

UpdateOnly: Updates an existing WMI instance.

CreateOnly: Creates a new WMI instance.

UpdateOrCreate: Updates the WMI instance if it exists or creates a new instance if an instance does not exist.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 
Accepted values: None, UpdateOnly, CreateOnly, UpdateOrCreate

Required: False
Position: Named
Default value: 
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit
Allows the user to specify a throttling value for the number of WMI operations that can be executed simultaneously.
This parameter is used together with the AsJob parameter.
The throttle limit applies only to the current command, not to the session or to the computer.

```yaml
Type: Int32
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: 
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm
Prompts you for confirmation before running the cmdlet.Prompts you for confirmation before running the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
Shows what would happen if the cmdlet runs.
The cmdlet is not run.Shows what would happen if the cmdlet runs.
The cmdlet is not run.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

## INPUTS

### None
This cmdlet does not accept input.

## OUTPUTS

### None
This cmdlet does not generate output.

## NOTES

## RELATED LINKS

[Get-WSManInstance](http://technet.microsoft.com/library/hh849864.aspx)

[Invoke-WSManAction](http://technet.microsoft.com/library/hh849865.aspx)

[New-WSManInstance](http://technet.microsoft.com/library/hh849866.aspx)

[Remove-WSManInstance](http://technet.microsoft.com/library/hh849870.aspx)

[Get-WmiObject](Get-WmiObject.md)

[Invoke-WmiMethod](Invoke-WmiMethod.md)

[Remove-WmiObject](Remove-WmiObject.md)
