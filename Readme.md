# Meshcentral 2 router

A node webkit-based application to ease certain application tunneling via [Meshcentral 2](https://github.com/Ylianst/MeshCentral). 
## Dependencies
```
npm install
```

## Configuration

```javascript
{
    "mesh_url": "https://alt.meshcentral.com/",    
	"mesh_username": "username",
	"mesh_password": "password in clear text",
	"mesh_passwordb64": "password encoded in base64",
	"ssh": "C:\\Program Files (x86)\\PuTTY\\putty.exe",
	"sftp": "C:\\Program Files\\FileZilla FTP Client\\filezilla.exe",
	"rdp": "C:\\Windows\\System32\\mstsc.exe",
	"ctm": "C:\\Program Files (x86)\\PuTTY\\putty.exe",
	"ctm_lbl": "Secret tunnel",
	"ctm_args": "-ssh 127.0.0.1 -P lport",
	"use_proxy": false,
	"proxy_type": "socks",
	"proxy_host": "proxy.company.com",
	"proxy_port": "1080"

}

```

Note: If you save *mesh_password* in clear text, it will be saved as *mesh_passwordb64* and *mesh_password* entry will be removed.

## How to run
```
> nw
```

## Custom application tunnelling
Three new JSON entries are added to accomodate addition of user defined custom application tunnelling.

_ctm_: The path of the binary

_ctm_lbl_: Button label

_ctm_arg_: Command line argument to start application

In order to let the user application to connect to randomly listening port created by mc2router, you need to assign the user application destination port to localhost and "lport". String lport will be replaced with the actual port.

_e.g.:_

ssh "-ssh 127.0.0.1 -P lport"

ssms "-S localhost,lport -U username -P password -nosplash"

For more custom application tunneling, new command list JSON is added to add multiple list of application tunneling configurations.

```json
{
    "cmds" :
    [ 
        { "id": 1, "label": "VNC port 5901", "cmdexec": "C:\\Program Files\\TightVNC\\tvnviewer.exe", "cmdargs" : "127.0.0.1::lport","cmdport":"5901"},
        { "id": 2, "label": "VNC port 5902", "cmdexec": "C:\\Program Files\\TightVNC\\tvnviewer.exe", "cmdargs" : "127.0.0.1::lport","cmdport":"5902"},
        { "id": 3, "label": "SSH port 22", "cmdexec": "C:\\Program Files (x86)\\PuTTY\\putty.exe", "cmdargs" : "-ssh 127.0.0.1 -P lport","cmdport":"22"}
    ]
}
```
Each entry need to have:
* label: This will be used as the title
* cmdexec: The path to binary/script to execute
* cmdargs: Commandline argument, please specify the target port of the application as string 'lport'
* cmdport: Target port at the destination device

## Credit
* Ylian St Hilaire
* Piero Fioravanti
* Shafin Jadavji
* Rico Cantrell
* Luca Levati

## Todo
* Add command list editor