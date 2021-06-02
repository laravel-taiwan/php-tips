# PHP 中有用的知識和陷阱

## 我忘了 PHP 函數的參數順序，它們是隨機的嗎？

經驗法則為：

**陣列函數**參數的順序為 「needle, haystack」，**字串函數**則相反，順序為 「haystack, needle」。

## 我應該如何保存「鹽」？

當使用 `password_hash()` 或者 `crypt()` 函數時， 「鹽」會被作為生成的 hash 值的一部分回傳。

你可以直接把完整的回傳值儲存到資料庫中，因為這個回傳值中已經包含了足夠的信息， 可以直接用在 `password_verify()` 或 `crypt()` 函數來進行密碼驗證。

下圖展示了 `crypt()` 或 `password_hash()` 函數回傳值的結構。 如你所見，演算法的資訊以及「鹽」都已經包含在回傳值中，在後續的密碼驗證中將會用到這些資訊。

![Crypt Structure](https://www.php.net/manual/zh/images/0af3dc557de5198c4312d2c38c08fbf0-crypt-text-rendered.svg)


## 參考資料

<https://www.php.net/manual/zh/faq.using.php>
