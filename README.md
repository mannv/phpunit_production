# Client
Yêu cầu phải cài đặt những thứ sau ở client
```
install: git, ruby >= 2.0
```

trong quá trình cài ruby có thể ko có bản >= 2.x
thì chạy các lệnh sau

```
sudo apt-add-repository ppa:brightbox/ruby-ng
sudo apt-get update
sudo apt-get install ruby2.3
```

nếu chạy lệnh **sudo apt-add-repository ppa:brightbox/ruby-ng** mà bị lỗi thì chạy lệnh này để fix
```
sudo apt-get install software-properties-common python-software-properties
```

### Cài đặt capistrano
sau khi cài xong ruby thì mới cài được capistrano
```
gem install capistrano
```

Để tích hợp capistrano vào project bất kỳ chạy lệnh sau
*cd tới thư mục gốc của project, chạy lệnh*

```
cap install
```

hệ thống tự động sinh ra những file sau

```
├── Capfile
├── config
│   ├── deploy
│   │   ├── production.rb
│   │   └── staging.rb
│   └── deploy.rb
└── lib
    └── capistrano
            └── tasks
```

# Server

Server cần phải cài đặt git
```
sudo apt-get install -y git
```

để clone được code từ github phải tạo Deploy keys project trên github
https://github.com/mannv/base-api/settings/keys
tham khảo cách tạo SSH KEY
https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/


ssh-keygen -t rsa -b 4096 -C "man.nv@kayac.vn"


VD SSH Key:
```
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQC85kNz0VeNep9QHXftau/5nlTsDm5PfZS4lHkh6RMENu8kweFGBwhpfb215WbJYuugJUc1yOmaSO7GGRiX2He7CfzicoGNcapmYLQCXQbBLzHBL2YWeJX84WAhMqIEaJSE5j4AMThE7HwrK/GaBj68vksyJD6I5E5Q8/TQ6xbKLFISSgOHgWeoOL7wfMUn96RM74ybRIAGvex4slkBKLKBy6bFVdTEDT1CHN8Oih3Q2mQr94mWKG9Pj1/XCr4VoFoxW50P2DeZTj3HieJOEmWPijFXMF90FqoqVuROcopQrqbPoCo0IEUKYtBsGzNyH+Samzg/HlnKepGEHEf0nXI2qMAc2KpqIDm1CFskLlwp7rI1LcSKywv+MVRrhPy4W16DxE0PAqU1iV2gCzC5vOPbzhLzMAHC6/VZTIG/IOtKHAtVkN3hgwodNC8SVuhMvtA/oi3UgyyWPxm/JVH2ygXpjA1kVV0Yv8ZAoJqD75G5RDvzBmYO4x+UFR+KHcQ9qj6yyrw7YthFi6lhZZ+tXt2V7kaNkx0Znh0peM1JUw+dtchfONNpA/lixULLL8ZNhcIc3IRr86YPS97BgE/LwC2BopaZlxPWXuDOatetN+4Lo/yTnXcqaXYhp5HnAk2bowyLI5tZ591K5Iut5e1Jjq2zcFfQLi2zaeOVxh+wDv/W/w== man.nv@kayac.vn
```


# Deploy command line

```
cap <tên file trong thư mục ./config/deploy> deploy
```
VD:
```
cap production deploy
```
trong thư mục **./config/deploy** phải có file cấu hình với tên **production.rb**