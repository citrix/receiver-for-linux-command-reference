# Citrix Receiver for Linux 13.5 Command Reference

The tables below list Citrix Receiver for Linux 13.5 command-line parameters. 

!!!tip "Note"
        A list of the parameters can be obtained typing `wfica` or `storebrowse` with 
        the `-?`, `-help`, or `-h` options.

## wfica

You can use a connection file simply by typing its name after `wfica` without any of the following options.

| To 											      | Type                                         |
|---------------------------------------------|----------------------------------------------|
| Specify the custom connection to use from the Connection file. <br/> <br/> **Note:** With the new self-service UI, you cannot set up a custom connection in this way. | `-desc <description>` or `-description <description>` |
| Specify a desktop file used for launch. | `-desktop <filename>` |
| Specify a connection file. | `-file connection <filename>` |
| Set alternative protocol file. This enables the use of an alternative module.ini. | `-protocolfile filename` |
| Set alternative client configuration file. This enables the use of an alternative wfclient.ini. | `-clientfile filename` |
| Display a different name for Citrix Receiver, specified by name, wherever that name appears. The default name is the device name. However, if you use a Sunray device, the default name is derived from the device’s MAC address. This is overridden by the ClientName entry in .ICAClient/wfclient.ini, which is itself overridden by issuing the `-clientname` name command. | `-clientname name` |
| Show this list of parameters. | `-help` |
| Display version information. | `-version` |
| Show error numbers and string. | `-errno` |
| Set the location of Receiver installation files. This is equivalent to setting the ICAROOT environment variable. | `--icaroot directory` |
| Suppress connection dialog boxes. | `-quiet` |
| Enable key logging. | `-keylog` |
| Set session geometry. | `-geometry WxH+X+Y` |
| Set color depth. | `-depth <4 | 8 | 16 | 24 | auto>` |
| Set monitor spanning. | `-span [h][o][a|mon1[,mon2[,mon3,mon4]]]` |
| Use private colormap. | `-private` |
| Use shared colormap. | `-shared` |
| Specify a string to be added to a published application. | `-param string` |
| Specify the UNIX path to be accessed through client drive mapping by a published application. | `-fileparam unixpath` |
| Specify a user name. | `-username username` |
| Specify a disguised password. | `-password password` |
| Specify a clear text password. | `-clearpassword "clear password"` |
| Specify a domain. | `-domain domain` |
| Specify an initial program. | `-program program` |
| Specify a directory for the initial program to use. | `-directory directory` |
| Turn on sound. | `-sound` |
| Turn off sound | `-nosound` |
| Set drive mapping overrides. These are of the form `A$=path`, where **path** can contain an environment variable (for example `A$=$HOME/tmp`). This option must be repeated for each drive to be overridden. For the override to work, there must be an existing mapping, although it need not be enabled. | `-drivemap string` |

!!!tip "Note"

## storebrowse


