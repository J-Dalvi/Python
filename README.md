# Python

- NOTES: Installing & Verifying Python on Windows
1. Check if Python Is Already Installed- Open Command Prompt and run: python --version or py --version- If installed, version number appears. If not, you'll see an error or Microsoft Store opens.
   
2. Download Python- Visit https://www.python.org/downloads/- Download the recommended Windows installer.
   
3. Install Python- Run the installer.- IMPORTANT: Check "Add Python to PATH".- Click Install Now.

4. Validate Python Installation- Run: python --version- Run: pip --version- Test: python -c "print('Python is working!')"

5. Check if Python & Scripts Are Added to Environment Variables- PATH entries required:
    Python installation directory
    Scripts directory- Open: sysdm.cpl → Advanced → Environment Variables- Check PATH under User or System variables.

- Issue Noted:- I currently cannot Verify PATH entries due to admin rights restriction.
- Workaround: Use Python via full path or reinstall with "Add to PATH" enabled

# Define Scope

What I am building (high level)

I want a Python script that:

- Connects to Outlook
- Reads emails from Inbox (optionally filter by date/sender/subject/unread)
- Saves each mail (and optionally attachments) to a shared folder
- Avoids duplicates + logs what it did

## Chunk 0 — Prep: confirm my approach & prerequisites

### 0.1 Confirm We are on Windows + Outlook desktop app
This approach requires:

- Windows
- Outlook desktop installed and configured
- I can open Inbox normally

### 0.2 Install required Python package
In VS Code terminal:

```pip install pywin32```

> You can keep BeautifulSoup/requests installed, but they aren’t required for the Outlook part.

### 0.3 Optional but recommended: create a project structure

Example: Folder named as 'outlook_export' within folder a file named as main.py, folders with name 'output' & 'logs

outlook_export/   
    main.py  
    output/  
    logs/  

