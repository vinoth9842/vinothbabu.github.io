---
layout: post
title: How I Build This Site
author: Rangsiman Ketkaew
date: "2019-07-26 01:29:00 +0700"
category:
  - HTML
  - web-development
summary: Example of style code I use to write this site
thumbnail: posts/html.png
permalink: content/6
comments: true
---

<br>

<h1 class="card-title">How I Build This Site</h1>
  <br>
  <h3><a id="Platform_and_Service_12"></a>Platform and Service</h3>
  <ul>
    <li>Github</li>
    <li>Jekyll</li>
    <li>Disqus</li>
    <li>MailChimp</li>
    <li>MakerWidget</li>
  </ul>
  <h3><a id="Programming_language_20"></a>Programming language</h3>
  <ul>
    <li>Markdown</li>
    <li>Ruby/Gem</li>
    <li>HTML/CSS</li>
    <li>Python</li>
    <li>IPython notebook</li>
  </ul>
  <h3><a id="IDE_and_extensions_28"></a>IDE and extensions</h3>
  <ul>
    <li>
      Visual Studio Code
      <ul>
        <li>Markdown All in one</li>
        <li>Markdown Shortcuts</li>
        <li>markdownlint</li>
        <li>Live Server</li>
        <li>Live Server Preview</li>
        <li>File Utils</li>
        <li>Auto Close Tag</li>
        <li>Auto Rename Tag</li>
        <li>Bracket Pair Colorizer</li>
      </ul>
    </li>
    <li>
      Vi/Vim
      <ul>
        <li>NERDTree</li>
      </ul>
    </li>
  </ul>
  <h3><a id="Other_tools_43"></a>Other tools</h3>
  <ul>
    <li>Jupyter Notebook</li>
    <li>Jupyter Book</li>
    <li><a href="https://nbviewer.jupyter.org/">nbviewer</a></li>
  </ul>
  <h3><a id="Jupyter_commandline_49"></a>Jupyter command-line</h3>
  <ul>
    <li>Merge multiple .ipynb files into one file</li>
  </ul>
  <pre><code>pip install nbmerge
</code></pre>
  <ul>
    <li>Convert .ipynb to .html (by default)</li>
  </ul>
  <pre><code>jupyter nbconvert NOTEBOOK.ipynb
</code></pre>
  <ul>
    <li>Convert .ipynb to .html (by default)</li>
  </ul>
  <pre><code>jupyter nbconvert NOTEBOOK.ipynb --to html
</code></pre>
  <ul>
    <li>Execute notebook and replace file</li>
  </ul>
  <pre><code>jupyter nbconvert NOTEBOOK.ipynb --execute
</code></pre>
  <ul>
    <li>Execute notebook and save as .html file</li>
  </ul>
  <pre><code>jupyter nbconvert NOTEBOOK.ipynb --execute --to html
</code></pre>
  <h3><a id="Convert_md_to_html_81"></a>Convert .md to .html</h3>
  <ul>
    <li>Use markdown2</li>
  </ul>
  <pre><code>pip install markdown2
