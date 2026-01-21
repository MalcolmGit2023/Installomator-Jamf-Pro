***

# 📦 Installomator + Jamf Pro (VLC Test)

This repo documents my first hands‑on experience using **Installomator** with **Jamf Pro** to manage application updates.  
Tested successfully with **VLC**, including user‑friendly update prompts via **swiftDialog**.

***

## ✅ Overview

I used Installomator to update an outdated version of VLC on a managed macOS device. The workflow:

*   Install an **older version of VLC**
*   Deploy **Installomator** via Jamf Pro
*   Create a **Jamf policy** targeting VLC
*   Trigger an update using Installomator’s VLC label
*   Prompt the user to quit VLC using **swiftDialog**
*   VLC updates cleanly and reliably

Result: ✅ **Worked exactly as expected**

***

## 🧪 Test Scenario

*   **Application tested:** VLC
*   **Initial state:** Older version of VLC installed
*   **MDM:** Jamf Pro
*   **Updater:** Installomator
*   **User interaction:** swiftDialog prompt to quit VLC

***

## 🛠 Setup Steps

### 1️⃣ Install Old Version of VLC

An older version of VLC was manually installed to validate Installomator’s ability to detect and update it.

***

### 2️⃣ Upload Installomator to Jamf

*   Uploaded the latest `Installomator.sh` script to **Jamf Pro**
*   Script set to run as **root**
*   No code modifications required

***

### 3️⃣ Create Jamf Policy

Policy configuration:

*   **Trigger:** Manual / Self Service
*   **Scope:** Test Mac(s)
*   **Script:** Installomator
*   **Priority:** Before / After (either works for this use)

***

### 4️⃣ Script Parameters Used

Example parameters passed to Installomator:

<img width="917" height="676" alt="image" src="https://github.com/user-attachments/assets/58242724-c40c-4fca-80b6-7a5cd3ad3a74" />


Key behavior:

*   Uses Installomator’s **VLC label**
*   Detects running VLC
*   Displays a **swiftDialog** prompt requesting the user to quit VLC
*   Proceeds with the update once VLC is closed

***

## 🧩 User Experience

When VLC is running and an update is available:

*   User sees a **swiftDialog prompt**
*   Prompt explains that an update is available
*   User is asked to quit VLC
*   After quitting, Installomator updates VLC automatically

No forced quits, no surprises.

***

## ✅ Results

*   Installomator correctly detected the outdated version
*   swiftDialog displayed clean, professional prompts
*   VLC updated successfully
*   No errors seen in Jamf policy logs

***

## 💡 Why Installomator

*   Zero packaging required
*   Maintained app definitions
*   Excellent Jamf + swiftDialog integration
*   Consistent, repeatable update workflow

***

## 🔗 References

*   Installomator Project  
    <https://github.com/Installomator/Installomator>

*   swiftDialog  
    <https://github.com/swiftDialog/swiftDialog>

*   Jamf Pro  
    <https://www.jamf.com/products/jamf-pro/>

***

## 📝 Notes / Next Steps

*   swiftdialog is required.
*   Test other apps.
