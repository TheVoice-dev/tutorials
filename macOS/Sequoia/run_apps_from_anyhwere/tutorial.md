# 🛠️ Disable Gatekeeper on macOS Sequoia (macOS 15)

> Run apps from anywhere — no App Store, no notarization, no restrictions.

---

## 🤔 Why Do This?

Apple’s Gatekeeper blocks apps that aren’t from the App Store or signed by "identified developers." This helps prevent accidental casual installation of malicious software—but it also locks out indie and open-source apps that don’t go through Apple's approval process.

Sometimes, the app you need isn’t on the App Store:
- It’s built by a solo developer or small team
- It’s open-source or free and doesn’t generate App Store revenue
- It’s too niche to justify distribution through Apple’s pipeline

If you’re just browsing email, YouTube, or using standard productivity tools—you’re fine. But if you want to explore outside the walled garden, here’s how to open the gate—with a caveat emptor:  
**you take full responsibility, and the training wheels are off.**

What does this mean?

If you don’t know how to verify an app, who made it, or what it does—**don’t install it**. It’s your system, your risk. Be smart. Don’t just grab random apps off the web unless you:
- Know and trust the developer
- Understand the app’s function OR,
- You yourself can audit the source code if available.

---

## ✅ Steps

1. **Open System Settings**
   - Apple Menu > System Settings  
   - Click **Privacy & Security**  
   - Scroll to "Security"
   - You will have a dropdown, or radio buttons, your options on either will be "App Store" and "App Store and Known Developers"
   - We need to add "Anywhere"
   - **So leave this window open**. Don’t close it!  
   - Proceed to Step 2.

2. **Open Terminal**
   - Open Spotlight  
     - Press and hold command key and tap spacebar  
     - In Spotlight type: Terminal  
     - Terminal will show in selections, click it.

3. In Terminal type and hit enter:
   ```bash
   sudo spctl --master-disable
   ```
   - You will be prompted for your password.
   - Enter your admin password when prompted
   - Once password is entered proceed to Step 4.

4. **Return to System Settings**
   - **Privacy & Security** should still be open from Step 1.
   - In your "Security" section with dropdown or radio buttons you will now have three options:
     - App Store
     - App Store and Known Developers
     - Anywhere

5. **Enable “Anywhere”**
   - Select "Anywhere" from dropdown or click and select "Anywhere" in the radio options.
   - Enter your password if required

---

## 🧠 Tips

- “Anywhere” only shows up if System Settings is open **before** the terminal command
- SIP (System Integrity Protection) does **not** need to be disabled
- Don’t install apps you can’t verify

---

## 🔐 Verify App Integrity (SHA-256 Check)

If the developer provides a checksum, run:

```bash
shasum -a 256 /path/to/AppName.app
```

Compare the output hash with what the developer published.

**If it doesn’t match — don’t run it.** This is a common way to confirm the app hasn’t been tampered with.

---

## 🔁 Re-enable Gatekeeper after you are finished using your newly installed app.

```bash
sudo spctl --master-enable
```

Turn Gatekeeper back on once you’ve installed the app. Helps prevent surprises later.

---

## 🧾 Balanced Take

- **Apple’s Side**: Curated, signed apps create a stable ecosystem and generate billions through App Store revenue.
- **User Freedom**: Without workarounds, Apple decides what you’re allowed to run. That’s not ideal if you need niche tools or open-source utilities.

**For average users** — App Store + signed apps is safest.  
**For developers and or unique cottage apps** — sometimes you need access to software the gate won’t let in.

---

> ✅ You're in control. Use responsibly. Stay curious.

