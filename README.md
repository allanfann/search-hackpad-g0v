# search-hackpad-g0v

這是 g0v 基礎建設的一個小坑，目標是做一個輕便快速的搜尋器，來取代 hackpad 現在的搜尋介面

好處是：

- 開新的專案、idea 之前，可以快速 review 一下是否有類似的討論或專案
- 找舊東西比較方便
- 不用在不同的平台上重複搜尋
- 搜尋結果不需要無止境的分頁、外連


最終希望是將這些都即時索引起來：

- g0v hackpad
- 所有 g0v hackpad 上有公開連結的 hackfoldr
- g0v github readme
- g0v.tw
- irc/slack log


目前只先做到用 jieba 把 https://github.com/g0v-data/hackpad-backup-g0v 所有的 html 做成可搜尋的索引檔案

現在有以下功能：

### make_index.py
- 會先在 hackpad-backup-g0v 下面 git submodule update 檢查是否有新的檔案
- 根據 hackpad-backup-g0v/pads.json 比對上次更新的時間、目前已經索引的檔案，將新增/更動的 html 重新 merge 到索引檔

### search.py
- 載入索引器後，輸入關鍵字，會找出相關的 hackpad id, last modify(commit) time, title

接下來要：

- 試著將搜尋變成一個 web API
- 當 hackpad-backup-g0v 更新時，自動觸發 make_index.py
- 整合其他資料

----
python3 & pip install:

- jieba
- whoosh
- html2text


`git submodule update --init`

`python3 make_index.py`

`python3 search.py`

根據這個教學來改的: http://www.jeyzhang.com/realization-of-full-chinese-text-search-using-whoosh-and-jieba.html

p.s 這是我第一次寫 python 有更好的做法請指教 >_<






