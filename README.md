# gridea-theme-breek
https://i.immmmm.com/post/gridea-theme-breek/

# update
1. 更新项目结构为Gridea主题标准结构

2. GiTalk评论配置下添加阅读量统计
    **gitalk.ejs**:
    ```javascript
    <link rel="stylesheet" href="https://unpkg.com/gitalk/dist/gitalk.css">
    <script src="https://unpkg.com/gitalk/dist/gitalk.min.js"></script>
    <script type="text/javascript" src="https://cdn.staticfile.org/valine/1.3.10/Valine.Pure.min.js"></script>

    <div id="gitalk-container"></div>

    <script>

    var valine = new Valine();
    valine.init({
            appId: '<%= site.customConfig.valineID %>' ,
            appKey: '<%= site.customConfig.valineKey %>',
            visitor: <%= site.customConfig.visitors %> // 阅读量统计
    })

    var gitalk = new Gitalk({
        clientID: '<%= commentSetting.gitalkSetting.clientId %>',
        clientSecret: '<%= commentSetting.gitalkSetting.clientSecret %>',
        repo: '<%= commentSetting.gitalkSetting.repository %>',
        owner: '<%= commentSetting.gitalkSetting.owner %>',
        admin: ['<%= commentSetting.gitalkSetting.owner %>'],
        id: (location.pathname).substring(0, 49),      // Ensure uniqueness and length less than 50
        distractionFreeMode: false  // Facebook-like distraction free mode
    })

    gitalk.render('gitalk-container')

    </script>

    ```

3. 文章总数统计修正，减去`关于`的统计
    **footer.ejs**:
    ```javascript
    <p class="published border-effect">
        ©2019 共 <%= site.posts.length - 1 %> 篇文章
        <br/>
        Theme <a href="https://gridea.dev/" target="_blank">「<%= themeConfig.themeName %>」</a> Powered by <a href="https://gridea.dev/" target="_blank">「Gridea」</a>
    </p>
    ```

    **post-list-archives.ejs**:
    ```javascript
    <h2 class="year">共 <%= site.posts.length - 1 %> 篇文章</h2>
    ```

4. 修改头部logo
`\assets\media\images\logoo.png`

5. 豆瓣读书详情链接修正
    `\assets\media\js\Bmdb.min.js`
    ```javascript
    c={API_BASE_URL:"https://bm.weajs.com/api/",DB_BASE_URL:"https://book.douban.com/subject/",
    ```