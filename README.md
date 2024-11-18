# Pastejacking Proof of Concept (PoC)

## Quick Note 🤦‍♂️
Yeah, I called this clickjacking earlier... whoops! Pastejacking is still new to me, so bear with me while I get the terminology right. Let’s dive into what it’s all about! 🚀

### What is Pastejacking?
Pastejacking is an interesting attack, especially given the number of CAPTCHAs we encounter daily. Threat actors exploit this by injecting websites with malicious redirects to fake CAPTCHAs. When users click to "verify" they’re human, the site injects a malicious command into their clipboard and instructs them to press Windows Key 🪟 + R, then Ctrl ⌨️ + V 📋, and finally hit Enter ⏎ to execute it.

While this is an interesting approach, using fake CAPTCHAs as the lure, it’s no surprise they’re effective—real CAPTCHAs are becoming more frequent, harder to solve, and causing fatigue, making users more likely to fall for these tricks.

### Why Should You Care?
Pastejacking is being used to spread malware like Lumma Stealer, an info-stealer that can grab your passwords, browser data, and even cryptocurrency wallets.

### How This PoC Works
This demo shows how pastejacking can:

- Trick users into copying a malicious PowerShell command by simply clicking on a website verify prompt.
- Execute the command in a hidden window, that downloads and runs a payload (a zip file containing 7Zip in this case).
- Extract and execute the payload automatically.

### The Multi-Stage Attack Chain
- **Set the Trap**: The user thinks they’re solving a CAPTCHA but ends up copying a preloaded malicious command.
- **Clipboard Hijack**: The clipboard gets injected with a PowerShell command that's obfuscated and difficult to understand.
- **Execution**: When pasted and executed, the command downloads, extracts, and runs the payload.

## See the PoC in Action 🚀
I've created an example site to show how pastejacking works. You can visit the site and see the attack in action:
https://mrlukerwilkinson.github.io/click_jacking_poc/

Here’s what to do:

- Click the "Verify you are human" checkbox on the site.
- Open Notepad 📝 or any text editor.
- Press Ctrl ⌨️ + V 📋 to paste the clipboard content.

You’ll see the malicious command that would have been executed if pasted into a terminal or Run dialog. This demonstrates how threat actors trick users into unknowingly running harmful code.

## Important Disclaimer ⚠️
**Before you proceed, please read the following carefully**:

**Educational Use Only**:
This PoC is for educational purposes and ethical testing in a controlled environment. Do not use this for malicious activities—it’s illegal and unethical.

**Non-Malicious Executable**:
The provided example does not contain harmful software. Instead, it uses a legitimate and clean version of 7-Zip as the executable. This ensures the demonstration is safe to explore without risking your system.

**File Verification**:
To confirm the file's integrity and authenticity, here is the hash of the 7-Zip executable used:

**SHA-256**: 67CB9D3452C9DD974B04F4A5FD842DBCBA8184F2344FF72E3662D7CDB68B099B

Verify this hash before running the file to ensure it has not been tampered with.

**"Unknown Program" Prompt**:
If you choose to run the pasted command, you may see a Windows prompt asking you to confirm installation of an unknown program. This is because the executable was renamed to setup.exe and lacks a digital signature. Windows flags unsigned or renamed files as "unknown."
While this PoC uses a legitimate executable, this demonstrates how attackers might disguise malicious software.

**Do Not Run Commands**:
Avoid pasting the generated command into a terminal or Run dialog unless you fully understand its purpose. Instead, view the pasted content in a text editor like Notepad to safely examine the attack mechanics.

