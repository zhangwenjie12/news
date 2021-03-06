# 新闻发布系统
***
## 简介
运行在Tomcat 7.0的网站工程，前台用了jsp、js、css等技术，后台用了Servlet作控制器调用java类来进行业务处理，MySQL后台数据库。

亮点

1. JavaScript的页面表单输入合法性检查。
2. css样式表的复用。
3. 实用的数据库封装类：获取查询结果的条目数、二维字符串数组形式读取数据库查询结果等。
4. Servlet返回页面的使用JS代码，使得处理更灵活。

入口：logweb/login.jsp
## 功能说明
1. #### 注册
  1. 填写用户名、密码、确认密码（必填），选择性别、职业、爱好，填写个人说明（选填），提交注册：要求用户名为中文，密码为6~16位字母数字及下划线构成。
  2. 提交成功之后现实注册信息，并提供链接返回登陆页面。注册用户默认为一般用户类型。

2. #### 登录
  1. 输入用户名及密码登录到新闻发布系统：登录时会判断用户类型，一般用户进入一般用户主界面，管理员进入管理员主界面。
  2. 登录后显示主界面：顶部为当前登陆用户的用户名，左侧为菜单栏，右侧为内容页面（此时显示欢迎页）。

3. #### 发布新闻
  1. 点击菜单栏“发布新闻”字样，在内容页面显示新闻发布操作页面。
  2. 填写新闻标题（必填）及新闻正文（选填）之后，点击提交。后台系统记录下发布者、新闻标题、新闻正文、发布时间等内容并自动添加新闻编号记录到数据库中。
  3. 若数据库提交成功，便弹出提示窗口显示“发布成功”，并进入一个新的发布页面。

4. #### 查询新闻
  1. 查询页面
      1. 输入新闻标题或发布人查询新闻：默认不填写则查询当前用户发布新闻；填写标题则查询所有此标题的新闻；填写发布人则查询填写的用户发布的新闻；都填写则匹配此用户此标题的新闻。并在下方以列表形式呈现查询结果。
      2. 若无查询结果，则跳转到查询错误页，并提供返回查询页面的链接。
      3. 每条查询出的新闻以列表显示编号、标题、发布人、发布时间，并提供对此条新闻的查看详细、修改、删除等操作。

  2. 查看详细
      1. 点击操作栏的“查看”链接进入查看新闻详细页面。
	  2. 查看详细页面以输入框的形式显示标题、内容、发布人、发布时间等信息，并且不允许修改。
	  3. 提供“返回”按钮跳转到新的查询页面。

  3. 修改新闻
      1. 点击操作栏的“修改”链接进入修改新闻页面。
      2. 修改新闻页面显示新闻编号、标题、正文、发布人、发布时间等项；其中只有标题和正文可修改。
      3. 修改之后点击提交按钮，若成功则刷新当前页并更新新闻信息。
      4. 提供“重置”重置当前新闻信息到初始状态，“返回”按钮跳转到新的查询页面。

  4. 删除新闻
	  1. 点击操作栏的“删除”链接删除此条新闻。
	  2. 删除操作会先提交确认提示，点击确认之后再提交删除数据库里的信息，最后弹出提示是否删除成功。
	  3. 若删除成功，则跳转到新的查询页面。


5. #### 修改密码
  1. 点击左侧菜单栏“修改密码”链接在内容页显示修改密码页面。
  2. 要求输入原密码、新密码、再次输入新密码。
  3. 点击“提交”按钮判断合法性，若通过合法性判断，则提交到数据修改新密码。
  4. 若修改数据库成功，则弹出修改成功提示框，并在内容页面显示欢迎页。

6. #### 用户管理（仅限管理员）
  1. 管理员用户登录界面菜单栏有“用户管理”链接，点击在内容页面显示用户查询页面。
  2. 查询用户
      1. 输入要查询的用户名提交显示查询结果；无输入则默认查询所有用户。
	  2. 查询成功则在下方以列表形式显示查询结果：包括用户名、性别、职业、用户类型。
	  3. 查询失败则在输入框下方提示错误信息。
  3. 查看用户详细信息
      1. 点击操作栏“查看”链接，进入用户信息详细页面。
	  2. 详细信息显示用户的用户名、密码（不显示）、性别、职业、爱好、个人说明、用户类型等信息，并且默认为不可修改。
	  3. 提供“返回”按钮跳转到刚刚已查询的结果页。
  4. 修改用户信息
      1. 点击操作栏“修改”链接，进入用户信息修改页面。
	  2. 现实当前用户的信息，除用户名外都可修改。
	  3. 修改完毕之后点击提交，则提交到数据库更新当前用户的用户信息。
	  4. 若提交数据库修改成功，则跳转到成功提示页面，并提供链接跳转到新的用户查询页面。
	  5. 若提交数据库修改失败，则跳转到失败提示页面，并提供链接跳转到新的用户查询页面。
	  6. 提供“返回”按钮跳转到新的用户查询页面。
  5. 删除用户
      1. 点击操作栏“删除”链接，删除此用户。
	  2. 执行删除操作前，弹出确认按钮，点击确认则继续执行删除操作，否则删除操作中断。
	  3. 若删除成功，则弹出成功提示框并跳转到新的用户查询页面。
	  4. 若删除失败，则弹出失败提示框并跳转到新的用户查询页面。

7. #### 退出登录
  1. 点击菜单栏“退出登录”链接，注销当前已登录用户并跳转到登录页面。

## 更新日志
2016-05-13 撰写说明文档，上传已完成的新闻发布系统项目。
