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

> outlook_export/   
  > main.py  
   > output/  
   > logs/  

<details> 
   <summary> Output Folder </summary>

Purpose:  
To store the emails and attachments you export.

Example usage:  
- Save .msg files inside output/  
- Save attachments inside output/attachments/  

You can rename this folder to anything:  

- saved_emails/  
- exported/  
- outlook_dump/  
- or directly use your shared folder path (e.g., \\server\share\folder\)  
</details>

<details>
   <summary> Logs Folder</summary>

Purpose:  
To keep logs of:  

- when the script ran
- how many emails it exported
- any errors

It's optional, but very useful later when you automate the script in Windows Task Scheduler.  
Common files inside:

- logs/run_20260214.txt
- logs/errors.txt

You can rename it too:

- logfiles/
- monitoring/
- or skip it completely for now
</details>

## Chunk 1 — “Hello Outlook”: connect and count Inbox mails

Replace main.py with this minimal test:

```
import win32com.client

def main():
    outlook = win32com.client.Dispatch("Outlook.Application").GetNamespace("MAPI")
    inbox = outlook.GetDefaultFolder(6)  # 6 = Inbox
    items = inbox.Items
    print("Total items in Inbox:", items.Count)

if __name__ == "__main__":
    main()
```

- [X] Run it
```
python main.py
```

> Expected output: it prints a number.

- If you get a security prompt from Outlook, allow it.  
- If it errors, possibly due to running it from wrong path, so troubleshoot the error duh!
