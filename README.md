# Kuro-AutoSignin

自动化每日任务，轻松管理库街区论坛与游戏签到

## 使用说明

1. **替换个人信息**：请通过抓库街区的包替换脚本中的 `token`、`devcode`、 `roleId`、 `userId` 和 `distinct_id`。
2. **获取 Token**：使用 `tools.py` 来获取你的 `token`（此方法用于不想折腾安卓抓包并且客户端不能再次登录，库街区的 token 如果新设备登陆了会刷新）；或者直接抓包。
3. **已对接 Server 酱**：在 `data.json` 中的 `serverKey` 字段中填入 Server 酱 Key，激活即时通知服务。
4. **云函数支持**：入口为 `index.handler`。

## 环境依赖

- NodeJS
  - 国内: <https://nodejs.cn/download/>
  - 官网: [Node.js — Download Node.js® (nodejs.org)](https://nodejs.org/en/download/package-manager)
- Python 环境
  - `pip install -r ./requirements.txt`

若使用 `pip install -r ./requirements.txt` 安装失败，则按以下顺序进行单独安装依赖

1. `pip install ddddocr`
2. `pip install numpy==1.26.2` 请勿使用 numpy2，会报错
3. `pip install PyExecJS`
4. `pip install loguru`
5. `pip install requests`

## 青龙面板运行方法

1. **拉取项目到本地**：将项目克隆到本地目录。
2. **获取个人信息**：捕获库街区的包，获取并填写好 `data.json` 中的 `token`、`devcode`、`roleId`、`userId` 和 `distinct_id`。
3. **创建订阅**：在青龙面板中创建新的订阅任务。
   - 名称：库街区签到
   - 类型：公开仓库
   - 链接：<https://github.com/mxyooR/Kuro-autosignin.git>
   - 定时类型：crontab
   - 定时规则：1 9 * * *
   - 白名单：main.py
   - 依赖文件：log|game_check_in|bbs_sgin_in

4. **导入 `data.json`**：在青龙面板的脚本管理中，进入 `mxyooR_Kuro-autiosignin` 文件目录下，导入并替换修改好的 `data.json` 文件。
5. **添加依赖**：在青龙面板的依赖管理里面安装requests依赖。

这样设置完成后，青龙面板将会每天按时自动运行库街区的签到任务。****
