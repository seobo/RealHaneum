# RealHaneum

~~~
# -*- coding: utf-8 -*-
2   
3 #---------------------------------
4 # pangpang2.py
5 #---------------------------------
6   
7 import os
8 from flask import Flask, request, jsonify
9   
10 app = Flask(__name__)
11   
12 @app.route('/keyboard')
13 def Keyboard():
14     dataSend = {
15         "type" : "buttons",
16         "buttons" : ["대화하기!", "도움말"]
17     }
18     return jsonify(dataSend)
19   
20 @app.route('/message', methods=['POST'])
21 def Message():
22     dataReceive = request.get_json()
23     content = dataReceive['content']
24     if content == u"대화하기!":
25         dataSend = {
26             "message": {
27                 "text": "명령어 목록!\n1. 도움말\n2. 안녕!\n3. 저기요~"
28             }
29         }
30     elif content == u"도움말":
31         dataSend = {
32             "message": {
33                 "text": "이제 곧 정식 버전이 출시될거야. 조금만 기다려~~~"
34             }
35         }
36     elif u"안녕" in content:
37         dataSend = {
38             "message": {
39                 "text": "안녕~~ 반가워 ㅎㅎ"
40             }
41         }
42     elif u"저기" in content:
43         dataSend = {
44             "message": {
45                 "text": "볼일 끝났으면 썩 꺼져!"
46             }
47         }
48     else:
49         dataSend = {
50             "message": {
51                 "text": content
52             }
53         }
54     return jsonify(dataSend)
55   
56 if __name__ == "__main__":
57     app.run(host='0.0.0.0', port = 5000)
58
 
59

60 #출처: http://cupjoo.tistory.com/5 [오지는 컴퓨터 공부]
61 #####################################################
~~~
