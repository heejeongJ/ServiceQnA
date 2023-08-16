# NoticeBoard Web
#### Django 기반 파이썬 CRUD 게시판

## 개발 시 참고 & 주의 사항
### 플라스크 서버 실행하기
이제 가상 환경에서 flask run 명령을 실행해 플라스크 로컬 서버를 실행하자.
```c
(myproject) c:\projects\myproject>flask run

 * Environment: production
   WARNING: This is a development server. Do not use it in a production deployment.
   Use a production WSGI server instead.
 * Debug mode: off
Usage: flask run [OPTIONS]

Error: Could not locate a Flask application. You did not provide the "FLASK_APP" environment variable, and a "wsgi.py" or "app.py" module was not found in the current directory.

```
그런데 로컬 서버를 실행하면 "플라스크 애플리케이션을 찾을 수 없다"는 오류가 발생한다. 오류 메시지를 조금 더 자세히 보면 "FLASK_APP 환경 변수가 없다"라고 표시되어 있다. 즉, 플라스크 서버를 실행하려면 반드시 FLASK_APP 환경 변수에 플라스크 애플리케이션을 설정해야 한다.

#### [플라스크]
##### FLASK_APP 환경 변수의 기본값
플라스크는 FLASK_APP 환경 변수가 지정되지 않은 경우 자동으로 app.py 파일을 기본 애플리케이션으로 인식한다. 따라서 앞의 pybo.py 파일을 app.py로 만들었다면 FLASK_APP 환경 변수를 별도로 지정하지 않아도 된다. 하지만 우리는 FLASK_APP 환경 변수의 값을 수정하여 이 문제를 해결할 것이다.

### 플라스크 애플리케이션 설정하기
myproject 디렉터리에서 set FLASK_APP=pybo 명령을 실행하여 환경 변수 FLASK_APP에 pybo라는 값을 설정하자. 환경 변수에 설정한 pybo는 앞에서 작성한 pybo.py 파일을 의미한다.
```c
(myproject) c:\projects\myproject>set FLASK_APP=pybo
```
그리고 플라스크 서버를 다시 실행하자.
```c
(myproject) c:\projects\myproject>flask run
WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 ** Serving Flask app 'pybo'
 ** Debug mode: off
 ** Running on http://127.0.0.1:5000 (Press CTRL+C to quit)
```
이번에는 오류 없이 잘 수행된다. 그런데 여전히 뭔가 미심쩍은 경고 메시지가 보인다. 이 경고 메시지가 나타난 이유는 플라스크 서버가 개발 모드로 실행되었기 때문이다.

> 운영 환경에서는 flask run으로 실행하는 개발서버가 아닌 WSGI 서버로 실행해야 한다. WSGI 서버로 플라스크를 구동하는 방법은 뒤에서 자세하게 다룬다.

### 개발 서버를 디버깅 가능하도록 실행하기
우선 <Ctrl+C> 를 눌러 구동 중인 플라스크 서버를 중지하자. 그리고 set FLASK_DEBUG=true 명령을 실행해 디버깅이 가능하도록 설정하자.
```c
(myproject) c:\projects\myproject>set FLASK_DEBUG=true
```
그리고 다시 플라스크 개발 서버를 실행하자.
```c
(myproject) c:\projects\myproject>flask run
 WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 * Serving Flask app 'pybo'
 * Debug mode: on
 * Running on http://127.0.0.1:5000 (Press CTRL+C to quit)
 * Restarting with stat
 * Debugger is active!
 * Debugger PIN: 286-954-098
```
그러면 디버깅 모드가 활성화되어 플라스크 개발 서버가 실행된다. 서버를 실행하고 마지막 문구를 보면 플라스크 서버가 127.0.0.1:5000로 실행되었음을 알 수 있다. 