</code></pre>
  <ul>
    <li>Use markdown-to-html</li>
  </ul>
  <p>
    <a href="https://www.npmjs.com/package/markdown-to-html"
      >https://www.npmjs.com/package/markdown-to-html</a
    >
  </p>
  <ul>
    <li>Use pandoc</li>
  </ul>
  <p>
    <a href="https://www.npmjs.com/package/markdown-to-html"
      >https://pandoc.org/getting-started.html</a
    >
  </p>

  <hr />

  ### HTML in Markdown

  <img src="/assets/img/test-and-wow.jpg" width="100%" height="auto" />

  <p>
    Lets try the different text styles <b> Bold </b> ,
    <strong> Strong </strong>, <em> Emphasis </em>, <i> Italic </i>
  </p>

  <p>Now, lets try different heading styles :</p>

  <code class="inlinecode"><h1>Hello in h1 !</h1></code>

  <h1>Hello in h1 !</h1>
  <code class="inlinecode"><h2>Hello in h2 !</h2></code>
  <h2>Hello in h2 !</h2>
  <code class="inlinecode"><h3>Hello in h3 !</h3></code>
  <h3>Hello in h3 !</h3>
  <code class="inlinecode"><h4>Hello in h4 !</h4></code>
  <h4>Hello in h4 !</h4>
  <code class="inlinecode"><h5>Hello in h5 !</h5></code>
  <h5>Hello in h5 !</h5>
  <code class="inlinecode"><h6>Hello in h6 !</h6></code>
  <h6>Hello in h6 !</h6>
  <code class="inlinecode"><h6 align="left">Hello in h6 at left !</h6></code>
  <h6 align="left">Hello in h6 at left !</h6>
  <code class="inlinecode"
    ><h6 align="center">Hello in h6 at center !</h6></code
  >
  <h6 align="center">Hello in h6 at center !</h6>
  <code class="inlinecode"><h6 align="right">Hello in h6 at right !</h6></code>
  <h6 align="right">Hello in h6 at right !</h6>

  <hr />

  <blockquote>
    <p>This is a Block Quote, It can Expand Multiple Lines</p>
  </blockquote>

  <p>You can use the mark tag to <mark>highlight</mark> text.</p>

  <p><del> This line of text is meant to be deleted text </del></p>

  <p><u>This line of text will render as underlined</u></p>
  <p><small>This line of text is meant to be treated as fine print.</small></p>
  <p><strong>This line rendered as bold text.</strong></p>
  <p><em>This line rendered as italicized text.</em></p>
  <p><abbr title="attribute">attr</abbr></p>
  <p><abbr title="HyperText Markup Language" class="initialism">HTML</abbr></p>

  <hr />
  >

  <p>Unordered List</p>

  <ul>
    <li>List Item 1</li>
    <li>List Item 2</li>
    <li>List Item 3</li>
    <li>List Item 4</li>
    <li>List Item 5</li>
  </ul>

  <p>Ordered List</p>
  <ol>
    <li>List Item 1</li>
    <li>List Item 2</li>
    <li>List Item 3</li>
    <li>List Item 4</li>
    <li>List Item 5</li>
  </ol>

  <hr />

  <div class="responsive-table">
    <table>
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Heading</th>
          <th scope="col">Heading</th>
          <th scope="col">Heading</th>
          <th scope="col">Heading</th>
          <th scope="col">Heading</th>
          <th scope="col">Heading</th>
          <th scope="col">Heading</th>
          <th scope="col">Heading</th>
          <th scope="col">Heading</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th scope="row">1</th>
          <td>Cell</td>
          <td>Cell</td>
          <td>Cell</td>
          <td>Cell</td>
          <td>Cell</td>
          <td>Cell</td>
          <td>Cell</td>
          <td>Cell</td>
          <td>Cell</td>
        </tr>
        <tr>
          <th scope="row">2</th>
          <td>Cell</td>
          <td>Cell</td>
          <td>Cell</td>
          <td>Cell</td>
          <td>Cell</td>
          <td>Cell</td>
          <td>Cell</td>
          <td>Cell</td>
          <td>Cell</td>
        </tr>
        <tr>
          <th scope="row">3</th>
          <td>Cell</td>
          <td>Cell</td>
          <td>Cell</td>
          <td>Cell</td>
          <td>Cell</td>
          <td>Cell</td>
          <td>Cell</td>
          <td>Cell</td>
          <td>Cell</td>
        </tr>
      </tbody>
    </table>
  </div>

  <hr />

  <h3 id="syntax-highlighting">Syntax Highlighting</h3>

  <p>
    You can add inline code just like this using &lt;code&gt;, e.g.
    <code class="inlinecode">i am code</code>
  </p>

  <p>This is block code using &lt;pre&gt;&lt;code&gt;.</p>
  <pre><code>&lt;pre&gt;&lt;code&gt;
