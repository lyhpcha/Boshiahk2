# Boshiahk2 - 嘸蝦殼 V2
免安裝的嘸蝦米輸入工具，以 AutoHotkey V2 開發。  
本程式會攔截鍵盤事件，所以會被某些掃毒軟體誤判，附上掃毒結果給大家參考：  
[32位元執行檔](https://www.virustotal.com/gui/file/93f3fd30a75d9dc6a156ab6885fe6fa3c7522234d7c73c953204124a9722a57f)
[64位元執行檔](https://www.virustotal.com/gui/file/8b8f4e5c12b98223e1f2b29fbfd4187fc07ff3a6b540db9df62cd1d28ae5759a)

一些說明可參考前一版本連結:[https://github.com/yurenli0217/BoshiahkGV](https://github.com/yurenli0217/BoshiahkGV)

### 更新 2021-10-03
- 修正注音模式下取消後，GDI+ 文字未更新的問題。
- 在全形模式下，「:」符號無法正常輸出成「：」。
- 修正數字1左邊的「~」符號，無法正常輸出。
- 介面全部用 GDI+ 來繪製，不再使用 GUI 模式，因此設定檔已全面更新。
- 針對字型設定，現在有兩個設定值 `FontName` 與 `FontNameExt`，使用的方式請參閱下方說明。
- 表格檔也做了更新，非常感謝PTT蝦友 Fairry 的幫忙，無私整理了表格檔，請參閱下方說明。
- 查注音念法的功能碼原為`[[`，但是會有衝突，所以功能碼改成`'[` 

### 更新 2021-09-29
- 增加一個設定值`EnSwitch2`，設定另一個中英切換的按鍵。
- 加入 GDI+ 顯示設定，設定方面請參閱 INI 檔中的設定值說明。
此版本中，我從 V1 版的 GDI+ 函式庫移植了少許文字相關的繪圖函式到此版本。  
介面呈現出來的是類似於OSD的效果(沒有背景色)，我自己在 V1 版中都是設定成這樣的外觀使用的。  
有興趣的可以切換到 GDI+ 模式試試看。
- 新增設定值`FontBold`，GUI和GDI+模式都會套用此設定值。
- 移除系統列圖示右鍵結束程式的功能，避免誤按

### 更新 2021-09-26
- 修正英文模式下，按「;」與「'」時，送字轉換錯誤的情況。

### 更新 2021-09-24
- 新增: 萬用碼查碼，請見下方說明。
- 新增: 送字時查詢注音，請參閱下方說明
- 修正跟隨螢幕功能內部錯誤
- 修正`BorderStyle`的設定值錯誤

### 更新 2021-09-20
- INI新增: [Settings] StartHidden、BorderStyle 兩個設定值。
- 修正程式內小錯誤。

### 更新 2021-09-16
- 程式碼整理，移除無用程式碼
- 修正: 輸入列寬度計算有時會錯誤的問題。

### 2021-09-15 初版發佈

# 輸入畫面範例 - (PNG動畫格式)
![image](https://github.com/yurenli0217/Temp/blob/main/Example_All.png?raw=true)  

# 下載方式如下圖  
![image](https://github.com/yurenli0217/Temp/blob/main/Download.png?raw=true)

# 程式執行前置作業
- AutoHotkey 本身有鍵盤攔截功能，所以有時會被防毒軟體誤判，因此提供 32 位元與 64 位元的執行檔，請在解壓縮後，先選擇一個不會被系統誤判的執行檔。
- `Table`資料夾內放的是表格檔，`Config`資料夾放的是其它設定檔。
- 程式執行時，會載入 `Config\LastPosition.ini` 儲存的座標位置，輸入介面有變更位置時會更新此檔案。刪除此檔案，執行時輸入介面會以預設值顯示在螢幕左下角。
- 若是有多個螢幕時，輸入介面會自動移到焦點視窗所在的螢幕，介面會顯示在一樣的相對位置。

## 輸入法介面開啟時，熱鍵與對應的功能
- Ctrl-Space 輸入法開啟/關閉。
- Ctrl-Alt-R 重新載入程式。
- Ctrl-Alt-C 查看上一次送字之拆碼
- Ctrl-Alt-G 重複上一次送出的字。
- Ctrl-Alt-P 進入注音模式。
- Shift-Space 半形/全形 輸入。
- Shift+,. 在多頁選字時，切換上下頁。
- Pgup/Pgdn 在多頁選字時，切換上下頁。
- Ctrl-Alt-Shift-C 查詢焦點視窗的 Class Name。
- Ctrl-Alt-Shift-T 查詢焦點視窗的視窗標題。
- 對輸入介面按右鍵，可以結束程式。

## 表格檔架構
程式內含的表格檔由 PTT Liu板蝦友 `Fairry` 無私整理，他將表格檔重新規劃，檔案說明如下:
- _Common.txt: 通用符號
- _Phonetic.txt: 注音對應表
- _User.txt: 使用者自訂字詞
- Liu.txt: 包含了Unicode擴展區的文字。
- LiuJap.txt: 日文專用表格
- LiuT2S.txt: 常用字打繁出簡表格
###本程式的表格檔內容含擴展A、B區的文字，推薦使用「全字庫正楷體」，此字型可支援到 Unicode 第2字面。

# 查詢功能
- 萬用碼查碼: 先輸入前導碼`[`，再輸入字根，不確定字根用`.`來代表。如`[A..P`，會顯示字碼首碼為`A`、尾碼為`P`、以及字根數為「四碼」的選字。
- 查詢注音: 先輸入前導碼`'[`，再輸入字根，選字後會顯示注音念法。

## 修改 Boshiahk2.ini 簡易說明
- 設定檔中已有針對各項設定值簡述用法。
- 設定檔分成 `[Settings]`、`[Table]`、`[CmdKey]` 三個區段，請留意不要刪除。
- 使用程式前可先詳細參閱 INI 檔內說明。
### ※注意※ 如果 boshiahk2.ini 文字編碼格式不是 UTF-16LE，程式將無法正常讀取設定，用記事本開啟另存成 UTF16-LE 即可。這是 Windows 本身的限制。

## FontName 與 FontNameExt 使用範例
使用的方式用全字庫來說明，全字庫正楷體中有兩個檔案名稱:  
`TW-Kai-98_1.ttf`  
`TW-Kai-Ext-B-98_1.ttf`  
其中`TW-Kai-Ext-B-98_1.ttf`儲存的文字是在Unicode `0x20000` 開始的文字，如果也想要使用這個字型檔，可以用以下設定值:  
`FontName = TW-Kai-98_1.ttf`  
`FontNameExt = TW-Kai-Ext-B-98_1.ttf`  
這樣在 Unicodde 0x20000 以後的文字就會用 TW-Kai-Ext-B-98_1.ttf 來顯示了。

## Config\ClipAuto.txt
- 檔案內容為視窗的 Class Name 清單，或是視窗標題，程式執行時會讀取該檔。
- 若是焦點視窗有符合 Class Name 或視窗標題，就會自動以剪貼簿送字。
- 可以用上述的熱鍵功能取得焦點視窗的 Class Name 或視窗標題。

如果想要符合的是 Class Name，每一行用*開頭，後面接 Class Name，如  
`*Notepad`  
只要 Class Name 為 Notepad 的都會自動用剪貼簿貼上。  

如果想要符合的是視窗標題，每一行直接輸入視窗標題包含的字串，如  
`批踢踢實業坊`  
視窗標題只要包含此字串，就會自動以剪貼簿送字。  
視窗標題也可以支援正規表示法比對字串，這是比較進階的用法，有興趣的可以試試。  
視窗標題比對時的英文文字不分大小寫。

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
