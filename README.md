

# 本仓库的目的是通过GitHub建立一个图床，上传资源图片，通过jsDelivr快速获取图片。

---

#### 以下为创建图床的方法，并通过jsDelivr快速加载图片。


<div id="article_content" class="article_content clearfix">
            <link rel="stylesheet" href="https://csdnimg.cn/release/phoenix/template/css/ck_htmledit_views-3d4dc5c1de.css">
                            <div class="htmledit_views" id="content_views">
                                            <p><img alt="" class="has" height="721" src="https://img-blog.csdnimg.cn/20190929011105652.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0NRRzE5ODg=,size_16,color_FFFFFF,t_70" width="1184"></p>

<p>jsDelivr 是国外的一家优秀的公共 CDN 服务提供商，也是首个「打通中国大陆（网宿公司运营）与海外的免费 CDN 服务」<a href="https://blog.iljw.me/2019/05/jsdelivr-cdn-github.html#fn1" rel="nofollow" id="fnref1">1</a>。jsDelivr 有一个十分好用的功能——<strong>它可以加速 Github 仓库的文件</strong>。我们可以借此搭建一个免费、全球访问速度超快的图床。</p>
<p><strong>声明：静态文件主要是缓存在 jsDelivr 的 CDN 节点上，确保 GitHub 承受最小的负载，并且你还可以从 GitHub 仓库获得快速简便的静态文件托管。</strong></p>
<blockquote>
<p>jsDelivr is a public, open-source CDN (Content Delivery Network) developed by <a href="https://prospectone.io/" rel="nofollow">ProspectOne</a>, focused on performance, reliability, and security. It is free to use for everyone, with no bandwidth limits<a href="https://blog.iljw.me/2019/05/jsdelivr-cdn-github.html#fn2" rel="nofollow" id="fnref2">2</a>.</p>

<p>jsDelivr is the only public CDN with a valid ICP license issued by the Chinese government, and hundreds of locations directly in Mainland China<a href="https://blog.iljw.me/2019/05/jsdelivr-cdn-github.html#fn1" rel="nofollow" id="fnref1:1">1</a>.</p>
</blockquote>

<h3 id="主要思路"><a name="t0"></a><a name="t0"></a>主要思路</h3>
<p>使用 PicGo<a href="https://blog.iljw.me/2019/05/jsdelivr-cdn-github.html#fn3" rel="nofollow" id="fnref3">3</a>将图片上传到指定 Github 仓库位置，再利用 jsDelivr 获得图片加速后的 url。</p>
<p>使用效果：<a href="https://cdn.jsdelivr.net/gh/joeyliu6/Blogger@master/static_files/iljw/img/large/20190512151852.png" rel="nofollow">点击访问测试图片</a></p>
<h3 id="github-配置"><a name="t1"></a><a name="t1"></a>Github 配置</h3>
<p>首先你先得<a href="https://wiki.jikexueyuan.com/project/github-basics/creat-new-repo.html" rel="nofollow">创建一个 Github 仓库</a><a href="https://blog.iljw.me/2019/05/jsdelivr-cdn-github.html#fn4" rel="nofollow" id="fnref4">4</a>，并获取一个 token（它可以让程序拥有控制仓库的权限）。</p>
<ol><li>访问 <a href="https://github.com/settings/tokens%EF%BC%8C">https://github.com/settings/tokens，</a></li>
	<li><img alt="" class="has" src="https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2pvZXlsaXU2L0Jsb2dnZXJAbWFzdGVyL3N0YXRpY19maWxlcy9pbGp3L2ltZy9sYXJnZS8yMDE5MDUxMjE1MzQ0NC5wbmc?x-oss-process=image/format,png"></li>
	<li><img alt="" class="has" src="https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2pvZXlsaXU2L0Jsb2dnZXJAbWFzdGVyL3N0YXRpY19maWxlcy9pbGp3L2ltZy9sYXJnZS8yMDE5MDUxMjE1MzczMi5wbmc?x-oss-process=image/format,png"></li>
	<li>拉到最下面，点击 <code>Generate token</code>，生成并复制。</li>
</ol><h3 id="picgo-配置"><a name="t2"></a><a name="t2"></a>PicGo 配置</h3>

