# SimilarityQuestion

1.代码功能：主要实现的是基于文本匹配，采用余弦定理算法进行排序，对问题数据库进行检索，由高到低输出检索排序结果。
           便于在后期检索知识库找不到结果时，能够通过全文本检索，找出最相似的答案。
           
2.代码结构：
+---src
----com.study---------->包
-------CosineSimilarAlgorithm.java-------->实现余弦相似度算法的功能类
---------->getSimilarity(String doc1, String doc2)：实现文本相似度算法（余弦定理），输出相似度值（double型），只将汉字作为向量，其他的如标点，数字等符号不处理
---------->isHanZi(char ch)：判断是否汉字
---------->getGB2312Id(char ch)：根据输入的Unicode字符，获取它的GB2312编码或者ascii编码，返回ch在GB2312中的位置，-1表示该字符不认识
-------ReadXML.java-------------------------->实现全文匹配检索的主类
---------->readXml(String str)：使用dom4j解析XML，比较输入字符串和得到的各段的相似度，排序输出str为输入的要比较的字符串，返回比较后的map，存放比较的double结果的key和对应的问题段落的值。
---------->getAllFile(File f)：获取所有文件夹下所有xml文件
---------->main(String[] args)：程序入口，读取用户提问，输出结果到result.txt中
-------String1.java----------->实现去除冗余字符的功能类
---------->strOptimize(String str)：将原文本去除冗余字符后，输出新的文本

+---lib
-------xml----------------->存放可供检索的所有xml文件
-----------xxx.xml------->电信问答xml文件
-----------...(.xml)----->电信xml文件

3.输入：控制台输入问句（String类型）用户提问

4.输出：list存储，String类型，输出最佳匹配答案

5.涉及的jar包：dom4j-1.6.1.jar  ：	用于dom4j解析xml文件。
              jaxen-1.1-beta-7.jar ：	dom4j的基础包，用于在采用dom4j解析xml时，使用XPath的方法快速获取某个节点的数据。
