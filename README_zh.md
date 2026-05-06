<div对齐="中心">
</一个>
    <p><他们>🗂️开源文件托管解决方案，支持Docker和无服务器部署，支持电报、不一致、CloudFlare R2、S3、拥抱面、WebDAV等多种存储渠道，提供restful API和WebDAV支持</他们></p>
    <p>
<一个href="https://github.com/MarSeventh/CloudFlare-ImgBed/blob/main/README_zh.md">简体中文</一个>|<一个href="https://github.com/MarSeventh/CloudFlare-ImgBed/blob/main/README.md">英语</一个>|<一个href="https://cfbed.sanyue.de">官方网站</一个>
    </p>
<一个href="https://github.com/MarSeventh/CloudFlare-ImgBed/blob/main/README_zh.md">简体中文</一个>|<一个href="https://github.com/MarSeventh/CloudFlare-ImgBed/blob/main/README.md">英语</一个>|<一个href="https://cfbed.sanyue.de">官方网站</一个><p对齐="中心">
<p对齐="中心"><一个href="https://github.com/MarSeventh/CloudFlare-ImgBed/blob/main/LICENSE"><IMGsrc="https://img.shields.io/github/license/MarSeventh/CloudFlare-ImgBed"alt="License"/></个><一个href="https://github.com/MarSeventh/CloudFlare-ImgBed/network/members"><IMGsrc="https://img.shields.io/github/forks/MarSeventh/CloudFlare-ImgBed"alt="叉子"/></一个>
    </P>
<p对齐="中心"><p对齐="中心">
<一个href="https://trendshift.io/repositories/14324"目标="_空白"><一个href="https://trendshift.io/repositories/14324"目标="_空白">
<IMGsrc="https://trendshift.io/api/badge/repositories/14324"alt="GitHub趋势"高度="80"><IMGsrc="https://trendshift.io/api/badge/repositories/14324"alt="GitHub趋势"高度="80">
</一个>  </一个>
    </p>
</div>








---

> [！重要]
>
> **v2.0版本升级注意事项请查看公告！**



<详细资料>
    <总结>公告</总结>



## 置顶

1. 部署使用出现问题，请先仔细查阅文档、常见问题解答以及已有issues。

