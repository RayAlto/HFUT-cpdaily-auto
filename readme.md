# cpdaily-auto 今日校园每日疫情填报自动提交

合肥工业大学今日校园每日疫情填报新平台自动提交脚本，适用于新平台，经测试数学学院功能正常，其他学院有很小几率不能正常使用，可以fork后改改。

# 使用

这个脚本会先获取你的上一次填报，用于本次提交，所以第一次使用时需要先手动提交至少一次。

## 填写配置文件

编辑 `config.json` 填写用户信息：

* `username`: 合肥工业大学的学号
* `password`: 新的疫情填报平台的密码（初始为身份证后6位）
* `location`: 提交时使用的位置信息，替代手机的定位，最好别乱填，哗众取宠
* `serverChan`: server酱的SCKEY，填写这个可以在微信上查看填报情况，没有/不需要的话可以填 `null`

例如：

```json
"user": [
    {
        "username": "201888888888",
        "password": "888888",
        "location": "Toilet, Home, China",
        "serverChan": "xxxx"
    }
]
```

当然也支持多用户，但建议不要帮太多人代挂，因为如果学校发现你提交时的IP与提交的地址不符时有可能请你喝茶，例如：

```json
{
    "user": [
        {
            "username": "2018888888",
            "password": "888888",
            "location": "Toilet, Home, China",
            "serverChan": "xxxx"
        },
        {
            "username": "2017777777",
            "password": "777777",
            "location": "Bed, Home, China",
            "serverChan": null
        }
    ]
}
```

## 运行

把 `config.json` 放在与 `submit.py` 相同目录下运行 `submit.py` 即可，比如目录结构是这样：

```plaintext
/usr/local/bin/HFUT-cpdaily-auto
├── config.json
└── submit.py
```

在这个目录下执行：

```shell
python submit.py
```

## 设置定时任务

不需要任何参数所以很简单，比如用 crontab ，执行

```shell
crontab -e
```

指令，把这一行添加在任意一行：

```crontab
0 15 * * * /usr/bin/bash /usr/local/bin/HFUT-cpdaily-auto/submit.sh
```

`submit.sh` 的内容：

```shell
#!/usr/bin/bash
# 把工作目录移动到脚本所在的目录中
cd /usr/local/bin/HFUT-cpdaily-auto
# 直接运行
/usr/bin/python submit.py
```

每天的下午3点都会自动进行填报提交