function Panel(element, canClose, closeHandler) {
  this.element = element;
  this.canClose = canClose;
  this.closeHandler = function () { if (closeHandler) closeHandler() };
&lt;/pre&gt;&lt;/code&gt;
</code></pre>

  <pre><code>&lt;pre&gt;&lt;code&gt;
This line is so longggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggg.
&lt;/pre&gt;&lt;/code&gt;
</code></pre>

  <hr />

  <h3 id="github-gist-embed">GitHub gist Embed</h3>

  <script src="https://gist.github.com/ahmadajmi/dbb4f713317721668bcbc39420562afc.js"></script>

  <hr />

  <h3>YouTube Responsive Embed</h3>

  <iframe 
    width="560" 
    height="315" 
    src="https://www.youtube.com/embed/C0Qaf-UJ2XQ" 
    title="YouTube video player" 
    frameborder="0" 
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
    allowfullscreen
  ></iframe>

  <hr />

  <h3>Vimeo Responsive Embed</h3>

  <iframe
    src="https://player.vimeo.com/video/212114694?title=0&amp;byline=0&amp;portrait=0"
    width="640"
    height="360"
    frameborder="0"
    webkitallowfullscreen=""
    mozallowfullscreen=""
    allowfullscreen=""
  ></iframe>

  <hr />

  <h3 id="ted-responsive-embed">TED Responsive Embed</h3>

  <iframe
    src="https://embed.ted.com/talks/ted_halstead_a_climate_solution_where_all_sides_can_win"
    width="640"
    height="360"
    frameborder="0"
    scrolling="no"
    allowfullscreen=""
  ></iframe>

  <hr />

  <h3 id="twitch-responsive-embed">Twitch Responsive Embed</h3>

  <iframe src="https://player.twitch.tv/?video=799499623&parent=www.example.com" frameborder="0" allowfullscreen="true" scrolling="no" height="378" width="620"></iframe>

  <hr />

  <h3 id="soundcloud-embed">SoundCloud Embed</h3>

  <iframe width="100%" height="300" scrolling="no" frameborder="no" allow="autoplay" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/632953275&color=%23ff5500&auto_play=false&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true&visual=true"></iframe><div style="font-size: 10px; color: #cccccc;line-break: anywhere;word-break: normal;overflow: hidden;white-space: nowrap;text-overflow: ellipsis; font-family: Interstate,Lucida Grande,Lucida Sans Unicode,Lucida Sans,Garuda,Verdana,Tahoma,sans-serif;font-weight: 100;"><a href="https://soundcloud.com/themaskedwolf" title="Masked Wolf" target="_blank" style="color: #cccccc; text-decoration: none;">Masked Wolf</a> · <a href="https://soundcloud.com/themaskedwolf/masked-wolf-astronaut-in-the-ocean" title="Astronaut In The Ocean" target="_blank" style="color: #cccccc; text-decoration: none;">Astronaut In The Ocean</a></div>

  <hr />

  <h3 id="codepen-embed">CodePen Embed</h3>

  <p
    data-height="265"
    data-theme-id="light"
    data-slug-hash="YWvpRo"
    data-default-tab="css,result"
    data-user="kharrop"
    data-embed-version="2"
    data-pen-title="Referral Form"
    class="codepen"
  ></p>
  <script
    async=""
    src="https://production-assets.codepen.io/assets/embed/ei.js"
  ></script>

  <hr />

  <h3 id="input-style">Input Style</h3>

  <p><input type="text" placeholder="I'm an input field!" /></p>

  <hr />

  <h3>Twitter Embed</h3>

  <blockquote class="twitter-tweet" data-lang="en">
    <p lang="en" dir="ltr">
      I just published “Deploying a blog using Jekyll and Github Pages with SSL
      certificate for Free”
      <a href="https://t.co/B3T3IQVU93">https://t.co/B3T3IQVU93</a>
    </p>
    &mdash; Sujay Kundu (@SujayKundu777)
    <a
      href="https://twitter.com/SujayKundu777/status/1012601950469160962?ref_src=twsrc%5Etfw"
      >June 29, 2018</a
    >
  </blockquote>
  <script
    async
    src="https://platform.twitter.com/widgets.js"
    charset="utf-8"
  ></script>

  <hr />

  <h3>Instagram Embed</h3>

  <blockquote class="instagram-media" data-instgrm-captioned data-instgrm-permalink="https://www.instagram.com/p/CKt5Ty_MtQ4/?utm_source=ig_embed&amp;utm_campaign=loading" data-instgrm-version="13" style=" background:#FFF; border:0; border-radius:3px; box-shadow:0 0 1px 0 rgba(0,0,0,0.5),0 1px 10px 0 rgba(0,0,0,0.15); margin: 1px; max-width:540px; min-width:326px; padding:0; width:99.375%; width:-webkit-calc(100% - 2px); width:calc(100% - 2px);"><div style="padding:16px;"> <a href="https://www.instagram.com/p/CKt5Ty_MtQ4/?utm_source=ig_embed&amp;utm_campaign=loading" style=" background:#FFFFFF; line-height:0; padding:0 0; text-align:center; text-decoration:none; width:100%;" target="_blank"> <div style=" display: flex; flex-direction: row; align-items: center;"> <div style="background-color: #F4F4F4; border-radius: 50%; flex-grow: 0; height: 40px; margin-right: 14px; width: 40px;"></div> <div style="display: flex; flex-direction: column; flex-grow: 1; justify-content: center;"> <div style=" background-color: #F4F4F4; border-radius: 4px; flex-grow: 0; height: 14px; margin-bottom: 6px; width: 100px;"></div> <div style=" background-color: #F4F4F4; border-radius: 4px; flex-grow: 0; height: 14px; width: 60px;"></div></div></div><div style="padding: 19% 0;"></div> <div style="display:block; height:50px; margin:0 auto 12px; width:50px;"><svg width="50px" height="50px" viewBox="0 0 60 60" version="1.1" xmlns="https://www.w3.org/2000/svg" xmlns:xlink="https://www.w3.org/1999/xlink"><g stroke="none" stroke-width="1" fill="none" fill-rule="evenodd"><g transform="translate(-511.000000, -20.000000)" fill="#000000"><g><path d="M556.869,30.41 C554.814,30.41 553.148,32.076 553.148,34.131 C553.148,36.186 554.814,37.852 556.869,37.852 C558.924,37.852 560.59,36.186 560.59,34.131 C560.59,32.076 558.924,30.41 556.869,30.41 M541,60.657 C535.114,60.657 530.342,55.887 530.342,50 C530.342,44.114 535.114,39.342 541,39.342 C546.887,39.342 551.658,44.114 551.658,50 C551.658,55.887 546.887,60.657 541,60.657 M541,33.886 C532.1,33.886 524.886,41.1 524.886,50 C524.886,58.899 532.1,66.113 541,66.113 C549.9,66.113 557.115,58.899 557.115,50 C557.115,41.1 549.9,33.886 541,33.886 M565.378,62.101 C565.244,65.022 564.756,66.606 564.346,67.663 C563.803,69.06 563.154,70.057 562.106,71.106 C561.058,72.155 560.06,72.803 558.662,73.347 C557.607,73.757 556.021,74.244 553.102,74.378 C549.944,74.521 548.997,74.552 541,74.552 C533.003,74.552 532.056,74.521 528.898,74.378 C525.979,74.244 524.393,73.757 523.338,73.347 C521.94,72.803 520.942,72.155 519.894,71.106 C518.846,70.057 518.197,69.06 517.654,67.663 C517.244,66.606 516.755,65.022 516.623,62.101 C516.479,58.943 516.448,57.996 516.448,50 C516.448,42.003 516.479,41.056 516.623,37.899 C516.755,34.978 517.244,33.391 517.654,32.338 C518.197,30.938 518.846,29.942 519.894,28.894 C520.942,27.846 521.94,27.196 523.338,26.654 C524.393,26.244 525.979,25.756 528.898,25.623 C532.057,25.479 533.004,25.448 541,25.448 C548.997,25.448 549.943,25.479 553.102,25.623 C556.021,25.756 557.607,26.244 558.662,26.654 C560.06,27.196 561.058,27.846 562.106,28.894 C563.154,29.942 563.803,30.938 564.346,32.338 C564.756,33.391 565.244,34.978 565.378,37.899 C565.522,41.056 565.552,42.003 565.552,50 C565.552,57.996 565.522,58.943 565.378,62.101 M570.82,37.631 C570.674,34.438 570.167,32.258 569.425,30.349 C568.659,28.377 567.633,26.702 565.965,25.035 C564.297,23.368 562.623,22.342 560.652,21.575 C558.743,20.834 556.562,20.326 553.369,20.18 C550.169,20.033 549.148,20 541,20 C532.853,20 531.831,20.033 528.631,20.18 C525.438,20.326 523.257,20.834 521.349,21.575 C519.376,22.342 517.703,23.368 516.035,25.035 C514.368,26.702 513.342,28.377 512.574,30.349 C511.834,32.258 511.326,34.438 511.181,37.631 C511.035,40.831 511,41.851 511,50 C511,58.147 511.035,59.17 511.181,62.369 C511.326,65.562 511.834,67.743 512.574,69.651 C513.342,71.625 514.368,73.296 516.035,74.965 C517.703,76.634 519.376,77.658 521.349,78.425 C523.257,79.167 525.438,79.673 528.631,79.82 C531.831,79.965 532.853,80.001 541,80.001 C549.148,80.001 550.169,79.965 553.369,79.82 C556.562,79.673 558.743,79.167 560.652,78.425 C562.623,77.658 564.297,76.634 565.965,74.965 C567.633,73.296 568.659,71.625 569.425,69.651 C570.167,67.743 570.674,65.562 570.82,62.369 C570.966,59.17 571,58.147 571,50 C571,41.851 570.966,40.831 570.82,37.631"></path></g></g></g></svg></div><div style="padding-top: 8px;"> <div style=" color:#3897f0; font-family:Arial,sans-serif; font-size:14px; font-style:normal; font-weight:550; line-height:18px;"> View this post on Instagram</div></div><div style="padding: 12.5% 0;"></div> <div style="display: flex; flex-direction: row; margin-bottom: 14px; align-items: center;"><div> <div style="background-color: #F4F4F4; border-radius: 50%; height: 12.5px; width: 12.5px; transform: translateX(0px) translateY(7px);"></div> <div style="background-color: #F4F4F4; height: 12.5px; transform: rotate(-45deg) translateX(3px) translateY(1px); width: 12.5px; flex-grow: 0; margin-right: 14px; margin-left: 2px;"></div> <div style="background-color: #F4F4F4; border-radius: 50%; height: 12.5px; width: 12.5px; transform: translateX(9px) translateY(-18px);"></div></div><div style="margin-left: 8px;"> <div style=" background-color: #F4F4F4; border-radius: 50%; flex-grow: 0; height: 20px; width: 20px;"></div> <div style=" width: 0; height: 0; border-top: 2px solid transparent; border-left: 6px solid #f4f4f4; border-bottom: 2px solid transparent; transform: translateX(16px) translateY(-4px) rotate(30deg)"></div></div><div style="margin-left: auto;"> <div style=" width: 0px; border-top: 8px solid #F4F4F4; border-right: 8px solid transparent; transform: translateY(16px);"></div> <div style=" background-color: #F4F4F4; flex-grow: 0; height: 12px; width: 16px; transform: translateY(-4px);"></div> <div style=" width: 0; height: 0; border-top: 8px solid #F4F4F4; border-left: 8px solid transparent; transform: translateY(-4px) translateX(8px);"></div></div></div> <div style="display: flex; flex-direction: column; flex-grow: 1; justify-content: center; margin-bottom: 24px;"> <div style=" background-color: #F4F4F4; border-radius: 4px; flex-grow: 0; height: 14px; margin-bottom: 6px; width: 224px;"></div> <div style=" background-color: #F4F4F4; border-radius: 4px; flex-grow: 0; height: 14px; width: 144px;"></div></div></a><p style=" color:#c9c8cd; font-family:Arial,sans-serif; font-size:14px; line-height:17px; margin-bottom:0; margin-top:8px; overflow:hidden; padding:8px 0 7px; text-align:center; text-overflow:ellipsis; white-space:nowrap;"><a href="https://www.instagram.com/p/CKt5Ty_MtQ4/?utm_source=ig_embed&amp;utm_campaign=loading" style=" color:#c9c8cd; font-family:Arial,sans-serif; font-size:14px; font-style:normal; font-weight:normal; line-height:17px; text-decoration:none;" target="_blank">A post shared by Instagram (@instagram)</a></p></div></blockquote> <script async src="//www.instagram.com/embed.js"></script>

  <br />

  <h3>Embedding PDF</h3>
  
  <h4>PDFObject</h4>

  <div id="pdf1"></div>

  <script src="/jv/pdfobject.js"></script>
  <script>
    PDFObject.embed("/sample/sample.pdf", "#pdf1");
  </script>

  <style>
    .pdfobject-container {
      height: 30rem;
      border: 1rem solid rgba(0, 0, 0, 0.1);
    }
  </style>

  <br />

  <h4>embed</h4>

  <embed
    src="/sample/sample.pdf"
    type="application/pdf"
    width="100%"
    height="500rem"
  />

  <br />

  <h4>iframe</h4>

  <iframe src="/sample/sample.pdf" width="100%" height="500rem">
    This browser does not support PDFs. Please download the PDF to view it:
    <a href="/sample/sample.pdf">Download PDF</a></iframe

  </br>