| Option | Description | Notes |
|----------------------|----------------------------------|----------------------------------|
| `-L`, `--launch` | Specifies the name of the published resource to which you want to connect. This launches a connection to a published resource. The utility then terminates, leaving a successfully connected session. |                                                  |
| `-E`, `--enumerate` | Enumerates the available resources. | By default, the resource name, display name, and folder of the resource are displayed. Additional information can be displayed, by using the `--details` option. |
| `-S`, `--subscribed` | Lists the subscribed resources. | By default, the resource name, display name, and folder of the resource are displayed. Additional information can be displayed using the `--details` option. |
| `-M`, `--details` Use in conjunction with the `-E` or `-S` option. | Selects which attributes of published applications are returned. This option takes an argument that is the sum of the numbers corresponding to the required details: `Publisher(0x1)`, `VideoType(0x2)`, `SoundType(0x4)`, `AppInStartMenu(0x8)`, `AppOnDesktop(0x10)`, `AppIsDesktop(0x20)`, `AppIsDisabled(0x40)`, `WindowType(0x80)`, `WindowScale(0x100)`, `DisplayName(0x200)`, and `AppIsMandatory(0x10000)`. `CreateShortcuts(0x100000)` can be used in conjunction with `-S`, `-s`, and `-u` to create menu entries for subscribed applications. `RemoveShortcuts(0x200000)` can be used with `-S` to delete all menu entries. | Some of these details are not available through storebrowse. If this is the case, the output is 0. Values can also be expressed in decimal as well as hexadecimal (for example, 512 for 0x200). |
| `-v`, `--version` | Writes the version number of `storebrowse` to the standard output. |     |
| `-?`, `-h`, `--help` | Lists the usage for `storebrowse`. | An abbreviated version of this table appears. |
| `-U`, `--username` | Passes the user name to the server. | When used with StoreFront, the site must be configured to support HTTP BasicAuth, otherwise these will be ignored. |
| `-P`, `--password` | Passes the password to the server. | When used with StoreFront, the site must be configured to support HTTP BasicAuth, otherwise these will be ignored. |
| `-D`, `--domain` | Passes the domain to the server. | When used with StoreFront, the site must be configured to support HTTP BasicAuth, otherwise these will be ignored. |
| `-r`, `--icaroot` | Specifies the root directory of the Receiver for Linux installation. | If not specified, the value is determined at run time. |
| `-i`, `--icons` Use in conjunction with the `-E`, or `-S` option. | Fetches desktop or application icons, in PNG format, of the size and depth given by the `best` or `size` argument.<br/> If the `best` argument is used, the best sized icon available on the server is fetched. You can convert this to any size required. The `best` argument is the most efficient for storage and bandwidth, and can simplify scripting. <br/> If the `size` argument is used, an icon is fetched of the specified size and depth. <br/> In both cases, icons are saved in a file for each of the resources that the `–E` or `-S` option returns. | The `best` argument creates an icon of the form **&lt;resource name&gt;.png**. <br/>The `size` argument is of the form **WxB**, where **W** is the width of the icon (all icons are square, so only one value is needed to specify the size), and **B** is the color depth (that is, the number of bits per pixel). **W** is required but **B** is optional. If it is not specified, icons of all available image depths are fetched for that size. The files that are created are named **&lt;resource name&gt;_WxWxB.png**. |
| `-u`, `--unsubscribe` | Unsubscribes the specified resource from the given store. |   |
| `-W [r|R]`, `--reconnect [r|R]` | Reconnects disconnected and active sessions. | `r` reconnects all disconnected sessions for the user. `R` reconnects all active and disconnected sessions. |
| `-WD`, `--disconnect` | Disconnects all sessions. | Only affects sessions to the store specified on the command line. |
| `-l`, `--liststores` | Lists the known StoreFront stores, that is those that storebrowse can contact. These are the stores registered with the ServiceRecord proxy. Also lists Program Neighborhood sites. |	|
| `-a`, `--addstore` | Registers a new store, including its gateway and beacon details, with the Service Record daemon. | Returns the full URL of the store. If this fails, an error is reported. |
| `-d`, `--deletestore` | Deregisters a store with the Service Record daemon. | |
| `-c`, `--configselfservice` | Gets and sets the self-service UI settings that are stored in StoreCache.ctx. Takes an argument of the form `<entry[=value]>`. If only entry is present, the setting's current value is printed. If a value is present, it is used to configure the setting. | Example: `storebrowse --configselfservice SharedUserMode=True` <br/> **Important:** Both entry and value are case sensitive. Commands that use this option will fail if the case is different to the documented case of the setting itself (in StoreCache.ctx).|
| `-C`, `--addCR` | Reads the provided Citrix Receiver (CR) file, and prompts the user to add each store. | The output is the same as `-a` but might contain more than one store, separated by newlines. |
## pnabrowse

		The `pnabrowse` utility is deprecated but can still query Program Neighborhood Agent sites that run the Web Interface for lists of servers and published resources, and lets you connect to a published resource. Citrix discourages the use of `pnabrowse` with StoreFront stores; use `storebrowse` instead. `storebrowse` can prompt for credentials from sites and stores. The `-U`, `-P` and `-D` options only work with Program Neighborhood Agent sites. 

| Option  | Description |
|---------|-------------|
| `-S` | List servers, one per line. |
| `-M` | Used in conjunction with `-A`, this selects individual columns of information returned about published applications. It takes an argument (1-1023) which is the sum of the numbers corresponding to the required details: Publisher(1), Video Type(2), Sound Type(4), AppInStartMenu(8), AppOnDesktop(16), AppIsDesktop(32), AppIsDisabled(64), Window Type(128), Window Scale(256), and DisplayName(512). |
| `-f` | Include Citrix XenApp folder names for published applications in the output from option `-A`. |
|---------|-------------|
| `-D` | Specify a domain for authenticating the user to the server running the Web Interface or the server running the Citrix XenApp (Program Neighborhood Agent) Service. |
| `-L` | Specify the name of the published resource to which you want to connect. This invokes Citrix XenApp and launches a connection to a published resource. If you specify both -E and-L, the last option on the command line takes effect. The utility then terminates, possibly leaving a connection open. |
| `-N` | Specify a new password. This option must be used with existing credentials and is valid only when the existing password has expired, as indicated by the exit code 238: E_PASSWORD_EXPIRED. |
| `-WD` | Disconnects all active sessions for the user. |
|---------|-------------|