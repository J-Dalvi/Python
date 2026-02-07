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
