# Meshcentral 2 router

A node webkit-based application to ease certain application tunneling via [Meshcentral 2](https://github.com/Ylianst/MeshCentral). 
## Dependencies
```
npm install ws request socksv5 https-proxy-agent
```

## Configuration

```javascript
{
    "mesh_url": "https://alt.meshcentral.com/",    
	"mesh_username": "usename",
	"mesh_password": "password",
	"ssh": "C:\\Program Files (x86)\\PuTTY\\putty.exe",
	"sftp": "C:\\Program Files\\FileZilla FTP Client\\filezilla.exe",
	"rdp": "C:\\Windows\\System32\\mstsc.exe",
	"ctm": "C:\\Program Files (x86)\\PuTTY\\putty.exe",
	"ctm_lbl": "Secret tunnel",
	"ctm_args": "-ssh 127.0.0.1 -P lport"
	"use_proxy": false,
	"proxy_type": "socks",
	"proxy_host": "proxy.company.com",
	"proxy_port": "1080"

}

```
## How to run
```
> nw
```

## Custom application tunnelling
Three new JSON entry are added to accomodate addition of user defined custom application tunnelling.

_ctm_: The path of the binary

_ctm_lbl_: Button label

_ctm_arg_: Command line argument to start application

In order to let the user application to connect to randomly listening port created by mc2router, you need to assign the user application destination port to localhost and "lport". String lport will be replaced with the actual port.

_e.g.:_

ssh "-ssh 127.0.0.1 -P lport"

ssms "-S localhost,lport -U username -P password -nosplash"

## Credit
* Ylian St Hilaire
* Piero Fioravanti
* Shafin Jadavji
* Rico Cantrell
* Luca Levati
