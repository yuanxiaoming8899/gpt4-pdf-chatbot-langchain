<div class="Box-sc-g0xbh4-0 bJMeLZ js-snippet-clipboard-copy-unpositioned" data-hpc="true"><article class="markdown-body entry-content container-lg" itemprop="text"><div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">GPT-4 &amp; LangChain - 为您的 PDF 文件创建 ChatGPT 聊天机器人</font></font></h1><a id="user-content-gpt-4--langchain---create-a-chatgpt-chatbot-for-your-pdf-files" class="anchor" aria-label="永久链接：GPT-4 和 LangChain - 为您的 PDF 文件创建 ChatGPT 聊天机器人" href="#gpt-4--langchain---create-a-chatgpt-chatbot-for-your-pdf-files"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用新的 GPT-4 api 为多个大型 PDF 文件构建 chatGPT 聊天机器人。</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用的技术堆栈包括 LangChain、Pinecone、Typescript、Openai 和 Next.js。LangChain 是一个框架，可以更轻松地构建可扩展的 AI/LLM 应用程序和聊天机器人。Pinecone 是一个矢量存储，用于以文本形式存储嵌入和 PDF，以便以后检索类似的文档。</font></font></p>
<p dir="auto"><a href="https://www.youtube.com/watch?v=ih9PBGVVOO4" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">教程视频</font></font></a></p>
<p dir="auto"><a href="https://discord.gg/E4Mc77qwjm" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果你有任何问题，请加入 discord</font></font></a></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这个 repo 和教程的视觉指南位于</font></font><code>visual guide</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件夹中。</font></font></p>
<p dir="auto"><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果遇到错误，请查看本页下方的故障排除部分。</font></font></strong></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">前言：请确保您已经在系统上下载了节点，并且版本为18或更高。</font></font></p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">发展</font></font></h2><a id="user-content-development" class="anchor" aria-label="固定链接：开发" href="#development"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="auto">
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">克隆 repo 或下载 ZIP</font></font></li>
</ol>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>git clone [github https url]
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="git clone [github https url]" tabindex="0" role="button">
     
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<ol start="2" dir="auto">
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">安装软件包</font></font></li>
</ol>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">首先运行</font></font><code>npm install yarn -g</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以全局安装 yarn（如果还没有安装的话）。</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后运行：</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>yarn install
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="yarn install" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">安装后，您现在应该看到一个</font></font><code>node_modules</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件夹。</font></font></p>
<ol start="3" dir="auto">
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">设置你的</font></font><code>.env</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件</font></font></li>
</ol>
<ul dir="auto">
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">复制到</font><font style="vertical-align: inherit;">
您的文件</font></font><code>.env.example</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中</font><font style="vertical-align: inherit;">应如下所示：</font></font><code>.env</code><font style="vertical-align: inherit;"></font><code>.env</code><font style="vertical-align: inherit;"></font></li>
</ul>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>OPENAI_API_KEY=

PINECONE_API_KEY=
PINECONE_ENVIRONMENT=

PINECONE_INDEX_NAME=

