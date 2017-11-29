---
title: Mac远程Win失败
date: 2016-09-18 18:37:54
tags:
---
# Mac远程Win10失败，提示：远程桌面连接无法验证您希望连接的计算机的身份

Solution
Enable RDP security layer in Group Policy on the machine:

Verify that the firewall allows remote desktop connections with RDP (Port 3389)
Click Start>Run
Type gpedit.msc and click "OK"
Result: The Group Policy Editor will open
In the left hand side bar, expand Computer Configuration>Administrative Templates>Windows Components>Remote Desktop Services>Remote Desktop Session Host
Select "Security"
Change "Require use of specific security layer for remote desktop (RDP) connection" to Enabled" and select "RDP" in the Options pane.
Change "Require user authentication for remote connections by using Network Level Authentication" to "Disabled."
Close Group Policy Editor and reboot the machine for changes to take effect.