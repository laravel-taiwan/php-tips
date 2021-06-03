# PHP 中有用的知識和陷阱

## 我忘了 PHP 函數的參數順序，它們是隨機的嗎？

經驗法則為：

**陣列函數**參數的順序為 「needle, haystack」，**字串函數**則相反，順序為 「haystack, needle」。

## 我應該如何保存「鹽」？

當使用 `password_hash()` 或者 `crypt()` 函數時， 「鹽」會被作為生成的 hash 值的一部分回傳。

你可以直接把完整的回傳值儲存到資料庫中，因為這個回傳值中已經包含了足夠的信息， 可以直接用在 `password_verify()` 或 `crypt()` 函數來進行密碼驗證。

下圖展示了 `crypt()` 或 `password_hash()` 函數回傳值的結構。 如你所見，演算法的資訊以及「鹽」都已經包含在回傳值中，在後續的密碼驗證中將會用到這些資訊。

![Crypt Structure](https://www.php.net/manual/zh/images/0af3dc557de5198c4312d2c38c08fbf0-crypt-text-rendered.svg)

## 下面程式碼怎麽沒有分成兩行顯示？
```php
<pre>
<?php echo "This should be the first line."; ?>
<?php echo "This should show up after the new line above."; ?>
</pre>
```

在 PHP 中，一段程式碼的結束標記，要嘛是`?>`，要嘛是`?>\n`（\n 表示換行）。因此在上面的例子中，輸出的句子將顯示在同一行中，因為 PHP 忽略了程式碼結束標記後面的換行。這意味著如果要輸出一個換行符號，需要在每段 PHP 程式碼的結束標記後面多加一個換行。

PHP 為什麽這麽做呢？因為在格式化正常的 HTML 時，這樣通常會更容易。假如輸出了換行而你不需要這個換行時，就不得不用一個非常長的行來達到這樣的效果，或者讓產生的 HTML 頁面的源文件的格式很難讀。



## 參考資料

- <https://segmentfault.com/a/1190000040084826>
- <https://www.php.net/manual/zh/faq.using.php>
