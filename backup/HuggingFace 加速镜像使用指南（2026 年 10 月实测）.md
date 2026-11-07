镜像地址 | 定位 | 说明
-- | -- | --
[https://hf-mirror.com](https://hf-mirror.com) | 首选 | 稳定可用，下载速度约为直连的2倍
[https://aifasthub.com](https://aifasthub.com) | 备用 | 速度略快于直连，可作备选方案
[https://modelscope.cn](https://modelscope.cn)（魔搭社区） | 国产模型首选 | 非镜像站点，官方维护，国产模型资源更全、下载更快


<h2>使用方法</h2>
<h3>用法一：网页直接替换域名</h3>
<p>将下载链接中的 <code>huggingface.co</code> 替换为镜像域名，其余路径保持不变。
示例：</p>
<pre style="white-space: pre; font-family: Consolas, Monaco, &quot;Courier New&quot;, monospace;"><code># 原始官方链接
[https://huggingface.co/gpt2/resolve/main/config.json](https://huggingface.co/gpt2/resolve/main/config.json)
# 替换为镜像后
[https://hf-mirror.com/gpt2/resolve/main/config.json](https://hf-mirror.com/gpt2/resolve/main/config.json)
</code></pre>
<h3>用法二：HF_ENDPOINT 环境变量（推荐）</h3>
<p><code>huggingface_hub</code>、<code>transformers</code>、<code>datasets</code> 等官方工具链均原生支持该环境变量，设置一次全局生效，无需修改代码。</p>
<ul style="list-style-type: disc;">
<li>Linux / macOS（写入 <code>~/.bashrc</code> 或 <code>~/.zshrc</code> 可永久生效）</li>
</ul>
<pre style="white-space: pre; font-family: Consolas, Monaco, &quot;Courier New&quot;, monospace;"><code>export HF_ENDPOINT=[https://hf-mirror.com](https://hf-mirror.com)
</code></pre>
<ul style="list-style-type: disc;">
<li>Windows PowerShell</li>
</ul>
<pre style="white-space: pre; font-family: Consolas, Monaco, &quot;Courier New&quot;, monospace;"><code>$env:HF_ENDPOINT = "[https://hf-mirror.com](https://hf-mirror.com)"
</code></pre>
<p>设置完成后，官方命令可直接正常使用，自动走镜像通道：</p>
<pre style="white-space: pre; font-family: Consolas, Monaco, &quot;Courier New&quot;, monospace;"><code>pip install -U "huggingface_hub[cli]"
hf download gpt2
</code></pre>
<p>Python 代码中的 <code>from_pretrained()</code> 方法也会自动适配该环境变量。</p>
<h3>用法三：国产模型优先使用魔搭社区</h3>
<p>通义千问、DeepSeek、GLM 等国产模型，在 ModelScope（魔搭社区）通常下载速度更快、资源更完整，配套官方 SDK：</p>
<pre style="white-space: pre; font-family: Consolas, Monaco, &quot;Courier New&quot;, monospace;"><code>pip install modelscope
modelscope download --model Qwen/Qwen2-0.5B
</code></pre>
<h2>常见问题</h2>
<ol style="list-style-type: decimal;">
<li><strong>为什么直连时好时坏？</strong>
HuggingFace 的页面与文件分布在多个域名和 CDN 节点上，国内到这些节点的路由波动较大，连通性和速度都不稳定。</li>
<li><strong>镜像站点安全吗？</strong>
镜像本质是中转代理，理论上可以获取传输内容。请勿在镜像站点登录 HuggingFace 账号，不要通过镜像拉取需要授权的私有模型；公开模型下载后，可比对官方页面公布的文件哈希值校验完整性。</li>
<li><strong>hf-mirror 会失效吗？</strong>
存在失效可能。这类服务多为社区公益维护，建议收藏原页面，失效时查看最新可用列表。</li>
</ol>
