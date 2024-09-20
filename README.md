# 🐱‍💻 PAM을 사용하여 비밀번호 정책 강화하기

### ❓ PAM (Pluggable Authentication Modules)
리눅스 시스템에서 사용하는 인증 모듈로써 사용자의 사용 권한을 제어한다.

---

### [1] libpam-pwquality 설치
```
sudo apt install libpam-pwquality
```

### [2] /etc/pam.d/common-password 수정
🎯 비밀번호 설정 시 8자리 이상으로 규제하는 것이 목표이다.
```
sudo vi /etc/pam.d/common-password
```
![image](https://github.com/user-attachments/assets/ea0125a1-2dd1-4871-bdf5-9d4eb1810fb1)

🛠 password requisite pam_pwquality.so retry=3 이후에 <b>minlen=8</b>을 추가한다.

![image](https://github.com/user-attachments/assets/bce177a1-a1c3-4c99-a23e-ff03b6a08131)

### [3] 확인해보기
🔑 사용자를 생성할 때 규제가 성공적으로 적용되었는지 확인할 수 있다.

![image](https://github.com/user-attachments/assets/3dd1540a-519c-4da8-8af3-a2331847d9be)

❌ 비밀번호를 8자리 이하로 입력하였더니 에러가 발생하였다.

![image (1)](https://github.com/user-attachments/assets/e619f125-d1d1-4d7f-8e90-6fc0a92ceb99)

⭕ 8자 이상 입력 시 유저 생성에 성공한다.
