---
external help file: PSITPro5_Core.xml
online version: http://go.microsoft.com/fwlink/p/?linkid=289601
schema: 2.0.0
---

# Out-Host
## SYNOPSIS
Sends output to the command line.

## SYNTAX

```
Out-Host [-InputObject <PSObject>] [-Paging]
```

## DESCRIPTION
The Out-Host cmdlet sends output to the Windows PowerShell host for display.
The host displays the output at the command line.
Because Out-Host is the default, you do not have to specify it unless you want to use its parameters to change the display.

## EXAMPLES

### Example 1: Display system processes one page at a time
```
PS C:\>Get-Process | Out-Host -Paging
```

This command displays the processes on the system one page at a time.
It uses the Get-Process cmdlet to get the processes on the system.
The pipeline operator sends the results to Out-Host, which displays them at the console.
The Paging parameter displays one page of data at a time.

The same command format is used for the Help function that is built into Windows PowerShell.
That function gets data from the Get-Help cmdlet and then uses the Paging parameter of Out-Host to display the data one page at a time by using this command format: Get-Help $Args\[0\] | Out-Host -Paging.

### Example 2: Display session history
```
PS C:\>$a = Get-History
PS C:\> Out-Host -InputObject $a
```

The first command uses the Get-History cmdlet to get the session history, and then it stores the history in the $a variable.

The second command uses Out-Host to display the content of the $a variable, and it uses the InputObject parameter to specify the variable to Out-Host.

## PARAMETERS

### -InputObject
Specifies the objects that are written to the console.
Enter a variable that contains the objects, or type a command or expression that gets the objects.

```yaml
Type: PSObject
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Paging
Indicates that this cmdlet displays one page of output at a time, and waits for user input before it displays the remaining pages, much like the traditional more command.
By default, all of the output is displayed on a single page.
The page size is determined by the characteristics of the host.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

## INPUTS

### System.Management.Automation.PSObject
You can pipe any object to this cmdlet.

## OUTPUTS

### None
This cmdlet does not generate any output.
However, the host might display the objects that Out-Host sends to it.

## NOTES
The cmdlets that contain the Out verb (the Out cmdlets) do not format objects.
They just render objects and send them to the specified display destination.
If you send an unformatted object to an Out cmdlet, the cmdlet sends it to a formatting cmdlet before rendering it.

The Out cmdlets do not have parameters for names or file paths.
To send data to an Out cmdlet, use a pipeline operator (|) to send the output of a Windows PowerShell command to the cmdlet.
You can also store data in a variable and use the InputObject parameter to pass the data to the cmdlet.
For help, see the examples.

Out-Host sends data, but it does not emit any output objects.
If you pipe the output of Out-Host to the Get-Member cmdlet, Get-Member reports that no objects have been specified.

## RELATED LINKS

[Clear-Host](http://go.microsoft.com/fwlink/?LinkID=225747)

[Out-Default](9848a107-ddc0-40a1-b759-5ac181c1d0cf)

[Out-File](13d09dc8-2398-4d73-9449-1d01eb4e7808)

[Out-Null](75391ca1-066e-402f-92c8-a41095d2854c)

[Out-Printer](22e377d5-b533-442f-987e-b3166bddcd6b)

[Out-String](d4502a29-2351-4580-b456-fb75280fedb4)

[Write-Host](023e670a-cfda-4e8c-af8f-c2b2d9ee5612)
