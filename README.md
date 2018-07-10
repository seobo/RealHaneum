# RealHaneum
~~~
- - -
＊ Real_Haneum
==============
<hr>
<h2> <pre>  project name : 경기대 수원캠 봇</pre></h2>

<p><pre>     경기대학교 app 에서 제공하는 정보를 잘 모르는 user 들에게 접근성이 좋은
    <br>    kakao talk 을 이용하여 chat bot 형식으로 서비스를 제공.<ins>api</ins>를 이용한다.
    <br>    예를 들어 스쿨버스 정보, 학식 정보, 사무실 전화번호 등등..</pre></p>
<br>
<p><pre>    <b><mark><ins>동작 예시</ins></mark></b> <br>    input(<q>오늘 학식 뭐야?</q>), output(<q><ins>오늘의 학식 url</ins></q>) </pre></p>

<p><abbr title="Application Programming Interface"> <strong>api 란?</strong></abbr>
  <pre>    <q>응용 프로그램에서 사용할 수 있도록, 운영 체제나 프로그래밍 언어가
    <br>     제공하는 기능을 제어할 수 있게 만든 인터페이스를 뜻한다.</q></pre></p>


<hr>
<p><pre>경기대학교 주소 <br><address> 경기도 수원시 영통구 광교산로 154-42 </address></pre></p>

</body>
</html>
~~~
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
