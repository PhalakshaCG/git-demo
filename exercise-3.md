# Jenkins Setup Instructions

## Step 1: Add the NodeJS Plugin
1. Open Jenkins in your browser.
2. Go to **Manage Jenkins** > **Manage Plugins**.
3. In the **Available** tab, search for "NodeJS".
4. Select the **NodeJS** plugin and click **Install without restart**.
5. Wait for the installation to complete.

---

## Step 2: Configure NodeJS as a Global Tool
1. Go to **Manage Jenkins** > **Global Tool Configuration**.
2. Scroll down to the **NodeJS** section.
3. Click **Add NodeJS**.
4. Provide a name (e.g., `NodeJS 16`) and select the desired Node.js version.
5. Check the box for "Install automatically" if you want Jenkins to handle the installation.
6. Click **Save**.

---

## Step 3: Create a Freestyle Project
1. Go to the Jenkins dashboard.
2. Click **New Item**.
3. Enter a name for your project (e.g., `WeatherAppPipeline`).
4. Select **Freestyle project** and click **OK**.
5. In the project configuration:
   - Under **Source Code Management**, select **Git**.
   - Provide the repository URL: `https://github.com/PhalakshaCG/demo-app.git`.
   - Add credentials (see Step 4).
   - Specify the branch to build (e.g., `main`).

---

## Step 4: Add GitHub Credentials
1. In the project configuration, under **Source Code Management**, click **Add** next to the **Credentials** dropdown.
2. Select the appropriate scope (e.g., **Global**).
3. Enter your GitHub username and personal access token.
4. Click **Add**.

---

## Step 5: Add Build Steps
1. In the project configuration, scroll down to the **Build** section.
2. Click **Add build step** > **Execute shell**.
3. Paste the following script:
   ```bash
   ls
   npm i
   # echo "WEATHER_API_KEY=24efb5d2ec9345c5a60123707260101" >> .env
   npm start & echo $! > app.pid
   sleep 2
   HTTP_STATUS=$(curl -o /dev/null -s -w "%{http_code}" "http://localhost:3000/weather")
   kill $(cat app.pid)
   rm app.pid

   if [ "$HTTP_STATUS" -eq 200 ]; then
     echo "Request succeeded with status code: $HTTP_STATUS"
     exit 0 # Pass the pipeline
   else
     echo "Request failed with status code: $HTTP_STATUS"
     exit 1 # Fail the pipeline
   fi
   ```

---

## Step 6: Save and Run the Job
1. Click **Save** to save the project configuration.
2. Go back to the project dashboard and click **Build Now** to trigger the job.
3. Monitor the console output to verify the script execution and the HTTP status check.

---
