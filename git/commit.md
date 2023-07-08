# git commit 規則

## 架構
- #為什麼要寫GitCommitMessage
- #為什麼要固定格式
- #Message的格式
    - #TYPE類型
    - #SUBJECT主旨
    - #BODY本文
    - #FOOTER頁尾
- #範例

## 一、 #為什麼要寫GitCommitMessage
記錄下做了哪些異動，以及為什麼要做這些異動。讓後人能夠快速地了解異動的內容，方便回溯程式碼已修正錯誤或添加新功能。

## 二、 #為什麼要固定格式
一個好的格式與規範，能夠讓人一目了然，迅速看出該Commit的重點。而且，在多人協作或專案交接時，不易造成各自為政的情形。

## 三、 #Message的格式
TYPE: SUBJECT

BODY

FOOTER
一個完整的Commit訊息必須包含以上三大區塊，且都由空行區隔。
第一行標題列，必須包含類型與主旨。

### 3-1 #TYPE類型
類型必須包含在標題中，且符合下列類型。

| 類型 | 說明 | 程式碼改動 |
| ----- | ----- | ----- |
| new | 新功能 | 有 |
| Modify | 既有功能需求調整的修改 | 有 |
| Fix | 錯誤修正 | 有 |
| Docs | 更新文件，如 README.md | 沒有 |
| Style | 程式碼格式調整(formatting)、缺少分號(missing semi colons)等 | 沒有 |
| Refactor | 重構針對已上線的功能程式碼調整與優化，且不改變記有邏輯 | 有 |
| Test | 測試新增測試、重構測試等 | 沒有 |
| Chore | 更新專案建置設定、更新版本號等瑣事 | 沒有 |
| Revert | 撤銷之前的commit revert: type(scope): subject (回覆版本：xxxx) | 有 |
| copy | 複製檔案 | 有 |

### 3-2 #SUBJECT主旨
主旨不應超過50個字元，若用英文書寫則需大寫開頭，中英文都不用句號結尾。
盡量以祈使句書寫，言簡意賅的簡述此Commit的改動。

### 3-3 #BODY本文
不是每個Commit都一定需要本文。
撰寫本文時，請務必將改了什麼與為什麼而改寫清楚。
每行不超過72個字。

### 3-4 #FOOTER頁尾
一般來說FOOTER不一定要寫。
通常用來標註對應的issue編號 (issue tracker IDs)。

## 四、 #範例
Fix: 修正首頁資料載入緩慢問題

- 首頁載入後等待超過10秒資料才顯示。
    - 將資料改為一次撈取，並暫存在記憶體中。

issue #456
Summarize changes in around 50 characters or less

More detailed explanatory text, if necessary. Wrap it to about 72
characters or so. In some contexts, the first line is treated as the
subject of the commit and the rest of the text as the body. The
blank line separating the summary from the body is critical (unless
you omit the body entirely); various tools like `log`, `shortlog`
and `rebase` can get confused if you run the two together.

Explain the problem that this commit is solving. Focus on why you
are making this change as opposed to how (the code explains that).
Are there side effects or other unintuitive consequences of this
change? Here's the place to explain them.

Further paragraphs come after blank lines.

 - Bullet points are okay, too

 - Typically a hyphen or asterisk is used for the bullet, preceded
   by a single space, with blank lines in between, but conventions
   vary here

If you use an issue tracker, put references to them at the bottom,
like this:

Resolves: #123
See also: #456, #789

## 註解及參見
[Git Commit Message 這樣寫會更好，替專案引入規範與範例](https://wadehuanglearning.blogspot.com/2019/05/commit-commit-commit-why-what-commit.html)
[Git Commit Message Style Guide #300](https://github.com/android/architecture-samples/issues/300)
[How to Write a Git Commit Message](https://cbea.ms/git-commit/)
[Angular Commit Messages Guideline](https://github.com/angular/angular/blob/22b96b9/CONTRIBUTING.md#commit)
[Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)