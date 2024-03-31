# 2fa-cli
A small CLI to manage your 2FA tokens and secrets. It comes with very basic encryption, a TOTP generator, automatic copy-to-clipboard, and the ability to manage up to 999 secrets.

# Installation
As of right now, I have decided not to use any package managers. This may come at a later date. For now, the CLI will have to manually be added to your PATH.

###Dependencies:
* Python 3.10 or higher
* pip 22.0 or higher

### Step 1:  
Click the green 'Code' button and select 'download ZIP'  

### Step 2:  
Extract the archive  

### Step 3:  
Open the archive in your terminal. Run `pip install -r requirements.txt`  

### Step 4:  
Linux & Mac: Drop the file "2fa" into your $PATH (that is ANY directory that is returned from `echo $PATH`. /usr/bin recommended)  
Windows: You may need to create a new PATH entry. You can do so by installing PowerToys. Navigate to: Environment Variables > User > Path > Edit.  Add a `;` (the separator), then write down the ABSOLUTE path to the 2fa file (which can be anywhere). You must then reboot for the changes to take effect.

### Step 5:  
Run 2fa -h anywhere to confirm you've installed the package correctly.

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

# Configuration
At the moment, I have not yet implemented a configuration file. But at the beginning of the 2fa file, there are a few keys you can change.

| Key | Type | Description |
| -- | -- | -- |
| 2fa_dir | string | What dir the .2fa file will go in. ! If you already have a .2fa file, you will need to migrate it manually.  Default: ~|
