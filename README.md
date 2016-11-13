# --全栈数据工程师养成攻略的代码实现
# -*- coding: utf-8 -*-

import sys 
reload(sys) 
sys.setdefaultencoding('utf-8')  
file=open('/Users/enniu/Desktop/xyj.txt')
result=[]
numbers={}
for line in file:
	line=line.strip()
	if len(line)==0:  		  
		continue
    line=line.decode('UTF-8') 
    #line=unicode(line)    
    for i in range(0,len(line)):
        if line[i] in ['.','.',':','!','-','，','。','！','：']:
            continue
        if not line[i] in result:
            result.append(line[i])
        if not numbers.has_key(line[i]):
            numbers[line[i]]=0
        numbers[line[i]]+=1
        ordernumbers=sorted(numbers.items(),key=lambda item:item[1],reverse=True)   
fw=open('/Users/enniu/Desktop/outcome.txt','w')
for x in ordernumbers:
    fw.write(x[0]+':'+str(x[1])+'\n')
fw.close()
file.close()