<ol><li>在<a href="https://github.com/Molunerfinn/PicGo/releases">此处</a>下载，Windows 系统就选 <code>.exe</code> 结尾的下；</li>
	<li>安装，打开 PicGo，在「图床设置」处配置 Github 图床；</li>
	<li><img alt="" class="has" src="https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2pvZXlsaXU2L0Jsb2dnZXJAbWFzdGVyL3N0YXRpY19maWxlcy9pbGp3L2ltZy9sYXJnZS8yMDE5MDUxMjE1NDUyOS5wbmc?x-oss-process=image/format,png"><ol><li>设定仓库名：填入你上面创建的仓库名，格式为：<code>用户名/仓库名；</code></li>
		<li>设定分支名：一般填写 <code>master</code> 就行了<a href="https://blog.iljw.me/2019/05/jsdelivr-cdn-github.html#fn5" rel="nofollow" id="fnref5">5</a>；</li>
		<li>设定 Token：将 Github 配置中得到的 Token 粘贴进去；</li>
		<li>指定存储路径：你想要把图片放在仓库的哪个位置，比如我是：<code>static_files/iljw/img/large</code>，Github 对应的是：<img alt="" class="has" src="https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2pvZXlsaXU2L0Jsb2dnZXJAbWFzdGVyL3N0YXRpY19maWxlcy9pbGp3L2ltZy9sYXJnZS8yMDE5MDUxMjE1NTUxOS5wbmc?x-oss-process=image/format,png"></li>
	</ol></li>
</ol><h3 id="jsdelivr-配置"><a name="t3"></a><a name="t3"></a>jsDelivr 配置</h3>

<p>其实就是上一节 PicGo 配置的最后一条——设定自定义域名。我的设定是：</p>
<pre class="has" name="code"><code class="hljs ruby"><span class="hljs-symbol">https:</span>/<span class="hljs-regexp">/cdn.jsdelivr.net/gh</span><span class="hljs-regexp">/joeyliu6/</span>Blogger@master
</code><div class="hljs-button {2}" data-title="复制" onclick="hljs.copyCode(event)"></div></pre>

<p>其中<a href="https://blog.iljw.me/2019/05/jsdelivr-cdn-github.html#fn6" rel="nofollow" id="fnref6">6</a><a href="https://blog.iljw.me/2019/05/jsdelivr-cdn-github.html#fn7" rel="nofollow" id="fnref7">7</a>：</p>
<ul><li><code>gh</code> 表示来自 Github 的仓库</li>
	<li><code>joeyliu6/Blogger</code> 仓库的具体位置</li>
	<li><code>master</code> 仓库的分支</li>
</ul><p>好的，在此就配置完成。图片链接形式如下：</p>

<pre class="has" name="code"><code class="hljs ruby"><span class="hljs-symbol">https:</span>/<span class="hljs-regexp">/cdn.jsdelivr.net/gh</span><span class="hljs-regexp">/joeyliu6/</span>Blogger@master/static_files/iljw/img/large/<span class="hljs-number">20190512151852</span>.png
</code><div class="hljs-button {2}" data-title="复制" onclick="hljs.copyCode(event)"></div></pre>

<p><img alt="" class="has" src="https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2pvZXlsaXU2L0Jsb2dnZXJAbWFzdGVyL3N0YXRpY19maWxlcy9pbGp3L2ltZy9sYXJnZS8yMDE5MDUxMjE1NTkzOC5wbmc?x-oss-process=image/format,png"></p>
<p>你可以通过 PicGo 方便地上传图片了，它支持拖拽、点击、剪贴板上传，上传后，图片链接直接复制的你的剪贴板中。</p>
<p>当然，你也可以通过 Git 命令，将本地图片批量上传到 Github 上，再替换成原文中的图片链接地址，以完成图片迁移的工作。</p>
<h3 id="结语"><a name="t4"></a><a name="t4"></a>结语</h3>
<p>整个过程比较简单，创建 Github 仓库，并获取 token，填入 PicGo 配置即可完成。</p>
<ul><li>使用 jsDelivr 加速静态文件访问，能够优化博客体验。</li>
	<li>在 Github 存储图片，利于博主对于图片的掌控。</li>
	<li>使用 PicGo 的原因是因为能够方便地将上传图片到 Github，并直接获取 jsDelivr 的加速后的图片地址。</li>
</ul>                                    </div><div data-report-view="{&quot;mod&quot;:&quot;1585297308_001&quot;,&quot;dest&quot;:&quot;https://blog.csdn.net/CQG1988/article/details/101652805&quot;,&quot;extend1&quot;:&quot;pc&quot;,&quot;ab&quot;:&quot;new&quot;}"><div></div></div>
