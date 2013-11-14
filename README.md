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

### POST /files/transfer/
####POST Data
```json
    {
        "file" : "{FILE PATH}",
        "server" : "{SERVER ID}"
    }
```

####Returns
Return transfer status (`200` or `500`)

### POST /polling/
Returns nothing if nothing happened or the text of the notification to show.


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


