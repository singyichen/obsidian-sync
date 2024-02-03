# Backend Framework Comparison

- [ ] [Express、Fastify、Hapi、Koa：Hello world 效能比較](https://medium.com/deno-the-complete-reference/express-vs-fastify-vs-hapi-vs-koa-hello-world-performance-comparison-dd8cd6866bdd "https://medium.com/deno-the-complete-reference/express-vs-fastify-vs-hapi-vs-koa-hello-world-performance-comparison-dd8cd6866bdd")
- [ ] [Node.js：2024 年最快的 Web 框架](https://medium.com/deno-the-complete-reference/node-js-the-fastest-web-framework-in-2024-fa11e513fa75 "https://medium.com/deno-the-complete-reference/node-js-the-fastest-web-framework-in-2024-fa11e513fa75")
- [ ] [如何為您的下一個 Node.js 應用程式選擇正確的框架。](https://dev.to/osam1010/how-to-choose-the-right-framework-for-your-next-nodejs-app-2c1e "https://dev.to/osam1010/how-to-choose-the-right-framework-for-your-next-nodejs-app-2c1e")
- [ ] [An Extensive Comparison of NodeJS Framework for 2023](https://externlabs.com/blogs/extensive-comparison-of-nodejs-framework/ "https://externlabs.com/blogs/extensive-comparison-of-nodejs-framework/")
- [ ] [Top NodeJS Frameworks for 2024](https://www.clickittech.com/developer/nodejs-frameworks/#h-what-are-the-top-nodejs-frameworks-for-backend)

# 比較表

| 框架 | Express | Fastify | Hapi | Koa |
| :--: | :--: | :--: | :--: | :--: |
| 特性 | 成熟、易用、流行 | 效能高、可擴充 | 安全、穩定、可控 | 精簡、優雅、高效 |
| 優點 | 社群資源豐富、介面方便、開發效率高 | 效能優異、擴充性強、支援 async/await | 安全性高、穩定性佳、可控性強 | 效能優異、程式碼簡潔、支援 async/await |
| 缺點 | 效能較低、不支援 async/await | 社群資源較少、部分功能需自行開發 | 學習曲線較陡、開發效率較低 | 社群資源較少、部分功能需自行開發 |
| 適合 | 初學者、小型專案 | 對效能有要求的專案 | 大型專案、對安全有要求的專案 | 對效能和程式碼風格有要求的專案 |
| 架構 | MVC、MVP | 插件式 | 插件式 | 洋蔥式 |
| 路由 | 簡單，支援多種路由方式 | 靈活，支援路由參數、路由群組等 | 靈活，支援路由驗證、路由授權等 | 靈活，支援路由中間件等 |
| 中間件 | 支援，但執行順序較為固定 | 支援，允許開發人員自定義執行順序 | 支援，允許開發人員自定義執行順序 | 支援，允許開發人員自定義執行順序 |
| 錯誤處理 | 簡單，但可以自定義錯誤處理函式 | 靈活，支援自定義錯誤處理函式和錯誤狀態碼 | 靈活，支援自定義錯誤處理函式和錯誤狀態碼 | 靈活，支援自定義錯誤處理函式和錯誤狀態碼 |
| 模板引擎 | 支援多種模板引擎，例如 EJS、Pug 等 | 支援多種模板引擎，例如 EJS、Pug 等 | 支援多種模板引擎，例如 EJS、Pug 等 | 支援多種模板引擎，例如 EJS、Pug 等 |
| 資料庫 | 支援多種資料庫，例如 MySQL、PostgreSQL 等 | 支援多種資料庫，例如 MySQL、PostgreSQL 等 | 支援多種資料庫，例如 MySQL、PostgreSQL 等 | 支援多種資料庫，例如 MySQL、PostgreSQL 等 |
| 驗證 | 支援多種驗證框架，例如 Passport、JWT 等 | 支援多種驗證框架，例如 Passport、JWT 等 | 支援多種驗證框架，例如 Passport、JWT 等 | 支援多種驗證框架，例如 Passport、JWT 等 |
| 效能 | 較低 | 優異 | 優異 | 優異 |
| 可擴充性 | 較差 | 優異 | 優異 | 優異 |
| 學習曲線 | 平緩 | 陡峭 | 陡峭 | 陡峭 |
| 社群資源 | 豐富 | 較少 | 較少 | 較少 |

## Express

Express 是最流行的 Node.js 框架之一，它擁有豐富的社群資源和大量的第三方套件。Express 提供了簡單易用的介面，可以幫助開發人員快速開發 Web 應用程式。

Express.js 是開源的 Node.js 模組，每週下載量約 1800 萬次，出現在超過 2 萬個堆疊中，全球超過 1,733 家公司使用。它是一款靈活且頂尖的 Node.js 框架，具備前沿的功能，使開發人員能夠建立穩健的單頁、多頁和混合網頁應用程式。

透過 Express.js，開發基於 Node.js 的應用程式變得快速且容易。它是一個迷你框架，可透過插件存取許多功能。Express.js 的原始開發者為 TJ Holowaychuk，於 2010 年 5 月 22 日首次發布。它廣泛用於許多知名公司，例如 Fox Sports、PayPal、Uber、IBM、Twitter、Stack、Accenture 等。

### Express.js 的主要功能

- 更快的伺服器端開發。
- 強勁效能 - 它提供薄薄的一層強大應用開發功能，而不會影響 Node.js 的能力。
- 許多工具都基於 Express.js。
- 動態渲染 HTML 頁面。
- 允許設置中間件以響應 HTTP 請求。
- 非常高的測試覆盖率。
- 高效路由。
- 內容協商。
- 可執行檔，可以用於快速生成應用程式。
- 除錯 - 該框架通过提供能够显示开发人员 bug 位置的调试功能，使调试变得非常容易。

### 何時使用 Express.js？

由於具備上述高端功能（詳細路由、配置、安全功能和除錯机制），此 Node.js 框架非常適合任何企業級或網絡應用程式。但建議在做出选择之前彻底比较 Node.js 框架。
## Fastify

Fastify 是近年來新興的 Node.js 框架，它以其高效能和可擴充性著稱。Fastify 採用了插件式的架構，允許開發人員根據需要靈活地擴充框架的功能。

## Hapi

Hapi 是另一個流行的 Node.js 框架，它以其安全性、穩定性和可控性著稱。Hapi 提供了一套完善的安全功能，並允許開發人員對應用程式的各個方面進行精細的控制。

## Koa

Koa 是 Express 的下一代框架，它在 Express 的基礎上進行了一些改進，提高了效能和靈活性。Koa 採用了更簡潔的介面，並提供了對 async/await 的支援。

Koa 是一個開源後端技術堆疊，每週下載量約為 100 萬次，存在於 400 多個堆疊中，並被多達 90 家公司使用。該框架將在版本 2 中實現巨大飛躍。它是由構建 Express 的同一組開發人員構建的。儘管如此，他們創建它的目的是提供更小、更具表現力的東西，並且可以為 Web 應用程式和 API 提供更強大的基礎。

該框架之所以脫穎而出，是因為它使用非同步函數，使您能夠消除回調並改善錯誤處理。Koa 利用各種工具和方法讓 Web 應用程式和 API 的編碼變得簡單又有趣。此框架不捆綁任何中間件。

該工具與其他流行的中間件技術類似；然而，它提供了一套方法來促進互通性、穩健性和中間件編碼的簡易性。簡而言之，Koa 提供的功能可以幫助開發人員更快、更高效率地建立 Web 應用程式和 API。

### Koa 的特點

以下是使 Koa 從其他最佳 Nodejs 框架中脫穎而出的一些關鍵功能：

- 此框架不與任何中間件捆綁。

- 佔用空間小——作為一個輕量級且靈活的工具，與其他 Nodejs 框架相比，它的佔用空間更小。儘管如此，您仍然可以靈活地使用插件擴展框架 - 您可以插入各種模組。

- 現代框架 – Koa 使用最新技術和規範建構（ECMAScript 2015）。因此，用它開發的程式可能會在很長一段時間內具有相關性。

- 錯誤處理 – 此框架具有簡化錯誤處理並使程式設計師更容易發現和消除錯誤的功能。這使得 Web 應用程式的崩潰或問題最少。

- 更快的開發——頂級 Nodejs 框架的核心目標之一是讓[軟體開發](https://www.clickittech.com/software-development/)更快、更有趣。Koa 是一個輕量級、靈活的框架，以其未來技術幫助開發者加速開發。

### 何時使用 Koa？

同一團隊開發了 Koa 和 Express。Express 提供了「增強節點」的功能，而 Koa 的創建目標是「修復和替換 Node」。它之所以脫穎而出，是因為它可以簡化錯誤處理並使應用程式擺脫回調地獄。Koa 公開了其 ctx.request 和 ctx.response 對象，而不是 Node 的 req 和 res 對象。

另一方面，Express 透過路由和模板等額外功能增強了節點的 req 和 res 對象，而 Koa 則沒有這些功能。如果您想要擺脫回調，那麼它是理想的框架，而當您想要實作 Nodejs 和傳統 Nodejs 風格的編碼時，Express 則適合。