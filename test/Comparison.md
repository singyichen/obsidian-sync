# Backend Framework Comparison

- [ ] [Express、Fastify、Hapi、Koa：Hello world 效能比較](https://medium.com/deno-the-complete-reference/express-vs-fastify-vs-hapi-vs-koa-hello-world-performance-comparison-dd8cd6866bdd "https://medium.com/deno-the-complete-reference/express-vs-fastify-vs-hapi-vs-koa-hello-world-performance-comparison-dd8cd6866bdd")
- [ ] [Node.js：2024 年最快的 Web 框架](https://medium.com/deno-the-complete-reference/node-js-the-fastest-web-framework-in-2024-fa11e513fa75 "https://medium.com/deno-the-complete-reference/node-js-the-fastest-web-framework-in-2024-fa11e513fa75")
- [ ] [如何為您的下一個 Node.js 應用程式選擇正確的框架。](https://dev.to/osam1010/how-to-choose-the-right-framework-for-your-next-nodejs-app-2c1e "https://dev.to/osam1010/how-to-choose-the-right-framework-for-your-next-nodejs-app-2c1e")
- [ ] [An Extensive Comparison of NodeJS Framework for 2023](https://externlabs.com/blogs/extensive-comparison-of-nodejs-framework/ "https://externlabs.com/blogs/extensive-comparison-of-nodejs-framework/")

# 比較表

|   框架   |                  Express                  |                  Fastify                  | Hapi                                      | Koa                                       |
|:--------:|:-----------------------------------------:|:-----------------------------------------:| ----------------------------------------- | ----------------------------------------- |
|   特性   |             成熟、易用、流行              |              效能高、可擴充               | 安全、穩定、可控                          | 精簡、優雅、高效                          |
|   優點   |    社群資源豐富、介面方便、開發效率高     |   效能優異、擴充性強、支援 async/await    | 安全性高、穩定性佳、可控性強              | 效能優異、程式碼簡潔、支援 async/await    |
|   缺點   |       效能較低、不支援 async/await        |     社群資源較少、部分功能需自行開發      | 學習曲線較陡、開發效率較低                | 社群資源較少、部分功能需自行開發          |
|   適合   |             初學者、小型專案              |            對效能有要求的專案             | 大型專案、對安全有要求的專案              | 對效能和程式碼風格有要求的專案            |
|   架構   |                 MVC、MVP                  |                  插件式                   | 插件式                                    | 洋蔥式                                    |
|   路由   |          簡單，支援多種路由方式           |      靈活，支援路由參數、路由群組等       | 靈活，支援路由驗證、路由授權等            | 靈活，支援路由中間件等                    |
|  中間件  |         支援，但執行順序較為固定          |     支援，允許開發人員自定義執行順序      | 支援，允許開發人員自定義執行順序          | 支援，允許開發人員自定義執行順序          |
| 錯誤處理 |      簡單，但可以自定義錯誤處理函式       | 靈活，支援自定義錯誤處理函式和錯誤狀態碼  | 靈活，支援自定義錯誤處理函式和錯誤狀態碼  | 靈活，支援自定義錯誤處理函式和錯誤狀態碼  |
| 模板引擎 |    支援多種模板引擎，例如 EJS、Pug 等     |    支援多種模板引擎，例如 EJS、Pug 等     | 支援多種模板引擎，例如 EJS、Pug 等        | 支援多種模板引擎，例如 EJS、Pug 等        |
|  資料庫  | 支援多種資料庫，例如 MySQL、PostgreSQL 等 | 支援多種資料庫，例如 MySQL、PostgreSQL 等 | 支援多種資料庫，例如 MySQL、PostgreSQL 等 | 支援多種資料庫，例如 MySQL、PostgreSQL 等 |
|   驗證   |  支援多種驗證框架，例如 Passport、JWT 等  |  支援多種驗證框架，例如 Passport、JWT 等  | 支援多種驗證框架，例如 Passport、JWT 等   | 支援多種驗證框架，例如 Passport、JWT 等   |
|   效能   |                   較低                    |                   優異                    | 優異                                      | 優異                                      |
| 可擴充性 |                   較差                    |                   優異                    | 優異                                      | 優異                                      |
| 學習曲線 |                   平緩                    |                   陡峭                    | 陡峭                                      | 陡峭                                      |
| 社群資源 |                   豐富                    |                   較少                    | 較少                                      | 較少                                      |

## Express

Express 是最流行的 Node.js 框架之一，它擁有豐富的社群資源和大量的第三方套件。Express 提供了簡單易用的介面，可以幫助開發人員快速開發 Web 應用程式。

## Fastify

Fastify 是近年來新興的 Node.js 框架，它以其高效能和可擴充性著稱。Fastify 採用了插件式的架構，允許開發人員根據需要靈活地擴充框架的功能。

## Hapi

Hapi 是另一個流行的 Node.js 框架，它以其安全性、穩定性和可控性著稱。Hapi 提供了一套完善的安全功能，並允許開發人員對應用程式的各個方面進行精細的控制。

## Koa

Koa 是 Express 的下一代框架，它在 Express 的基礎上進行了一些改進，提高了效能和靈活性。Koa 採用了更簡潔的介面，並提供了對 async/await 的支援。