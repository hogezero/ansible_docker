# ansible_docker
# 事前準備
下記の内容で`inventory.ini`を作成する。  
```
[debian11]
srv01 ansible_host=XXX.XXX.XXX.XXX

[debian11:vars]
ansible_user=ユーザ名
ansible_ssh_port=22
ansible_ssh_pass=ユーザパスワード
ansible_sudo_pass=ユーザパスワード                  ; become_methodをsudoを指定場合
ansible_ssh_private_key_file="./path/file_key"   ; 鍵認証場合
ansible_become_user=root                         ; become_methodをsuを指定場合
ansible_become_pass=ルートパスワード                ; become_methodをsuを指定場合
```

ディレクトリ構成は下記。  
```
.
├── inventory.ini
├── playbook.yml
└── roles
    └── docker
        ├── handlers
        │   └── main.yml
        └── tasks
            ├── install.yml
            └── main.ym
```
# 実行
```
ansible-playbook -i inventory.ini playbook.yml
```