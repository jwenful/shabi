一、实验目的 
1、分析学生选课系统 
2、使用GUI窗体及其组件设计窗体界面
3、完成学生选课过程业务逻辑编程 
4、基于文件保存并读取数据 
5、处理异常 
二、业务要求 
1、系统角色分析及类设计 学校有“人员”，分为“教师”和“学生”，教师教授“课程”，学生选择课程。 定义每种角色人员的属性，及其操作方法。 属性：人员（编号、姓名、性别） 教师（编号、姓名、性别、所授课程） 学生（编号、姓名、性别、所选课程） 课程（编号、课程名称、上课地点、时间、授课教师）
2、基本要求 设计GUI窗体，支持学生注册、课程新加、学生选课、学生退课、打印学生选课列表等操作。 基于事件模型对业务逻辑编程，实现在界面上支持上述操作。 针对操作过程中可能会出现的各种异常，做异常处理。 基于输入/输出编程，支持学生、课程、教师等数据的读写操作。
三、解题思路 
1、首先定义五个系统角色类，分别是人员People类、教师Teacher类、学生Students类、课程Subject类。 
2、根据要求说明，挖掘其中的逻辑关系；容易发现，通过打印学生信息，可以实现对课程与老师信息的输出，故可以 得到他们之间的包含关系：学生信息→课程信息→教师信息，考虑到一个学生只能选一门课，一门课只能由一个老师教 授，可知这条单链包含关系就可以使其相关联。
3、为测试类以外的四个类添加属性与方法，将People类设为Teacher类与Students类的父类，这两个子类可以通过继承 获取父类的id、name、sex等属性并且继承相应地方法。
4、覆盖Object根类中的toString方法，使其可以根据类名返回特定的字符串信息。
5、主页IndexTest类：首先创建JFrame窗体，设置窗体的像素、名称；然后创建JPanel容器，向该容器中添加3个JButton 组件，分别为：学生选课、学生退课和课程打印，点击相应的按钮进入相应的页面。 6、学生选课模块ChoiceSubject类，此类通过extends关键字继承JFrame类，目的是通过对该类的实例化可以实现窗口显 示，从而实现页面的跳转。创建JPanel面板容器，向该容器添加JList组件，目的是使信息列表化；添加JCheckBox组件可 以实现对待选课程的勾选；勾选完成后，点击“确定”按钮，程序会将所选课程的数据写入文本文件，实现数据的调用与 储存。
7、学生退课模块QuitSubjects类，同样也是继承JFrame类，创建JPanel面板容器，向该容器添加JList组件，通过点击每 一行课程信息进行退课的选择(可以通过常按Shift键实现多门课的选中），点击“退课”按钮，弹出“退课成功”对话框，点 击“确定”，执行setVisable(false)语句，关闭对话框。
8、打印课程模块PrintSubjects类，通过文件操作Readfile（）读取选课、退课后的数据，显示在窗体中。
9、添加课程AppendSUbjects类，设置6个JTextField组件用于输入课程信息，一个JComobox组件实现性别的选择，三个 按钮，点击“添加按钮”将课程信息拼接成字符串，利用文件操作将其写入文件中，点击“退出”按钮，销毁界面，点击“重 置”按钮消除输入信息实现重新输入。
10、登录注册LoginTest类，利用JRadioButton设置单选按钮从而实现分角色登 录。考虑到每个系统管理员是固定的几个，所以该系统没有设置管理员注册页面，仅仅保留了登录页面，而学生可以进 行注册与登录。管理员登录后，自动跳转到添加课程页面，而学生登录后跳转到选课页面，因为学生不具备添加课程的 权限。 
11、文件操作FileOperations类，为其类创建readFile()与writeFile()方法，从而实现数据的读写与信息在各程序之 间的传递。
四，思路图
见文件
![145](https://user-images.githubusercontent.com/114643475/195378120-6c0b2cec-a425-4b96-89d6-4ea8d79bba64.png)
