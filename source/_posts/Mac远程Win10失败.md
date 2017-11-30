---
title: Mac远程Win失败
date: 2016-09-18 18:37:54
tags:
- mac
- 远程
---
Mac远程Win10失败，提示：远程桌面连接无法验证您希望连接的计算机的身份

# Solution
* 1.Enable RDP security layer in Group Policy on the machine.

* 2.Verify that the firewall allows remote desktop connections with RDP (Port 3389)
* 3.Click Start>Run，Type gpedit.msc and click "OK", The Group Policy Editor will open.
* 4,In the left hand side bar, expand Computer Configuration>Administrative Templates>Windows Components>Remote Desktop Services>Remote Desktop Session Host.
* 5.Select "Security",Change "Require use of specific security layer for remote desktop (RDP) connection" to Enabled" and select "RDP" in the Options pane.
* 6.Change "Require user authentication for remote connections by using Network Level,Authentication" to "Disabled."
* 7.Close Group Policy Editor and reboot the machine for changes to take effect.