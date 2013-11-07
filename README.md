Transfer protocol specification
===============================

## General notes
### Variables
Elements like `{ID}` represents variables that will be replaced at runtime.


##Command

### GET /server   action : qrCode
Return QR Code

### GET /files
Return list of files on the server

### GET /server   action : statut
Return the status of the server
(name, localisation)

### POST /files   action : upload
Post(idFile, serverReceiver)
Post the file from server A to B
Return transfer status (Success or failed)

### POST /files   action : receive
Post(File) 
Return transfer status (Success or failed)

##Definition of a specific command

### Get QR Code
Conctent of the qr code
{Name};{IP Address}

### Get List of Files
```xml
<response>
    <files>
      <file>
         {FILE MODEL REPRESENTATION}
      </file>
      <file>
        ...
      </file>
        ...
      </files>
</response>
```

## Model Representation
### File
```xml
    <file>
        <id>1</id>
        <name>Foo</name>
        <path>Bar</path>
    </file>
```

### Server Info 
```xml
    <serverInfo>
        <ipAddress>127.0.0.1</ipAddress>
        <name>Test</name>
        <status>OnLine</status>
        <localisation>Montreal</localisation>
    </serverInfo>
```


