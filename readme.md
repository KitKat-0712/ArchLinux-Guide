# Arch Linux &nbsp;X &nbsp;GNOME 安裝 & 調校指南 (繁中)
* Last Modified Date : 2022/07/28 Thu
* Contact with ME on **Telegram** : `@green_tea_tastes_good`

---

&nbsp;
## 安裝Arch Linux(透過archinstall)

* 請先製作開機碟 , 並將開機碟的開機順序調為第一順位

&nbsp;

* 你可以透過 `archinstall` 用比較人性化的方式安裝 Arch Linux

    **注意** : 此過程需要連接網路 , 這裡使用有線連接的方式

&nbsp;

* 教學影片(以第一支影片為主) :
    * <https://youtu.be/YiDM4ymenE8>
    * <https://youtu.be/leQbSsu-7F4>

&nbsp;

* 基本上照著**第一支**影片一步一步來就會成功 , 不過有些選項可以按照你的需求調整 , 像是
    * `Drive(s)` 硬碟
    * `Bootloader` 啟動程式 - 建議選擇 **no (default)** , 影片中的 **grub-install** 是因為虛擬機的關係
    * `Root password` Root的密碼 - 建議不要是空的
    * `User account` 使用者帳號 - 建議要給使用者帳號sudo權限
    * `Additional packages` 套件 - 推薦安裝套件 :
        * `vim` 文字編輯器
        * `firefox` 瀏覽器
        * `wqy-zenhei` 中文字型(因為語言設為中文 , 若不安裝中文字型會導致無法正確顯示中文字)
        * `ibus` `ibus-chewing` 中文輸入法
        * `git`
        * `neofetch` 顯示系統資訊

&nbsp;

* 安裝完後會跳出以下畫面 , 任選其一
    
    <img src="https://i.postimg.cc/rwJB4D0X/Virtual-Box-Arch-Linux-26-07-2022-11-37-41.png" width="50%" alt="# 無法載入圖片 #">

    &nbsp;

    接著會回到這個畫面 , 輸入 `reboot` 後等字跑完 , 螢幕黑屏時迅速拔除開機碟

    <img src="https://i.postimg.cc/zv5gMD5N/Virtual-Box-Arch-Linux-26-07-2022-16-29-30.png" width="50%" alt="# 無法載入圖片 #">

    &nbsp;

    如果動作不夠快可能會回到一開始的選擇畫面 , 這時選擇最下面的 **Reboot** 並拔除開機碟

    <img src="https://i.postimg.cc/Pxqx8LtP/Virtual-Box-Arch-Linux-26-07-2022-16-46-19.png" width="50%" alt="# 無法載入圖片 #">

    &nbsp;

    安裝成功 !
    
    <img src="https://i.postimg.cc/L8TNVXdz/Virtual-Box-GNOME-26-07-2022-16-57-46.png" width="50%" alt="# 無法載入圖片 #">

&nbsp;
## 基本指令
* 終端機(Terminal) - 可以執行Linux命令(Linux Command) , 輸入命令後按Enter即可執行 , 文章中的 *執行 ...(命令)* 皆指此

    <img src="https://i.postimg.cc/jjT4wnMH/2022-07-26-17-42-16.png" width="50%" alt="# 無法載入圖片 #">

&nbsp;

* 檔案與目錄管理 : <https://blog.techbridge.cc/2017/12/23/linux-commnd-line-tutorial/>

&nbsp;

* 立即關機 - `shutdown -h 0`
* 重新啟動 - `reboot`

&nbsp;

* neofetch - 顯示系統資訊(需要 `neofetch` 套件才能正常執行)

&nbsp;

* pacman - 套件管理器
    * 安裝套件 : `pacman -S <package>`
    * 移除套件 : `pacman -R <package>`
    * 更新所有的套件 : `sudo pacman -Syu`
    * 需要時前面會加上 `sudo`
    * 範例 : `sudo pacman -S neofetch`

&nbsp;

* 從AUR上管理套件
    * 網址 : <https://aur.archlinux.org/>
    * 安裝套件(需要 `git` 套件才能正常執行) :
        ```
        git clone https://aur.archlinux.org/<package>.git
        cd <package>
        makepkg -si
        ```
    * 刪除套件 : `sudo pacman -R <package>`


&nbsp;