2. **注意**：本仓库为[电报图象](https://github.com/cf-pages/Telegraph-Image)项目的重制版，如果你觉得本项目不错，在支持本项目的同时，也请支持原项目。

##v2.7.1+CloudFlare页面构建输出目录变更

> 自 v2.7.1 版本起，前端构建产物已迁移至 `前端距` 目录。**CloudFlare页面用户**需要手动修改构建配置：
>
>1.前往CloudFlare Dashboard→您的Pages项目→`设置`→`构建`
>2. 编辑`构建配置`，将`构建输出目录`从`/` 修改为 `/frontend-dist`
> 3. 保存后重新部署
>
>Docker用户和工人用户无需操作。

##2026.3.4v2.6.2重构Docker镜像的说明

>本次版本对Docker镜像进行了重构，涉及基础镜像、目录结构和数据库等方面的变更，带来了并发、内存管理等方面的优化。为确保数据安全，请务必**先备份数据再进行升级**。
>
>###升级前：备份数据
>
> 1. 备份数据：在管理面板下载备份文件（若原来使用本地R2存储需要全部下载重传）
> 2. 备份data文件夹
>
>###升级步骤
>
> 1. 拉取最新镜像：
>
>    ```猛击
>    Docker合成张力
>    ```
>
> 2. 使用新镜像启动容器：
>
>    ```猛击
>    Docker复合up-d
>    ```
>
> 3. 检查容器是否正常运行：
>
>    ```猛击
>    docker合成日志-f
>    ```
>
>    确认日志中无报错信息后即可正常使用。
>
>4.恢复数据：在管理面板恢复全部数据（原来的R2文件需要重传）
>
>###升级异常：回退版本
>
> 如果升级后出现异常，可通过以下步骤回退：
>
> 1. 停止容器：
>
>    ```猛击
>    docker作曲向下
>    ```
>
> 2. 回退到旧版本镜像：
>
>    ```猛击
>    #amd64
>    Docker ramarals提/云耀嵌入@sha256:896dc1b79883
>    #臂
>    Dockerra马氏提/cloudflare-imgbed@sha256:b5442ccc198c
>    ```
>
>    同时修改 `docker-compose.yml` 中的 `图像` 字段为对应旧版本 tag，然后重新启动：
>
>    ```猛击
>    Docker复合up-d
>    ```
>
> **注意事项**：
> - 升级前请务必确认备份完整，必要时备份一份data文件夹
> - 如果你使用了自定义的 `docker-compose.yml` 配置（如自定义端口、环境变量等），升级时请注意保留
> - 遇到问题请先查阅文档和已有 issues，或提交新的 issue

## 2025.2.6  V2.0 版本升级注意事项

> v2.0 版已发布，相较于 v1.0 版本进行了大量改动和优化，但 beta 版本可能存在潜在不稳定性，若您追求稳定，可选择暂缓更新。
>
> 由于**构建命令发生了变化**，此次更新需要您**手动进行**，请按照以下步骤进行操作：
>
> - 同步fork的仓库至最新版（若已自动同步可忽略）
>
> -前往pages管理页面，进入`设置`->`构建`，编辑`构建配置`，在`构建命令`处填写`npm安装`
>
> - 新版本所有设置项已**迁移至 管理端->系统设置 界面**，原则上无需再通过环境变量的方式进行设置，通过系统设置界面进行的设置将**覆盖掉**环境变量中的设置，但为了保证 **电报渠道的图片** 能够与旧版本相兼容，**若您之前设置了 Telegram 渠道相关的环境变量，请将其保留！**
>
> - 确保上述设置完成无误后，前往 pages 管理页面，进入`部署`，对最后一次不成功的部署进行`重试操作`

##关于切换到电报渠道的通知


>由于电报图床被滥用，该项目上传渠道已切换至电报信道，请**更新至最新版（更新方式见第3.1章最后一节）**，按照文档中的部署要求**设置`TG_BOT_TOKEN`和`TG_CHAT_ID`**，否则将无法正常使用上传功能。
>
> 此外，目前**KV数据库为必须配置**，如果以前未配置请按照文档说明配置。
>
> 出现问题，请先查看第5节常见问题Q&A部分。

</详细资料>




#1.导言

免费文件托管解决方案，具有**上传**、**管理**、**读取**、**删除**等全链路功能，覆盖文件全生命周期，支持**鉴权**、**目录**、**图片审查**、**随机图**等各项特性（详见[功能文档](https://cfbed.sanyue.de/guide/features.html)）。

![CloudFlare](自述文件/海报.PNG)

# 2. [文件](https://cfbed.sanyue.de)

提供详细的部署文档、功能文档、开发计划、更新日志、常见问题解答等，帮助您快速上手。

[![更新日期](https://recent-update.cfbed.sanyue.de/cn)](https://cfbed.sanyue.de/guide/update-log.html)

#3.演示

**演示站点**：[CloudFlare ImgBed](https://cfbed.1314883.xyz/) 访问密码：`cfbed`

![image-20250313204101984](README/login.png)

![image-20250313204101984](README/upload.png)

<详细资料>
    <总结>其他页面效果展示</总结>

![image-20250313204138886](README/uploading.png)

![image-20250313204308225](README/dashboard.png)

![image-20250314152355339](自述文件/customer-config.png)

![状态页](README/status-page.png)

![公共画廊](自述文件/public-gallery.png)



</详细资料>

#4.提示

- **前端开源**：参见[MarSequenth/三岳-ImgHub](https://github.com/MarSeventh/Sanyue-ImgHub)项目。

- **桌面端开源**：参见[MarSequenth/卫星](https://github.com/MarSeventh/satellite)项目。

- **生态建设**：欢迎社区参与生态建设，欢迎提交 PR 或者 Issue，优质内容参见[官网生态建设页面](https://cfbed.sanyue.de/about/ecosystem.html)。

- **赞助**：项目维护不易，喜欢本项目的话，可以作者大大一点小小的鼓励哦，您的每一份支持都是我前进的动力\~ 


  <一个href="https://afdian.com/a/marseventh"><IMGsrc="https://img.shields.io/badge/AFDIAN-946CE6?style=for-the-badge&logo=afdian&logoColor=white" 高度="36" alt="Afdian"></一个>&nbsp;&nbsp;<一个href="readme/weixin-reward.png" 目标="_空白"><IMGsrc="https://img.shields.io/badge/WeChat_Pay-07c160?style=for-the-badge&logo=wechat&logoColor=white" 高度="36" alt="WeChat Pay"></一个>&nbsp;&nbsp;<一个href="readme/alipay-reward.png" 目标="_空白"><IMGsrc="https://img.shields.io/badge/Alipay-1677FF?style=for-the-badge&logo=alipay&logoColor=white" 高度="36" alt="WeChat Pay"></一个>

- **赞助商**：感谢以下赞助者对本项目的支持！

  [![赞助者](https://afdian-sponsors.sanyue.de/image?columns=12)](https://afdian.com/a/marseventh)
  
- **贡献者**：感谢以下贡献者对本项目的无私贡献！

  [![贡献者](https://contrib.rocks/image?repo=Marseventh/Cloudflare-ImgBed)](https://github.com/MarSeventh/CloudFlare-ImgBed/graphs/contributors)

#5.明星历史

**如果觉得项目不错希望您能给个免费的star✨✨✨，非常感谢！**

[![Star History Chart](https://api.star-history.com/svg?repos=MarSeventh/CloudFlare-ImgBed,MarSeventh/Sanyue-ImgHub&type=Date)](https://star-history.com/#MarSeventh/CloudFlare-ImgBed&MarSeventh/Sanyue-ImgHub&Date)

#6.特别赞助人

- **[CloudFlare](https://www.cloudflare.com) & [EdgeOne](https://edgeone.ai/?from=github)**：提供CDN加速和安全保护服务

<一个href="https://www.cloudflare.com"><IMGsrc="readme/cloudflare-logo.png"alt="Cloudflare Logo"高度="25"></个><一个href="https://edgeone.ai/?from=github"><IMGsrc="readme/edgeone-logo.png"alt="腾讯Logo"高度="25"></一个>

- **[速维云](https://www.svyun.com/recommend/AELZ0UeMz8K11Zg7pEXC)**：提供云计算服务资源支持

-**[Linux DO](https://linux.do/)**fc：真诚友善团结专业