</code></pre><div class="zeroclipboard-container">
   
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<ul dir="auto">
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">访问</font></font><a href="https://help.openai.com/en/articles/4936850-where-do-i-find-my-secret-api-key" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">openai</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">来检索 API 密钥并插入到您的</font></font><code>.env</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件中。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">访问</font></font><a href="https://pinecone.io/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">pinecone</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">来创建和检索您的 API 密钥，并从仪表板检索您的环境和索引名称。</font></font></li>
</ul>
<ol start="4" dir="auto">
<li>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在</font></font><code>config</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件夹中，将 替换</font></font><code>PINECONE_NAME_SPACE</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为</font></font><code>namespace</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您在运行 时想要在 Pinecone 上存储嵌入的位置</font></font><code>npm run ingest</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。此命名空间稍后将用于查询和检索。</font></font></p>
</li>
<li>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在</font></font><code>utils/makechain.ts</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">链中将 更改</font></font><code>QA_PROMPT</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为您自己的用例。</font><font style="vertical-align: inherit;">如果您有权访问 api，请将</font><font style="vertical-align: inherit;">更改为</font></font><code>modelName</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">请在此 repo 之外验证您是否有权访问</font><font style="vertical-align: inherit;">api，否则应用程序将无法运行。</font></font><code>new OpenAI</code><font style="vertical-align: inherit;"></font><code>gpt-4</code><font style="vertical-align: inherit;"></font><code>gpt-4</code><font style="vertical-align: inherit;"></font><code>gpt-4</code><font style="vertical-align: inherit;"></font></p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将您的 PDF 文件转换为嵌入</font></font></h2><a id="user-content-convert-your-pdf-files-to-embeddings" class="anchor" aria-label="永久链接：将您的 PDF 文件转换为嵌入" href="#convert-your-pdf-files-to-embeddings"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此 repo 可以加载多个 PDF 文件</font></font></strong></p>
<ol dir="auto">
<li>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在文件夹内</font></font><code>docs</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，添加您的 pdf 文件或包含 pdf 文件的文件夹。</font></font></p>
</li>
<li>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">运行脚本</font></font><code>yarn run ingest</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以“提取”并嵌入您的文档。如果遇到错误，请按照下面的方法进行故障排除。</font></font></p>
</li>
<li>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">检查 Pinecone 仪表板以验证您的命名空间和向量是否已添加。</font></font></p>
</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">运行应用</font></font></h2><a id="user-content-run-the-app" class="anchor" aria-label="永久链接：运行应用程序" href="#run-the-app"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一旦您验证嵌入和内容已成功添加到您的 Pinecone，您可以运行该应用程序</font></font><code>npm run dev</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">来启动本地开发环境，然后在聊天界面中输入问题。</font></font></p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">故障排除</font></font></h2><a id="user-content-troubleshooting" class="anchor" aria-label="永久链接：故障排除" href="#troubleshooting"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一般来说，请留意</font><font style="vertical-align: inherit;">此 repo 的</font></font><code>issues</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和部分以寻找解决方案。</font></font><code>discussions</code><font style="vertical-align: inherit;"></font></p>
<p dir="auto"><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一般错误</font></font></strong></p>
<ul dir="auto">
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">确保你正在运行最新的 Node 版本。运行</font></font><code>node -v</code></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">尝试使用其他 PDF 或先将 PDF 转换为文本。您的 PDF 可能已损坏、扫描或需要 OCR 才能转换为文本。</font></font></li>
<li><code>Console.log</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">变量</font></font><code>env</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并确保它们被暴露。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">确保您使用的 LangChain 和 Pinecone 版本与此 repo 相同。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">检查您是否已创建</font></font><code>.env</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">包含有效（且可用）的 API 密钥、环境和索引名称的文件。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您进行更改</font></font><code>modelName</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><code>OpenAI</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">请确保您可以访问相应模型的 API。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">确保您的账单账户上有足够的 OpenAI 积分和有效的卡。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">检查您的全局环境中是否没有多个 OPENAPI 密钥。如果有，</font></font><code>env</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">项目中的本地文件将被系统</font></font><code>env</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">变量覆盖。</font></font></li>
<li><font style="vertical-align: inherit;"></font><code>process.env</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果仍然存在问题，</font><font style="vertical-align: inherit;">请尝试将 API 密钥硬编码到变量中。</font></font></li>
</ul>
<p dir="auto"><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">松果错误</font></font></strong></p>
<ul dir="auto">
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">确保您的松果仪表板</font></font><code>environment</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">与</font><font style="vertical-align: inherit;">和文件</font></font><code>index</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中的仪表板相匹配</font><font style="vertical-align: inherit;">。</font></font><code>pinecone.ts</code><font style="vertical-align: inherit;"></font><code>.env</code><font style="vertical-align: inherit;"></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">检查您是否已将矢量尺寸设置为</font></font><code>1536</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">确保您的松果命名空间是小写的。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Starter（免费）计划中用户的 Pinecone 索引在 7 天不活动后将被删除。为防止这种情况，请在 7 天之前向 Pinecone 发送 API 请求以重置计数器。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用新的 Pinecone 项目、索引和克隆的 repo 从头重试。</font></font></li>
</ul>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">信用</font></font></h2><a id="user-content-credit" class="anchor" aria-label="永久链接：信用" href="#credit"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此 repo 的前端灵感来自</font></font><a href="https://github.com/zahidkhawaja/langchain-chat-nextjs"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">langchain-chat-nextjs</font></font></a></p>
</article></div>