* vim - 文字編輯器(需要 `vim`套件才能正常執行)
    
    * 開啟文件(有時需要sudo權限) : `vim <file>` 或 `sudo vim <file>`

        <img src="https://i.postimg.cc/Ls3BdKHP/2022-07-26-21-13-17.png" width="50%" alt="# 無法載入圖片 #">
    
    * 開啟後是 **命令模式** , 按 `i` 鍵進入 **輸入模式** ( 底下會顯示 **-- 插入 --** )
    
    * 按 `Esc` 鍵回到 **命令模式** 後 , 再按 `:` 會進入 **底線命令模式** , 常用的底線命令如下(輸入完後按Enter) :
        * `wq` : 儲存並退出
        * `q` : 退出(檔案沒有變更時)
        * `q!` : 強制退出(檔案有變更但不想儲存)
    
    * 參考 : 
        * <http://www.vixual.net/blog/archives/234>
        * <https://www.runoob.com/linux/linux-vim.html>

&nbsp;
## 安裝中文輸入法(新酷音)
1. 安裝 `ibus` 和 `ibus-chewing` 套件

2. 執行 `sudo vim /etc/profile.d/ibus.sh`

    開啟後新增這些字 :
    ```
    GTK_IM_MODULE=ibus
    QT_IM_MODULE=ibus
    XMODIFIERS="@im=ibus"
    ```
    完成後儲存退出 , 重新登入

3. 接著到 **設定值(Settings) - 鍵盤 - 輸入來源** 手動加入新酷音中文輸入法 , 即完成

    <img src="https://i.postimg.cc/9XD22kHZ/2022-07-26-14-34-18.png" width="50%" alt="# 無法載入圖片 #">

* 參考 : <https://blog.xuite.net/ak47588168/linux/45614115>

&nbsp;
## 安裝GNOME擴充套件(GNOME Shell Extension)前所需的準備
1. 安裝 `gnome-shell-extensions` 套件

2. 在 **Firefox 附加元件站** 的 **GNOME Shell integration** 中按下 **新增至 Firefox** 按鈕

    連結 : <https://addons.mozilla.org/zh-TW/firefox/addon/gnome-shell-integration/>

    <img src="https://i.postimg.cc/PJ9qBK0f/2022-07-17-21-20-25.pnghttps://i.postimg.cc/PJ9qBK0f/2022-07-17-21-20-25.png" width="50%" alt="# 無法載入圖片 #">

    執行以下指令(需要 **git** 套件才能正常執行) :
    ```
    git clone https://aur.archlinux.org/gnome-browser-connector.git
    cd gnome-browser-connector
    makepkg -si
    ```

3. 重新登入後即可新增GNOME擴充套件

&nbsp;
## 如何安裝 & 設定擴充套件
1. 在 GNOME Shell Extension 商店中 , 將需要的擴充套件啟用

    GNOME Shell Extension 商店連結 : <https://extensions.gnome.org/>

    <img src="https://i.postimg.cc/ZKwBLFwQ/2022-07-17-21-06-56.png" width="50%" alt="# 無法載入圖片 #">

&nbsp;

2. 在 **擴充套件(Extensions)** 應用程式中 , 將最上面的 **擴充套件** 選項啟用 , 往下滑找到剛剛啟用的擴充套件 , 即可設定

    <img src="https://i.postimg.cc/mk2MbddQ/2022-07-17-21-17-38.png" width="50%" alt="# 無法載入圖片 #">

* 注意 : **GNOME Shell Extension 商店** 和 **擴充套件 應用程式** 是同步的

&nbsp;
## 安裝主題(Theme)前所需的準備
* 請確認你已經做了 **安裝Gnome擴充套件(GNOME Shell Extension)前所需的準備** 這段所描述的步驟

* 在 **GNOME Shell Extension** 商店中 , 將 **User Themes** 擴充套件啟用 , 重新登入後即完成
    
    連結 : <https://extensions.gnome.org/extension/19/user-themes/>

&nbsp;
## 如何切換主題
* 安裝完主題後 , 在 **調校(Tweaks) - 外觀 - 佈景主題 - Shell** 即可切換主題

* 如果無法切換主題 , 如下圖所示 , 請照著 **安裝主題(Theme)前所需的準備** 這段所描述的步驟再做一次

    <img src="https://i.postimg.cc/gkZXjN4j/2022-07-26-23-01-15.png" width="50%" alt="# 無法載入圖片 #">
