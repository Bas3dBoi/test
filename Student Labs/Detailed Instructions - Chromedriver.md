# Detailed Instructions for Installing and Setting Up ChromeDriver

ChromeDriver is essential for running Selenium tests on Google Chrome. Follow these steps to download and set up ChromeDriver on your system.

**Step 1.** Check Your Chrome Browser Version
1. Open Google Chrome.
2. Click the three dots in the upper right corner.
3. Go to "Help" > "About Google Chrome".
4. Note the version number of Chrome.

**Step 2:** Download ChromeDriver
1. Go to the [ChromeDriver download page](https://sites.google.com/chromium.org/driver/downloads).
2. Find the version of ChromeDriver that matches your Chrome browser version.
3. Download the appropriate version for your operating system (Windows, macOS, or Linux).

**Step 3:** Extract the ChromeDriver Executable
1. Locate the downloaded ZIP file (e.g., `chromedriver_win32.zip` for Windows).
2. Extract the ZIP file. The extracted file will be the `chromedriver.exe` executable (or just `chromedriver` on macOS and Linux).

**Step 4:** Move ChromeDriver to a Directory in Your PATH

- Windows
   1. Create a new directory for ChromeDriver (e.g., `C:\chromedriver`).
   2. Move `chromedriver.exe` to the new directory.
   3. Add the directory to your system's PATH:
     - Open the Start Menu, search for "Environment Variables", and select "Edit the system environment variables".
     - In the System Properties window, click on the "Environment Variables" button.
     - In the Environment Variables window, find the "Path" variable in the "System variables" section, and click "Edit".
     - Click "New" and add the path to the directory where you placed `chromedriver.exe` (e.g., `C:\chromedriver`).
     - Click "OK" to close all windows.

- macOS/Linux
   1. Open a terminal.
   2. Move `chromedriver` to `/usr/local/bin`:
   
   ```sh
   sudo mv chromedriver /usr/local/bin/
   ```
   3. Ensure `chromedriver` is executable:

     ```sh
     sudo chmod +x /usr/local/bin/chromedriver
     ```

**Step 5:** Verify the Installation
1. Open a terminal or command prompt.
2. Type `chromedriver` and press Enter.
3. If ChromeDriver is installed correctly, you should see output indicating that ChromeDriver is starting:

   ``` bash
   Starting ChromeDriver 91.0.4472.101 (sha1:5b2a2c63488b4f3223c396072c741d556c6df545) on port 9515
   Only local connections are allowed.
   Please see https://chromedriver.chromium.org/security-considerations for suggestions on keeping ChromeDriver safe.
   ChromeDriver was started successfully.
   ```