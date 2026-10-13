# 一套真的能用的 workflow skills，不是更漂亮的說明書

**直接結論**：好的 skill 不是把話說得更完整，而是把失敗切得更乾淨。你要的是一套能讓 agent 先停下來看證據、再決定要不要改 prompt 的系統。

## 這版的差異
- 不再只寫「可以做什麼」；也寫「先看哪個失敗點」
- 不再只寫「證據很重要」；而是寫「證據不夠時怎麼停」
- 不再只寫「不要混版本」；而是把 current / archive / pending 明確化
- 不再只做五個 skill；多一個 router，避免 agent 猜錯入口

## 這套的判斷順序
| 步驟 | 目的 | 產出 |
|---|---|---|
| router | 找出第一個該修的問題 | 該先用哪個 skill |
| hygiene | 清掉舊版干擾 | current-only scope |
| evidence | 檢查實際送進去的材料 | sent / excluded / unsupported |
| refusal | 擋住腦補 | `pending` / `not written` / `conflict` |
| one-step | 固定 baseline，只改一類條件 | 可歸因的 before/after |
| constraint | 把輸出壓回邊界內 | 更短、更準、更可驗證 |

## 這版最重要的原則
1. **先切 scope，再看答案。**
2. **先看 evidence，再改 prompt。**
3. **先處理第一個錯點，不要一次修全部。**
4. **沒寫就沒寫，不要補成看起來合理。**
5. **同一個 skill 只對一種 failure mode 負責。**

## 這套適合什麼情況
- 文件版本很亂
- 摘要開始亂編
- 回答看起來合理但沒證據
- 模型老是自己加步驟
- 你不想再靠「多寫幾句看看」碰運氣

## 不適合什麼情況
- 你就是要自由發揮的創作
- 你已經有嚴格版本控制與測試框架
- 你不打算驗證輸出是否可追溯

## 這版的特色語言
這套會一直圍繞四個詞：**current、archive、pending、conflict**。
它們不是裝飾，是控制輸出的硬邊界。
