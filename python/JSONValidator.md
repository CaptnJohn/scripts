Script for validating if a JSON file is valid and printing out the status of validation. Also prints out info of what is wrong.

Using the script

> python scriptname.py jsonFileName.json

``` py

import os
import sys
import json

# Takes in a file and loads it with json. Returns true if succeeded.
def validateJSONFile(JSONFile):
    try:
        json.loads(JSONFile.read())
    except ValueError as err:
        print('Invalid JSON": %s', err)
        return False
    return True


if sys.argv[1:]:
    fileArgument = sys.argv[1]
    if os.path.exists(fileArgument):
        JSONFile = open(fileArgument, "r")
        isValid = validateJSONFile(JSONFile)
        JSONFile.close()
        print('JSON valid:', isValid)
    else:
        print(fileArgument + ' file passed was not found:', fileArgument)
else:
    print('Pass in argument with the script for file to check. Example: python JSONValidator.py Test.json')
    
```
