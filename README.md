# Boshiahk2 - 嘸蝦殼 V2
免安裝的嘸蝦米輸入工具，以 AutoHotkey V2 製作。  
本程式會攔截鍵盤事件，所以會被某些掃毒軟體誤判，附上掃毒結果給大家參考：  
[32位元執行檔](https://www.virustotal.com/gui/file/93f3fd30a75d9dc6a156ab6885fe6fa3c7522234d7c73c953204124a9722a57f)
[64位元執行檔](https://www.virustotal.com/gui/file/8b8f4e5c12b98223e1f2b29fbfd4187fc07ff3a6b540db9df62cd1d28ae5759a)

一些說明可參考前一版本連結:[https://github.com/yurenli0217/BoshiahkGV](https://github.com/yurenli0217/BoshiahkGV)

### 2021-09-12 初版發佈
- 目前提供基本的輸入功能，查碼功能尚未加入。

# 輸入畫面範例
![image](https://github.com/yurenli0217/Temp/blob/main/Example_V2_WIP.png?raw=true)  

# 下載方式如下圖  
![image](https://github.com/yurenli0217/Temp/blob/main/Download.png?raw=true)

# 程式執行前置作業
- AutoHotkey 本身有鍵盤攔截功能，所以有時會被防毒軟體誤判，因此提供 32 位元與 64 位元的執行檔，請在解壓縮後，先選擇一個不會被系統誤判的執行檔。
- `Table`資料夾內放的是表格檔，`Config`資料夾放的是其它設定檔與字型檔(ttf 或 ttc)
- 程式執行時，會載入 `Config\LastPosition.ini` 儲存的座標位置，輸入介面有變更位置時會更新此檔案。刪除此檔案，執行時輸入介面會以預設值顯示在螢幕左下角。
- 若是有多個螢幕時，輸入介面會自動移到焦點視窗所在的螢幕，介面會顯示在一樣的相對位置。

## 輸入法介面開啟時，熱鍵與對應的功能
- 對輸入介面右鍵，可以結束程式。
- Ctrl-Alt-X 離開程式。
- Ctrl-Alt-R 重新載入程式。
- Ctrl-Alt-L 切換送字後是否顯示拆碼。
- Ctrl-Space 輸入法開啟/關閉。
- Shift-Space 半形/全形 輸入。
- Shift+,. 在多頁選字時，切換上下頁。
- Pgup/Pgdn 在多頁選字時，切換上下頁。
- Ctrl-Alt-Shift-C 查詢焦點視窗的 Class Name。
- Ctrl-Alt-Shift-T 查詢焦點視窗的視窗標題。

## 修改 Boshiahk2.ini 簡易說明
- 設定檔中已有針對各項設定值簡述用法。
- 設定檔分成 `[Settings]`、`[Table]`、`[Cmd]` 四個區段，請留意不要刪除。
- 使用程式前可先詳細參閱 INI 檔內說明。
### ※注意※ 如果 boshiahk2.ini 文字編碼格式不是 UTF-16LE，程式將無法正常讀取設定，用記事本開啟另存成 UTF16-LE 即可。這是 Windows 本身的限制。

## Config\ClipAuto.txt
- 檔案內容為視窗的 Class Name 清單，或是視窗標題，程式執行時會讀取該檔。
- 若是焦點視窗有符合 Class Name 或視窗標題，就會自動以剪貼簿送字。
- 可以用上述的熱鍵功能取得焦點視窗的 Class Name 或視窗標題。

如果想要符合的是 Class Name，每一行用*開頭，後面接 Class Name，如  
`*Notepad`  
只要 Class Name 為 Notepad 的都會自動用剪貼簿貼上或是停用游標跟隨。  

如果想要符合的是視窗標題，每一行直接輸入視窗標題包含的字串，如  
`批踢踢實業坊`  
視窗標題只要包含此字串，就會自動以剪貼簿送字或是停用游標跟隨。  
視窗標題也可以支援正規表示法比對字串，這是比較進階的用法，有興趣的可以試試。  
視窗標題比對時的英文大小寫視為一樣。

# 系統輸入法和語系設定
嘸蝦殼輸入介面的運作屬外掛方式輸入中文，若要正常運作，系統內建的輸入法要先進行設定。  
系統的語言設定和輸入法設定可以參照以下兩種方式:  
1. 語系設定成英文語系  
![image](https://github.com/yurenli0217/Temp/blob/main/LangSetting2.png?raw=true)  
此模式下使用外掛式中文輸入最穩定，但若是遇到某些應用程式需要系統輸入法在中文語系下才能輸入中文時，就必須要使用第二種方法。

2. 輸入法設定成倉頡英數模式(非必要時不建議)  
![image](https://github.com/yurenli0217/Temp/blob/main/LangSetting1.png?raw=true)  
設定成倉頡輸入法，可以配合 INI 設定項 `SysImePatch`，程式會自動監控將系統輸入法狀態維持在英數模式。  
例如 Excel 中的 VBA 程式編輯，就會需要用到這種方式來輸入中文。
