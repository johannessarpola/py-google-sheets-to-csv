# What

Retrieves the set sheets and their worksheets from Google Sheets and outputs CSVs with their
data.

# HOWTO

1. Install Python2.7, (included in distribution, not in git) (remember to tick the option to include in PATH if on Windows)
2. Run 'py setup.py develop' from commandline (if you have other python versions installed then it's 'py -2.7 setup py develop'
3. Follow instructions on https://developers.google.com/sheets/quickstart/python on
how to create client_secret.json for a user
    - Notice that the downloaded file needs to be renamed to client_secret.json
4. configure sheet-ids.json to retrieve all the necessary sheets and sheets
    - "SpreadSheet1" : { ... defines the name for the sheet
    - "id":"1pNaDgWk6vrUxLwfA81nPUP06_fLqZCFmlUsrG1Z0RdI" ... defines the id for the sheet
    (instructions on how to get this are on the developers.google.com link above)
    - "Sheets": [ ... inside this worksheets are defined
5. Run SheetsRunnable.py and accept the permission (this nees to be done once)
6. Run SheetsRunnable.py (or schedule) again
7. A folder called out is created and in it are CSV files for the configured sheets

# FAQ

- Python version?
> 2.7 as Goole API client wont work on 3.x, will probably change at some point.
Follow progress here https://github.com/google/google-api-python-client

- Safe?
> Yes, pretty much. If you modify the source code, it's on your own responsibility.

- Do I have to give permission for Google Sheets?
> Yes, how else would it allow to read files

- Will the permission expire at some point?
> Generally they do, but couldn't find specifics. Should be quite simple to regenerate the permission by just removing C:\\Users\\USERNAME\\.credentials\\gsheets.json and rerun.

- Does the application have access to change anything?
> No, it's readonly. Although you still need to take care with client_secret.json
as it's basically your login details but not in clear text format. You can always
revoke access through http://console.developers.google.com/

- I borked JSON structure and everthing fails?
> Redo from original development, take
care that all special characters are closed and commas where they should be.

- Logging?
> yes, main.log in root after first run

- Something else?
> Contact johannes.sarpola@pengon.fi
