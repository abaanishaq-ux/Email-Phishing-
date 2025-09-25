# Email-Phishing-
Phishing Email Analysis — phish_report.md
Examined file: phish_sample.txt
Date analyzed: 23 Sep 2025

1 — Short summary
I examined an email that pretended to be from PayPal and asked the recipient to verify their account immediately. The message contains a spoofed sender domain, a misleading link that is not on PayPal’s domain, and an executable attachment. These are classic phishing indicators — treat the email as malicious.

2 — What I found (plain language)
1) Sender address mismatch

Seen: support@paypals-security.com
Why suspicious: Legitimate PayPal emails come from @paypal.com. The domain paypals-security.com is not PayPal’s domain and is likely controlled by the attacker to look legitimate.
2) Misleading link

Seen link: http://paypal-secure.verify-account.com/login?uid=AB123
Why suspicious: The link contains the word “paypal” but the real domain is verify-account.com. Attackers often use subdomains or long URLs to trick users into thinking the link is official.
3) Dangerous attachment

Seen: Account_Verify.exe
Why suspicious: Reputable companies do not send .exe files for account verification. Executables can contain malware. Do not download or run this file.
4) Urgent scare language

Seen text: “If you fail to verify within 24 hours, your account will be permanently suspended.”
Why suspicious: Phishers use urgency and threats to cause panic so people click without thinking. Real services provide calm instructions and official channels for help.
5) Header/authentication red flags

What to check: Received path, sending IPs, and SPF/DKIM/DMARC authentication results. If these show unrelated servers or spf=fail / dkim=fail, that indicates spoofing. (See raw headers below.)
3 — Raw headers (example saved from the sample)
Note: This is the raw header block taken from the saved sample email (paste your real headers here if you extracted them from Gmail/Outlook).

From: support@paypals-security.com
To: you@example.com
Subject: Urgent: Your Paypal Account Will Be Suspended - Verify Now
Date: Tue, 23 Sep 2025 08:35:12 +0000
Message-ID: <12345.abc@mail-server.com>
Return-Path: <support@paypals-security.com>
Received: from unknown (HELO mail-server.com) (203.0.113.45)  
        by mx.example.com with SMTP; Tue, 23 Sep 2025 08:35:13 +0000
Received-SPF: fail (mx.example.com: domain of paypals-security.com does not designate 203.0.113.45 as permitted sender)
Authentication-Results: mx.example.com; spf=fail smtp.mailfrom=paypals-security.com; dkim=neutral
Quick interpretation (simple): The Received lines show the message came from IP 203.0.113.45 — which is not a known PayPal mail server. Received-SPF: fail means the sending server was not authorized by the sender domain’s SPF record. These are strong indicators of spoofing.

4 — Evidence files included in repository
phish_sample.txt — raw saved copy of the email (headers + body).
phish_report.md — this report.
screenshot-1.png — screenshot showing link hovered (real URL visible).
screenshot-2.png — screenshot showing the email headers / “Show original” view.
(If you do not have screenshots, replace those file entries with a pasted copy of the raw headers in this report.)

5 — Recommended actions (what to do next)
Do not click links or open attachments.
Mark the message as phishing/spam in your email client to report it.
Delete the email after reporting.
If anyone clicked the link or opened the attachment:
Immediately change the passwords for the affected accounts using the official website or app (do not use the link in the email).
Enable two-factor authentication (2FA) on the account.
Scan the machine with an updated antivirus and check for suspicious activity.
If required, forward the raw headers and email to the legitimate company’s abuse/phishing contact or your security team.
6 — Short conclusion
This email is a phishing attempt. It uses domain impersonation, a misleading link, an executable attachment, and urgent language to trick the recipient. Treat it as malicious and follow the recommended actions above.

— End of report —
