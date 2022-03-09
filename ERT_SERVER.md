# 測試用4G路由器(固定IP)設定指引

### 相關參數
+ 固定IP=211.21.102.67
+ Wifi帳號密碼: TP-Link_B32E // cgrg65609
+ LAN DHCP範圍: 192.168.1.101 - 192.168.1.199
+ DMZ設定: 啟用，指定IP=192.168.1.250 

# Win7_64_R2MS_Server VirtualBox安裝指引

### 需求
+ 事前製作完成的Win7_64bit_EarthImagerVM.ova。

### 虛擬機設定
+ 匯入「Win7_64bit_EarthImagerVM.ova」。改名稱為「Win7_64_R2MS_Server」，先使用預設值匯入至自訂的位置，例如:「D:\VM」。
+ 匯入完成後先不要開機，先進行虛擬機參數設定:
    + 「一般>進階>共用剪貼簿」:雙向  
    + 「一般>進階>拖放」:雙向  
    + 「系統>主機板>基本記憶體」:4096[MB]  
    + 「系統>主機板>處理器」:4  
    + 「網路>介面卡1>連接埠轉發>」:   
        + Rule1:協定=TCP，主機IP=「0,0,0,0」，主機連接埠=「80」，客體IP=「0,0,0,0」，客體連接埠=「80」  
        + Rule2:協定=TCP，主機IP=「0,0,0,0」，主機連接埠=「8080」，客體IP=「0,0,0,0」，客體連接埠=「8080」  
    + VM開機，進入桌面會偵測硬體變化後提示重新啟動。按下重新啟動。
    + 提示非正版，請自行啟用。沒有啟用也不影響後續測試開發。
    + VM關機。在關機狀態下，在Host主機上編輯bat檔案，使內容為:「"C:\Program Files\Oracle\VirtualBox\VBoxManage.exe" modifyhd "D:\VM\Win7_64_R2MS_Server\XXX.vdi" --resize 102400」。
    + VM開機後，進入裝置管理員>存放裝置>磁碟管理，於C:磁碟按下右鍵，延伸磁碟區，下一步，完成。至此硬碟可用空間為100[GB]。  

### 第三方軟體安裝  
+ 安裝「ChromeStandaloneSetup64.exe」。安裝完成後手動移除工作列的舊IE捷徑。
+ 安裝「npp.8.1.6.Installer.x64.exe」。
+ 安裝「xampp-windows-x64-7.4.27-2-VC15-installer.exe」。只安裝Apachea、MySQL、PHP、Perl、phpMyAdmin。
    + 以系統管理員身分運行主程式「C:\xampp\xampp-control.exe」。設定「Config>Autostart of modules」把「Apachea、MySQL」打勾。再把「Config>Start Control Panel Minimized」打勾。再按下「Save」。完成之後重新啟動電腦。
    + 使用普通使用者身分運行一次主程式「C:\xampp\xampp-control.exe」，允許通過防火牆(私人網路與工作網路都允許)。
    + 製作捷徑並放到「啟動」資料夾中。
+ 安裝「MCR_R2014a_win64_installer.exe.exe」。使用預設路徑。

### 自有軟體
+ 解壓縮「R2MS_ERT_Web_Server.zip」內檔案到「C:\R2MS_ERT_Web_Server」下。
+ 手動執行「C:\R2MS_ERT_Web_Server\R2MS_ERT_Wizard_Web_Server.exe」，允許通過防火牆(私人網路與工作網路都允許)。製作捷徑並放到「啟動」資料夾中。
+ 手動執行「C:\R2MS_ERT_Web_Server\ERT_Inversion_Master_Web_Server.exe」，允許通過防火牆(私人網路與工作網路都允許)。製作捷徑並放到「啟動」資料夾中。
+ 手動執行「C:\R2MS_ERT_Web_Server\windows-amd64-filebrowser\filebrowser.exe」，允許通過防火牆(私人網路與工作網路都允許)。製作捷徑並放到「啟動」資料夾中。
+ 解壓縮「R2MS_PHP.zip」內檔案到「C:\xampp\htdocs」下。


