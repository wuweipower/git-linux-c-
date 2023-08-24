# 实习收获：
整个实习是围绕C++基础技术栈展开的。实习内容的项目主要是学习，实际操作，测试。
实习内容包括了
1. git命令的学习，以及在真正企业背景下的实际操作练习，然后进行学习成果测评
2. linux操作系统以及相关命令的学习，并且在无图形化的虚拟机上进行实际操作，然后进行学习成果的测评
3. C++基础知识的学习，针对C++11的主要特性进行了学习，并进行了实际操练，然后进行C++知识的线上测评。
4. 项目课题的设计与实现。会要求编写设计文档，会有公司CTO进行点评以及建议。在完成课题的过程中，会有导师指导。
5. 每隔一段时间会有专题讲座，由企业里面的工程师进行专题讲解。

## 具体收获
1. git rebase的使用场景的熟悉
2. 学习了cmake的基础语法，能构方便建立多文件的C++项目的编译和测试执行。
3. 学会了markdown文件里面插入plantuml代码，该代码可以自动生成uml图。好处是如果uml图需要经常修改，只需要修改代码即可，而不是要去重新调整绘图，截图粘贴。而且plantuml的绘图比较美观，不需要自己手动调整图中每个元素的具体位置，提高了开发效率。
4. 学会了智能指针的使用，摆脱了管理裸指针的痛苦。
5. 通过阅读相关的源码，深入理解了move函数和移动语义。提升了我课题代码的性能。
6. 熟悉了googletest的源码编译与使用，并且通过googletest完成了多个单元测试，在课题的实践中，不断的回归测试，帮助了我发现潜在的bug。
7. 导师帮忙做代码优化和规范主要有
   - 代码中的空格
   - 类似STL中的容器一样，返回成员的值应该返回常量引用
   - 头文件不要把using指令放在全局作用域，会污染头文件
   - C++11可以在声明成员变量的时候就赋值
   - 对于类成员指针，使用shared_ptr
   - 对于声明智能指针，名字过长使用别名typedef或者using
   - 对于函数参数，如果其中的参数不需要改变，就要用const引用
   - 一般不要自己抛异常，外层没有catch的话程序就崩溃了
   - 尽管自己知道是否会越界，但是代码中仍然要判断是否越界
   - 头文件中不要定义全局变量，多个cpp包含后，在链接阶段会报重复定义的错误，解决方式是使用extern声明，一个cpp定义它。
   - 对于具有全局性的变量，应该考虑线程安全，可以使用锁机制，也可以用thread_local关键字给每个线程一个备份
   - nullptr不能赋值给string类
   - 对于多个case的返回结果是一致的情况可以连着写case，中间不break
   - 不应该出现多个shared_ptr指向同一个裸指针，因为会造成多次delete，如果要指向this，应该继承std::enable_shared_from_this，然后使用shared_from_this()函数。
   - const变量不能move，阅读move函数源码可以知道，const的属性将会被保留，而拷贝构造函数无法匹配这个变量，所以，编译器是讲这个变量匹配给普通构造函数，无法实现移动语义。
   - 对于字符串，还是使用string类，不要用char*，方便使用

8. 学会在无图形化界面下，使用ssh连接虚拟机，在虚拟机上挂载外部设备和安装数据库
9. 学会了使用C++的宏帮助写日志和debug，如__LINE__显示代码所在的函数，__FILE__显示代码所在的文件，以及使用#if和#endif进行条件编译。
10. 为了避免复杂的判断路径的问题，我使用了标准库的realpath函数，实现了绝对路径的字符串的生成，方便在控制台打印的时候，定位对应的文件。
11. 对于编码中可以会出错的地方，使用assert和static_assert帮助检查代码中可能出现的问题。
12. 对于const变量，有的时候想要在特定的情况下改变他的值，或者赋值给一个非常量的变量，可以使用const_cast。
13. 深刻理解了赋值和拷贝。赋值不是拷贝，赋值是更新内存中的值，是已经存在了两个对象之间赋值，而拷贝是构造一份新的，开辟了新的空间，使用一个对象去操作另外一个快要生成的对象。
14. 对于树形结构的内存构建，需要使用递归函数，从一个根节点开始，针对不同的情况，递归他的兄弟节点或者子结点。

