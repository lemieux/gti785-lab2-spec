Transfer protocol specification
===============================

## General notes
### Variables
Elements like `{ID}` represents variables that will be replaced at runtime.

### Constants
All requests must return a value if the request is processed correctly or return a `404` or a `500` when an error occurs

##Command

### GET /
Return QR Code

### GET /files/
Return list of files on the server

### GET /server/
Return the status of the server
(name, localisation)

### POST /files/

#### POST Data
This call sends a file to the remote server
Return transfer status (Success or failed)

### POST /files/delete/
#### POST Data
```json
    {
        "file" : "{FILE PATH}"
    }
```


### POST /files/transfer/
####POST Data
```json
    {
        "file" : "{FILE PATH}",
        "server" : "{SERVER URL}"
    }
```

####Returns
Return transfer status (`200` or `500`)

### POST /polling/
Returns nothing if nothing happened or the text of the notification to show.
####Returns
A notification.


##Definition of a specific command

### Get QR Code
Content of the QR code
{URL}

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
    <server>
        <url>http://127.0.0.1:8080</url>
        <name>Test</name>
        <localisation>Montreal</localisation>
    </server>
```

### Notification
```xml
    <notification>
        <file>/test.png</file>
        <action>TRANSFER_FAIL</action>
    </notification>
```

#### List of actions possible
- UPLOAD_SUCCESS : upload successful
- UPLOAD_FAIL : upload failed
- TRANSFER_SUCCESS : file transfer succesful
- TRANSFER_FAIL : file transfer failed
- FILE_ADDED :  a new file was added to the server
- FILE_DELETED : a file was deleted
- FILE_DELETE_FAIL : a delete operation failed


