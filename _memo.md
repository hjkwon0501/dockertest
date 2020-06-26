# Info
```
⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯
 Instructor : 남중구
 E-Mail     : nowage@gmail.com
 Blog       : http://j.finfra.com
 FaceBook   : https://www.facebook.com/NamJungGu
 Phone      : 010-9797-9872
⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯

* http://dropbox.com ← 계정 없으시면 회원 가입하세요.

  - Dropbox Client앱을 설치하시면 강의 내용이 실습PC로 동기화됩니다.
     다운로드 주소 : http://dropbox.com/install
  - Dropbox 계정(이메일)을 nowage@gmail.com으로 보내 주시면
     강사가 강의자료가 있는 폴더로 초대해 드려요.

* 강의 메모 : http://bit.ly/nowageM1 (강의 요약 및 스크립트)

* 질문 및 건의 사항 : http://sli.do 23905번으로 들어오세요.(익명 채팅)

```


# Docker Using
## 아주 기본 명령어
```
docker search 키워드
winpty docker run -it 이미지명
docker images
docker ps -a
```
## 기본 명령어 정리
```
docker rm 컨테이너명
docker start 컨테이너명
docker attach
<<ctl+p,q>> 나오기
docker stop 컨테이너명
docker rm -f 컨테이너명  # 켜있어도 rm
```
##  Run
```
docker run -it 이미지명
docker run -it --name 컨테이너명 이미지명
docker run -it --name n1 -p 8888:80 -v c:\\Users\\nowage\\html:/usr/share/nginx/html nginx
```
* 정리하면
```
docker run              \
 -it                    \
 --name n1              \
 -p 8888:80             \
 -v c:\\Users\\nowage\\html:/usr/share/nginx/html \
 nginx
```
## exec
```
docker exec -it 컨테이너명 bash
```
## save
```
docker commit -m '메세지' 컨테이너명 이미지명
docker save -o 파일명 이미지명
```

## Docker Login
* 비번을 유저의 토큰으로 사용하는 것에 주의
```
docker login --username 유저명
```

## commit & push
```
docker commit -m 'xxx' 컨테이너명 이미지명
docker login
docker push 이미지명
```
## 청소
* Container먼저 지우고 이미지 지운다.



# Docker build
* Docker build Example : https://github.com/Finfra/dockers.git


# Kubernetes
## Short-names 
| Short name    |Full name                  |
|---------------|---------------------------|
| po            |pods                       |
| rs            |replicasets                |
| svc           |services                   |
| ns            |namespaces                 |
| no            |nodes                      |
| ep            |endpoints                  |
| ds            |daemonsets                 |
| deploy        |deployments                |
| -             | -                         |
| rc            |replicationcontrollers     |
| hpa           |horizontal pod autoscalers |
| cs            |componentstatuses          |
| limits        |limitranges                |
| cm            |configmaps                 |
| csr           |certificatesigningrequests |
| ev            |events                     |
| ing           |ingresses                  |
| pdb           |poddisruptionbudgets       |
| psp           |podsecuritypolicies        |
| pv            |persistentvolumes          |
| pvc           |persistentvolumeclaims     |
| quota         |resourcequotas             |
| sa            |serviceaccounts            |

## 기본명령어
```
kubectl cluster-info
kubectl version
kubectl get nodes       

kubectl get services
kubectl get deployments
kubectl get pods

kubectl run <deploy명> --image=<이미지명> --port=80
kubectl get deployments
kubectl logs <pod명>
kubectl.exe exec -it <pod명> bash

kubectl get services
kubectl expose deployment/<deploy명> --type="NodePort" --port 80
kubectl describe services/<deploy명>

kubectl scale deployment <deploy명> --replicas=4

kubectl.exe label pod nginx-5578584966-clbsr xxx=333
kubectl get pods -l xxx=333

kubectl create -f d.yaml
kubectl.exe label pod nginx-5578584966-clbsr xxx=333
kubectl get pods -l xxx=333

kubectl delete services/nginx
kubectl autoscale rs nginx-5578584966 --max=20
kubectl.exe get hpa
kubectl describe hpa/nginx-5578584966

kubectl.exe get deploy nginx -o yaml > nginx.yaml
kubectl create -f nginx.yaml

```







# Basic Tech
## git
### Windows에서 필수 셋팅
* GitBash에서는 autocrlf로 되어 있어서 enter키가 외곡됨으로 필수 셋팅
```
git config --global core.autocrlf false
git config --global core.eol lf
```
### commit을 위한 필수 셋팅
```
git config --global user.email "nowage@gmail.com"
git config --global user.name "Nam JungGu"
```




## Ubuntu 설치
```
apt update -y
apt install -y vim
```
## Bash
```
x=1
y=2
echo $x$y   # 문자열 더하기
let z=$x+$y # 숫자 연산
echo $z
for i in $(seq 5); do
  echo $i
done
```
* Example 구구단 3단
```
for i in $(seq 1 9); do
  let su=3*$i
  echo 3 X $i = $su
done
```










# Workshop
## Day1
1. Ubuntu 이미지 기반으로 u1이라는 컨테이너를 만드시오.
2. u1 컨테이너에 nginx를 설치하시오.
3. u1 컨테이너를 유저명/nginx1 이미지로 만들고 docker hub에 push하시오.

## Day2
1. Docker Image Build 하시오. (단, Nginx를 설치해서, Ubuntu이미지에서)

3. Docker Build Script를 Github에 Push하시오.(최소한의 Usage를 README.md에 넣으시오. )
                                               ex) docker build -t nowage/nginx-test  .
2. Docker hub로 Push하시오. (최소한의 Description을 넣으시오.즉, 생성스크립트의 github 주소 )











.
