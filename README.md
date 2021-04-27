## Setup
1. Download the individual files needed, as well as the `auth.py` file.
2. Set the `LOGIN_TOKEN` in `auth.py` to your IBM Quantum Experience Token. 

## Running Each Script

### auth.py
**What it does**: Sends an API call to authenticate your account.</br>
**Notes**: You must set the **LOGIN_TOKEN** variable to your IBM Quantum Experience Token. 
Other than that, no further action is needed for this file. This file is used in all of the scripts.
If you experience an `AUTHORIZATION_REQUIRED` error or a `401` status code, double check that you have included your valid IBM Quantum Token in this file.

-----

### edit_group.py
**What it does**: Adds or Removes a Group in your Hub</br>
**Parameters**:</br>
&ensp;`<hub>`: Required. The name of your hub.</br>
&ensp;`<action>`: Required. Either 'add' or 'remove'.</br>
&ensp;`<group_name>`: Required. The name of the group being added or removed.</br>
&ensp;`<group_title>`: Optional. Triggered by the `-t` flag. Only required if adding a group. The title of the group being added.</br>
**Usage**:</br>
&ensp;If adding group: `python edit_group.py <hub> add <group_name> -t <group_title>`</br>
&ensp;If removing group: `python edit_group.py <hub> remove <group_name>`</br>

-----

### edit_project.py
**What it does**: Adds or Removes a Project in your Hub</br>
**Parameters**:</br>
&ensp;`<hub>`: Required. The name of your hub.</br>
&ensp;`<group>`: Required. The name of the parent group.</br>
&ensp;`<action>`: Required. Either 'add' or 'remove'.</br>
&ensp;`<project_name>`: Required. The name of the project you are adding or removing.</br>
&ensp;`<project_title>`: Optional. Triggered by the `-t` flag. Only required if adding a project. The title of the project being added.</br>
**Usage**:</br>
&ensp;If adding project: `python edit_project.py <hub> <group> add <project_name> -t <project_title>` </br>
&ensp;If removing project: `python edit_project.py <hub> <group> remove <project_name>`

-----

### edit_users.py
**What it does**: Adds or Removes a user to or from a Project within your Hub</br>
**Parameters**:</br>
&ensp;`<hub>`: Required. The name of your hub.</br>
&ensp;`<group>`: Required. The name of the parent group.</br>
&ensp;`<project>`: Required. The name of the project the the user will be added to or removed from.</br>
&ensp;`<action>`: Required. Either 'add' or 'remove'.</br>
&ensp;`<user_email>`: Required. User being added or removed.</br>
**Usage**:</br>
&ensp;`python edit_users.py <hub> <group> <project> <action> <user_email>`

-----

### get_analytics_for_users.py
**What it does**: Retrieves system usage stats for users on specific backends over a given date range. Creates a .csv file in same directory and stores the results in this file</br>
**Parameters**:</br>
&ensp;`<hub>`: Required. The name of your hub.</br>
**Required Files**:</br>
&ensp;`analytics_data.csv`</br>
This file should be filled out with the following format:
| Start              | End                | User    | Backends                  |
| ------------------ | ------------------ | ------- | ------------------------- |
| `mm-dd-yy` or `''` | `mm-dd-yy` or `''` | `email` | `backend1, backend2, ...` |

This script will return usage stats of each `user` on each backend listed in that row's `backends` column between the `start` and `end` date range. 
If no date is given for `start` or `end`, then it will return usage stats across the Hub's entire existence.
Duplicate `user` entries are not accepted, and only the first instance of that `user` will have analytics returned.
 
**Output**:</br>
&ensp;System usage stats stored in newly created file: `analytics_results.csv`

**Usage**:</br>
&ensp;`python get_analytics_for_users.py <hub>`

