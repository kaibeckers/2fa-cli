# 2fa-cli
A small CLI to manage your 2FA tokens and secrets. It comes with very basic encryption, a TOTP generator, automatic copy-to-clipboard, and the ability to manage up to 999 secrets.

# Installation
As of right now, I have decided not to use any package managers. This may come at a later date. For now, the CLI will have to manually be added to your PATH.

Dependencies:
* Python 3.10 or higher
* pip 22.0 or higher

Step 1:  
&nbsp;&nbsp;&nbsp;&nbsp;Click the green 'Code' button and select 'download ZIP'  

Step 2:  
&nbsp;&nbsp;&nbsp;&nbsp;Extract the archive  

Step 3:  
&nbsp;&nbsp;&nbsp;&nbsp;Open the archive in your terminal. Run `pip install -r requirements.txt`  

Step 4:  
&nbsp;&nbsp;&nbsp;&nbsp;Linux & Mac: Drop the file "2fa" into your $PATH (that is ANY directory that is returned from `echo $PATH`. /usr/bin recommended)  
&nbsp;&nbsp;&nbsp;&nbsp;Windows: You may need to create a new PATH entry. You can do so by installing PowerToys. Navigate to: Environment Variables > User > 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Path > Edit.  Add a `;` (the separator), then write down the ABSOLUTE path to the 2fa file (which can be anywhere). Then reboot.  

Step 4:  
&nbsp;&nbsp;&nbsp;&nbsp;Run 2fa -h anywhere to confirm you've installed the package correctly.

# Usage
### 2fa {get, ls, add, del} [-h, --help]
Entry point. Does nothing without a subcommand or flag.

| Argument      | Description   |
| ------------- | ------------- |
| get           | Retrieves a TOTP token for the current time  |
| ls            | List all 'secret' identifiers  |
| add           | Add a new secret  |
| delete        | Delete a secret  |
| -h, --help    | Help  |

Example: 
```
2fa -h
```

### 2fa get [-c, --copy] [-h,--help] name
Retrieve a TOTP *token* for the current time.
| Argument      | Type  | Description   |
| ------------- | ----- | ------------- |
| name          | String  | What secret to use to generate the token |
| -c, --copy    | Toggle  | Determines whether code is copied to clipboard : default: False |
| -h, --help    | Toggle  | Help / Command Docs |

Example: 
```
2fa get discord -c
```

### 2fa ls [-h, --help]
Lists all 'secret' identifiers.
| Argument      | Type  | Description   |
| ------------- | ----- | ------------- |
| -h, --help    | Toggle  | Help / Command Docs |

Example: 
```
2fa ls
```
Example in combination with grep:
```
2fa ls | grep 'discord'
```

### 2fa add [-h, --help] name secret
Add a new secret.
| Argument      | Type  | Description   |
| ------------- | ----- | ------------- |
| name          | String  | What secret to use to generate the token |
| secret        | String  | The secret provided by an external service.|
| -h, --help    | Toggle  | Help / Command Docs |

Example: (not a real key)
```
2fa add discord SRSHY6GPEHPU0ZYW 
```

### 2fa delete [-h, --help] name
Deletes a secret.
| Argument      | Type  | Description   |
| ------------- | ----- | ------------- |
| name          | String  | What secret to delete [by identifier] |
| -h, --help    | Toggle  | Help / Command Docs |

```
2fa delete discord
```

# .2fa file
This script will create a small 2FA file in your home. Your secrets are stored here, in an encrypted form.
