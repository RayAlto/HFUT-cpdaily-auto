# cpdaily-auto 今日校园每日疫情填报自动提交

> 脚本仅限学习参考使用，请勿用于非法用途。开发这个脚本也仅仅是用于学习，作者并不提供任何基于这个脚本的服务。

## 使用

这个脚本会先获取你的上一次填报，用于本次提交，所以第一次使用时需要先手动提交至少一次。

### 填写配置文件

编辑 `config.json` 填写用户信息：

- `username`: 合肥工业大学的学号
- `password`: 新的疫情填报平台的密码（初始为身份证后 6 位）
- `location`: 提交时使用的位置信息，替代手机的定位，最好别乱填，哗众取宠
- `region` : 省市区，比如 `安徽省//合肥市//蜀山区` ，用 `//` 隔开

例如：

```json
{
    "user": [
        {
            "username": "201888888888",
            "password": "888888",
            "location": "Toilet, Home, China",
            "region": "Beijing//Japan//moscow"
        }
    ]
}
```

多用户时配置文件可以这么写：

```json
{
    "user": [
        {
            "username": "2018888888",
            "password": "888888",
            "location": "Toilet, Home, China",
            "region": "Beijing//Japan//moscow"
        },
        {
            "username": "2017777777",
            "password": "777777",
            "location": "Bed, Home, China",
            "region": "Beijing//Japan//moscow"
        }
    ]
}
```

### 运行

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
