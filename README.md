# --全栈数据工程师养成攻略的代码实现
# -*- coding: utf-8 -*-
"""
Created on Sat Oct 22 23:36:45 2016

@author: enniu
"""
import sys 
reload(sys) 
sys.setdefaultencoding('utf-8') #默认ACII编码不支持中文，故用utf-8编码

#计算出现了多少汉字，每个汉字出现了多少次，出现的最频繁的汉字
file=open('/Users/enniu/Desktop/xyj.txt')
result=[]
numbers={}

for line in file:
    line=line.strip()
    if len(line)==0:  #去除左右空白符
        continue
    line=line.decode('UTF-8')  #字符串转为Unicode形式，否则又会出现乱码。与下面语句等价
    #line=unicode(line)    
    for i in range(0,len(line)):
        if line[i] in ['.','.',':','!','-','，','。','！','：']:
            continue
        if not line[i] in result:
            result.append(line[i])
        if not numbers.has_key(line[i]):
            numbers[line[i]]=0
        numbers[line[i]]+=1
ordernumbers=sorted(numbers.items(),key=lambda item:item[1],reverse=True)   #字典按照值来排序
fw=open('/Users/enniu/Desktop/outcome.txt','w')
for x in ordernumbers:
    fw.write(x[0]+':'+str(x[1])+'\n')
fw.close()

file.close()
