# 文章自动生成器
## 1.前言
最近开始想写一些东西，脑子里也有不少想法，但是自己写又比较费时间，而且还要排版，精修，刚开始写的字数甚少，想法也是断断续续，不连贯，本想放弃，但是想到放弃就太可惜了，自己又是程序出身，最近AI写作不是很流行么，于是萌发了自己搞一个类似AI写作的工具，辅助自己写作。
## 2.实现方式
既然暂时没精力写一整个文章，那就把自己脑子里面的想法，写成句子，先从句子入手，慢慢训练写文章的能力，并且通过编程算法，将这些句子整理成文章，做成类似于AI写作的工具。
开发语言是python，用到的部分库如下：
`` import  random  
`` from  docx  import  Document  
`` from  docx.shared  import  Pt  
`` from  docx.enum.text  import  WD_PARAGRAPH_ALIGNMENT  
客户端程序连接我的云端，运行句子模型，生成文章，并将文章生成word文档，最终形成一篇文章，并自动生成标题,修改样式。
`` def  create_article(title, triplets):  
``     """  
``     创建文章并保存为Word文档  
``     """  
``     doc  =  Document()  
``       
``     # 设置标题样式为Heading 1  
``     heading  =  doc.add_heading(level=1)  
``     heading.text =  title  
``     heading.alignment =  WD_PARAGRAPH_ALIGNMENT.CENTER  
``     # heading.font.name = '宋体'  
``     # heading.font.size = Pt(16)  
``       
``     # 添加内容，并设置字体为宋体  
``     for  triplet  in  triplets:  
``         para  =  doc.add_paragraph(triplet)  
``         para.alignment =  WD_PARAGRAPH_ALIGNMENT.JUSTIFY  
``         for  run  in  para.runs:  
``             run.font.name =  'SimSun'  
``             run.font.size =  Pt(12)
`` 
``     # 保存文章到Word文档  
``     output_filename  =  f"output/{title}.docx"  
``     doc.save(output_filename)  
``     return  output_filename  _
## 3.运行效果展示
最后将python脚本和算法以及模型库打包，打包指令如下：
`` pyinstaller --onefile --icon=anni.ico  .\generate_article.py
pyinstaller --onefile --icon=anni.ico  .\generate_article.py
直接运行generate_article.exe_，客户端会连接模型，运行模型，最终生成文章。
## 5.后续
展示的模型为10000字训练的，测试运行效果还不错，第三篇就获得百度推荐2w+次。
后续会继续增加模型容量，完整源码和更大模型加V：sydygys。
![微信二维码](https://github.com/sydyg/generate_article/assets/24352068/08fb9ec1-cc66-4017-89df-582c8144a30c)