## 培训内容
1. C++后端开发基础分享。讲解了C++11的主要特性：智能指针，lambda表达式，auto，decltype，移动语义等等，讲解了工程化的C++开发：在docker容器中使用不同的环境进行编译打包，代码目录结构以及代码编写的规范，git多人协作规范。讲解了企业研发流程，包括了产品的研发和测试。
2. 迪备中json使用与实践，讲解了Json-spirit库对json对象的序列化和反序列化，并给出实践内容。
3. 存储、备份和鼎甲。本次培训内容主要是针对行业，讲解行业内部的情况，让我们具体了解这个行业的发展。其中深入浅出地讲解了很多现有的技术的原理。针对行业上的一些企业做了很多具体的分析，而针对自身，也讲解了很多企业级的技术和问题解决方案，收获颇丰。
# 心得体会：
1. 第一次的git的实际操作测试理解错意思，导致我最终的提交是错误的，主要原因是对企业实际操作的陌生，不知道一些命令的使用场景。其中git rebase的命令的使用场景对我来说就比较陌生，尽管我知道命令的功能。
2. git笔试和linux笔试考试范围很广，很多题目答不对，导致分数特别低，比较打击自信心。
3. 领导非常负责，对实习生特别上心，会亲自批改试卷，亲自检查，和员工交流很谦卑，在实习生设计文档的展示中，也提出了很多中肯的意见，对于学校培养的漏洞，给我们提出了很多非常好的意见。
4. 考试成绩大部分是匿名，保护了每个人的自尊心。
5. 考试后，会单独发报告或者试卷，报告里面会有题目分析。拿到试卷后，我们可以自行修改，或者直接去询问导师或者领导，这点非常好，因为会有人耐心回复。
6. 公司每个周周五只需要上七个小时班，剩下的两个小时，可以参加公司组织的运动会，公司内部员工也非常积极地参加。氛围浓厚。在运动过程中，还可以和领导面对面交流学校学习方面的内容，领导也会给出中肯的意见，以及一些比较重要的信息。
7. 每天都需要登记工时和报告，非常方便记录我每天的学习成果。
8. 在设计文档，软件工程的实际操作方面，学校里面并没有仔细具体实践过，尽管可能实践，但是大概率会特别老旧，不太符合实际企业实践。针对我们这种学习上的漏洞，公司提供了很多参考资料给我们学习，特别注重实习生的培养。
9. 公司每隔一段时间就会有技术分享，对我们开拓眼界非常有帮助。
10. 公司中很多前辈都非常热心的提供帮助，我有一次代码一直出现内存异常，公司里面有个工程师热心帮助我debug。最后在其帮助下解决了问题。
11. 企业中OA审批速度极快，对于工作中关于后勤的问题能在几分钟内就可以得到解决。
12. 企业中内耗很少，每个周只需要上5天班，每天只需要工作9个小时，研发部门可以弹性上班，可以在很晚的时间才来上班。这里的员工基本都是准点下班，除了特殊紧急的任务情况外，基本无加班情况，员工幸福度很高。不过，高管级别的人一般会工作比较多，对公司发展特别上心。
13. 公司里面会有零食，在工作饿了的时候可以自取补充能量，非常贴心。


# 意见和建议
1. 在git的笔试中，有的内容与给的参考资料匹配度低。比如其中的git flow的使用，考试内容与公司wiki上的不太符合，support分支的具体含义，公司wiki上也没有具体讲，但是考试内容考到了。除此之外，由于考试内容涉及面很广，我需要阅读并学习整本书才能很好做好git笔试，但是我后面才发现，考试内容其实在参考书籍的附录，本人建议，可以适当提醒重点的位置，不然考生的阅读范围过广很多学习到的根本在笔试中派不上用场，或者提供考试方向，避免漫无目的的学习，当然，这个建议是针对考试，对个人学习收益较小，学习仍然需要面面俱到，并且深入了解知识点。
2. linux笔试中，由于给了很多参考书籍，考试范围比较广，尽管在考完试后，在书籍上寻找答案也较困难。知识点比较分散。建议为考试形成一个系统的题库，尽管有题库但是实际操作上并不全面。