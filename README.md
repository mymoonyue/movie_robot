# Docker官方镜像
https://registry.hub.docker.com/r/yipengfei/movie-robot/

# 前端源代码
https://github.com/pofey/movie-robot-frontend

# 声明
影音是自己的终身需求，为了保持持续更新的热情，所以选择封闭激活使用制度。上班就很忙，晚上回家研发新功能，完善核心功能也是很花时间的（经常要2-3点才睡）。所以想使用，你必须为我付出的业余时间买单，通过捐助获得激活码。

发上一枚可以体验到4月30日的激活码，可以随意传播，邀请自己的朋友来玩，430结束，捐助获得激活码的价格将会提高，是否停止开放永久版也在考虑中。
seGRdbqgVolN0JveBe5p58fnXNGcw9TbtyFoWoLKqOtkU8JrCZGaa3Bj8OWhD8AVXaqTYYja4RO6f2o32To4cDJhz7n6JV7PakwONqg5fZfTw3YkDMICj85FncwEUjuH

激活码获取方式：
* 通过捐助作者，可以获得激活码，现在永久买断使用权128元，打赏码在下面，也可以直接访问：https://yee-1254270141.cos.ap-beijing.myqcloud.com/movie_robot/pay.jpg
* 机器人现已开放API系统，如果你可以在此基础上构建其他场景应用，凡被采纳，均可获得激活码。

官方telgram免费大群：[加入智能影音机器人交流群](https://t.me/+shOuvzcee9I4ZDll)

# 功能
WebUI功能预览

<img src="https://raw.githubusercontent.com/pofey/movie_robot/main/doc/images/webui-search.jpg" width="300" height="650"/><img src="https://raw.githubusercontent.com/pofey/movie_robot/main/doc/images/webui-downloading-dark.jpg" width="300" height="650"/><img src="https://raw.githubusercontent.com/pofey/movie_robot/main/doc/images/search-ww.jpg" width="300" height="650"/><img src="https://raw.githubusercontent.com/pofey/movie_robot/main/doc/images/webui-downloading.jpg" width="300" height="650"/>

定时自动从豆瓣电影的想看、在看、看过中获取影音信息，然后去PT站（支持多家站点）自动检索种子，找到最佳资源后按豆瓣电影分类提交到BT下载工具下载。在下载前，会自动检查你的Emby中是否已经存在。
基于此功能机制，还顺带具备了下列功能：
- 将一部刚上映，或者还没上映的电影加入想看，当PT站更新时会第一时间帮你下好，被Emby扫描到后直接观看。
- 对剧集类型的影视资源，如果你正在看一部没更新完的剧，只要pt站更新，也会帮你对比本地影音库缺少的剧集开始自动下载。
- 支持多PT站汇总搜索打分选种

针对新增下载和存量硬盘的影视库，机器人还可以帮你对乱七八糟下载种子名做标准化整理，整理后会按电影名+年份+tmdbid的方式存储，可以使用硬链接或复制模式的整理方式。
# 当前支持的站点
## 馒头、彩虹岛、天空、TTG、SSD、朋友、北洋园、柠檬、我堡、猫站、葡萄等几乎所有主流站点

# 更新日志
## 如何保持机器人是最新版本
Docker应用升级指南：https://feather-purple-bdd.notion.site/docker-09e1db16b2b14040840bd2f5660e666c

2022.04.13
beta标签上线新版本：Beta 2.1.9A，此版本升级后，不可降级回latest，请备份好配置文件
1. 新增多用户体系，可以为不同用户设定不同角色，控制登录后可访问的功能；
2. 新增几个站点适配，感谢@茶茶 提供的适配支持！
3. 新增实验玩法：一个适配overseerr订阅请求的接口，可以使用overseerr选片后交给机器人去选择下载硬链，强化中文支持，你用哪个用户token给到这个接口，就会使用哪个用户的选种策略配置；
4. 优化右上角智能下载按钮，二合一，顺序执行，统一为执行智能下载；
5. 优化智能下载逻辑，微信订阅后，立即启动智能下载，无需等定时1小时；同时，暂时关闭智能下载页面cron表示设置，统一为每小时1次，测试新的豆瓣抗反爬机制；
6. 优化通知能力，来自不同用于的豆瓣、微信订阅，在用户配置页面绑定配置后，均为定向推送，谁想看推给谁；同时增加通知到多通道的能力；
7. 优化豆瓣对监听用户设定的选种策略，统一迁移到用户设置；
8. 优化剧集智能下载逻辑一部剧集如果因pt种子名包含全集字样，下载后将停止订阅，不在继续执行；
9. 优化下载记录显示内容，增加来自用户，点击种子名可以跳转到对应种子详情页；
10. 优化Web页面资源存储结构，页面有关的菜单、角色权限、icon，全部迁移到容器的/app/frontend 目录，高手可以自己映射改造；

2022.04.09
Beta标签最新版本号1.9
1. 建立自有订阅机制，先在微信搜索中开放订阅能力，下周出WEB页面；
2. 优化豆瓣的使用形式，避免被豆瓣识别为爬虫；
3. 优化下载记录页面展示的元素内容，主列表页弱化种子信息，同时增加详情查看按钮显示更丰富的下载相关信息；
4. 优化下载记录删除功能，可以自定义选择是否加入黑名单、是否删除关联订阅、是否删除种子及文件；
5. 优化未识别到的重新识别页面，显示影视类型、及硬链接后的路径，提交时冻结按钮，优化显示样式；
6. 修复几十个智能下载和识别有关的BUG，不一一列举。
7. 感谢@ruicky @miniers 提供的前端技术支持和代码贡献！

2022.04.05
1. 新增养站功能，自动进行流量管理，不管你有多少PT站，全部交给机器人打理，自动帮你下载最热门的free种子挂上传；忘了PT站，好好看电影吧。详细功能介绍：https://feather-purple-bdd.notion.site/854f2ab70f394358b00b0ff9e2c1690a

2022.04.02
最新版在Beta标签，版本号：RC 20.6，修复几个重大BUG
1. 修复因PT站副标题描述不规范，不含季或不含集时，可能造成剧集信息分析错误，进而导致重复下载资源的BUG；
2. 修复月光骑士这种，tmdb只有英文名，没有中文名，导致种子全部被过滤掉的BUG；
3. 修复北洋园副标题为空时，显示为校64的适配BUG；
4. 优化因部分站点资源种没有年份信息时的匹配算法，修复部分剧集因没年份下不到的BUG；（这个优化并不会降低准确率，只有在种子中英文名都符合规范，并且季度信息符合所下载要求，才会放过这种空年份的种子）


2022.03.30晚
发布一个小版本Beta标签，RC 12
1. 新增丐帮、阿童木站点支持；
2. 修复豆瓣设置拉取多少天设置失效的BUG；
3. 修复重新识别部分情况下无效，并且通知为None的BUG；
4. 修复一处剧集解析的大坑，极端情况下可能会使内存和CPU使用率极具上升；
5. 尝试修复企业微信通知部分设备乱码的BUG；
6. 调整纯黑色主题的颜色细节，修复部分透明的BUG，感谢@jsl9208！
7. 中屏以下，下载记录不再触发动画，感谢@miniers！
8. 修复新增站点但不重启，可能导致下载报错的BUG；


2022.03.30
Beta标签RC 10版本完成发布
1. 重新适配全部PT站点，当前共支持17个，新版适配全部由我开发测试，数据质量可靠，增加了更多维度信息，更准确的分类信息；本次更新新增烧包、备胎站点支持，删除ptt；
2. 搜索结果显示种子免费及折扣、2倍上传标签，搜索后种子链接可点击跳转到PT站；
3. 重写智能下载的搜索逻辑，更多样的资源匹配机制，比以前智能化程度提升至少5倍；
4. 重写剧集下载及追更逻辑，将不再重复下载全季完结包；
5. 重写电影和剧集识别逻辑，利用重构后的PT站分类搜索能力，智能下载的准确率比之前提升至少5倍；
6. 重写智能下载资源搜索后过滤逻辑，同时增加一些被过滤的详细说明日志，观察重写后的效果；
7. 修复部分情况下，手动下载的电视剧，无法被监控识别的BUG（上一版为了解辅种问题引入）；
8. 底层http访问机制升级，提升网络请求稳定性与效率；
9. 优化下载记录页面样式，增加影视类型显示，名称和年份样式调整等，感谢@ruicky 大佬的改进与对前端部分源码作出的贡献！
10. 增加纯黑色页面主题，感谢@jsl9208 大佬贡献的前端代码！
11. 修复了很多bug；

关于智能下载的逻辑，简述部分变化：

1. 以前的剧集下载，会出全集下全集，多个资源包有完全重复的分集，不会做过滤，重构后逻辑变为当你本地缺少这部剧一半以上时，才会优先下完结全集包，否则会单集优先，同时增加交集过滤。
2. 以前的豆瓣想看下载，只会按豆瓣上标的中文名去pt站搜索资源，有些命名不规范的就搜不到。重构的逻辑变为，先将豆瓣数据识别为tmdb信息，然后用中英双语或多中文名+英文去pt站搜索资源，然后对资源合并去重后进行处理，增强了资源匹配的覆盖度。
3. 以前的pt搜索，会搜全量种子类型，一些游戏、音频、电子书资源，也会乱入，影响订阅追新的准确度。重构后，首先会精准的基于pt站分类去做搜索，再采用算法，做电影或剧集识别，交由过滤器处理，提高了准确率。
4. 重构了过滤器机制，当前有六层过滤器，负责对pt搜索后结果，做精准筛选，这六种过滤器，会针对不同资源类别，不同数据情况，动态选择，以保证下到绝对准确的种子。这六层过滤，基本和人类去选择一个资源的过程相似。
5. 还优化了数不清的细节，不做赘述。


2022.03.23

Docker镜像的Beta标签，已经升级至最新准正式版RC1 此版本为跨越式重大升级，正式告别手动编写配置文件，全部优化为WEB页面配置流程。
如果你是老用户：你所使用的任意一个版本都可以直升Beta，配置目录用现有的，但初次启动需要打开Web做个简单的初始化流程。当然你也可以继续停留在latest养老！
如果你是新用户：或之前配置和db不重要（删了或换新配置路径），那么请直接拉Beta体验吧！
相比3月4号的版本，此版本更新内容如下：
1. 所有网站访问、媒体服务器、下载工具、存储路径、影音识别、推送通知设置，豆瓣想看智能下载设置，全部可以在Web页面配置，告别配置文件；
2. 新增多站点聚合搜索及直接下载能力，当前已支持站点：馒头、彩虹岛、天空、TTG、SSD、朋友、北洋园、柠檬、我堡、猫站、葡萄、hdchina、hdfans、pthome、btschool、pttime，几乎所有主流大站；
3. 新增近期下载管理页面，此页面可以一览下载记录、下载进度（实时读取下载器）、对未识别或识别错的资源重新分析等一系列管理能力；
4. 新增立即触发豆瓣任务、微信搜索等若干小功能；
5. 以上所有WEB功能均适配了手机版，Android、iPhone均可直接加为桌面App，PC端也开放了搜索参数，可以整合浏览器工具；
6. 修复数不清的BUG，优化数不清的底层算法逻辑；


2022.03.04(Beta220304v1)
1. 新增Web API系统，支持并行聚合多站搜索，按关键字或豆瓣id
2. 利用API能力，新增微信搜索功能，可以在企业微信的应用设置消息接收，直接发送关键字搜索，搜索后经过机器人多策略排序后，点击直接下载
3. 修复jackett的一些BUG
4. 修复qbit下载器删除种子后报错的BUG
5. 优化pthome用户名匹配
6. 修复pt站种子剧集分析的BUG
7. 修复SSD获取下载数错误的BUG 

2022.02.28
1. 新增Beta版tag
2. 增加pttime、ourbits以及jackett支持
3. 优化TR部分情况下查找种子报错
4. 电视剧支持首发过滤

2022.02.27
1. 馒头恢复正常，去掉浏览器内核，发布0.1正式版
2. 修复btschool的BUG
3. 所有通知渠道支持多用户。

2022.02.26
1. 馒头这两天抽风，每次搜索都会出Cloudflare 5秒盾验证，新版的机器人增加了浏览器内核，可以模拟人工验证，修复了这个问题，支持自动跳过所有PT站的5秒盾验证。


2022.02.23
1. 新增豆瓣详细配置，可以根据豆瓣想看的标签，决定选择策略以及对关键字加权，这个关键字可以是字幕组、压制组、站点名（英文跟pt部分配置一样）。可以根据不同的豆瓣id，选择策略；
2. 新增通知时增加评分显示，来自谁的豆瓣昵称下载；
3. 新增fanart API，下载完成发送通知时，会优先去fanart查找电影封面图，其次TMDB，最后用豆瓣的；
4. 优化下载电影过程，全面加速。增加查找缓存，多PT站点并行搜索；除首次运行任务外，多pt站时处理速度至少是以前版本的十倍；
5. 优化Emby智能刷新功能的媒体库识别；
6. 优化豆瓣多id想看时，重复电影的处理；
7. 修复手动挡下载时，部分资源解析会出错的BUG

2022.02.21
1. sqlite操作类加锁，同时优化监控种子任务的错误处理，增强稳定性；
2. 修复部分emby用户无法局部刷新影视库的BUG；
3. 修复Emby在Widnows部署时部分情况无法正确识别媒体库的BUG
4. 新增站点支持btschool、putao

2022.02.20
1. 感谢大佬 miniers 贡献代码，支持了chdbits、keepfrds
2. 优化手动提交种子任务监测的通知友好性，对自由下载的剧集，识别集数信息；
3. 硬链接整部剧集是忽略音频文件

2022.02.19
1. 优化剧集数识别，认识回話，增加几个日漫命名格式。
2. compress策略将remux分数定义翻倍，绝对碾压其他权重。
3. 对pt站匹配不到年份的种子，放行，不做验证。

2022.02.17
1. 重磅更新：任何自己添加到下载器的种子，都可以被机器人监控到，被监控的种子，监控下载完成时，会自动做影视识别和硬链接或复制，同时发送通知；这个功能可以让不喜欢使用豆瓣想看体系的用户，享受机器人的识别整理改名功能；
2. 机器人的搜索方式，从以前的通过豆瓣上电影名称搜索，改为通过imdbid去pt站搜索。这可以有效避免复杂影视名称搜不到结果的问题，如日漫，和很长的电影名字。同时通过imdbid搜索的方式，也不会对年份做强验证，一些种子名称不规范年份不对而被机器人过滤的问题应该不会存在了。当然如果一个电影没有imdbid，还是会采用电影名去搜索；
3. 从豆瓣想看的电影下载完做识别和硬链接时，会将豆瓣的电影信息和年份给到识别器，让识别的准去率更高，未来可能还会直接给imdbid；
4. 升级优化默认的三套选种策略，详细说明：https://feather-purple-bdd.notion.site/12f6d44243194c8c96a7e000b9dde023
5. 回归老版本启动逻辑，docker容器第一次启动时，默认执行一次任务；

2022.02.15
1. 修复PT站存在emoji表情时导致搜索失败的BUG；
2. 修复因剧集智能整理改动，导致追剧选种解析错误的一个BUG，追剧集数选择有问题的朋友需要更新；
3. 修复TR下载器卡死会导致监测任务报错的BUG；

2022.02.14
1. 正式推出电影和电视剧智能管理Beta版！通过机器人下载好的影视，会自动识别影视信息，然后采用硬链接或复制的方式，以标准的影视命名，链接到指定的新目录，完美解决影音服务的刮削识别问题，帮它找好tmdbid！

2022.02.11
1. 支持电影文件管理功能，将下好名称乱七八糟的资源，统一整理为电影名+年份的标准文件夹结构，同时填入tmdbid，帮助影音服务器完成刮削；支持将多版本电影格式，合并到一个文件夹内，让Emby这种影音服务器可以播放时选择不同版本；整理后的文件可以选择采用硬链接或复制的方式，整理到新的目录，不会影响原有文件做种；（电视剧整理很快将会放出，敬请期待）

2022.02.08
1. 修复了使用transmission提示下载失败且无法推送的BUG
2. 增加企业微信推送支持


2022.02.06
1. 新增本地数据库，对下载记录做记录，一些看完从影视库删除或下载工具删除种子的电影，如果还未取消豆瓣想看，不会出现重复下载的BUG了。pt站再下载完成间隔增加新种子可能导致选到新种重复下载的BUG也修复了；
2. 新增通知系统，当前暂时只支持Bark通知；
3. 新增下载种子状态监听功能，当种子下载完成时，可以通过配置的通知方式，发送通知；
4. 新增两套规则配置，名称分别是compress、compact，全压缩选种规则和紧凑型存储空间选种，这两种新增的规则，全压缩版不会再出现emby无法播放的蓝光原盘内容，紧凑型会格外注重视频压缩质量，同时优先匹配1080为主的视频，体积会小很多；
5. 优化规则中name_keywords字符串匹配不区分大小写；
6. 优化pt站检索结果，增加种子id的识别；
7. 优化选种打分逻辑，更客观的打分逻辑；
8. 优化下载保存模式，增加区域（area）细分匹配项，同时cate和area都支持多个并且匹配模式；
9. 修复电视剧名称含有‘话’的分集方式可能识别错误的BUG；

2022.02.02
1. 优化日志输出形式，由以前的stdout调整为可写本地文件以及stdout，日志文件目录在映射的/data目录下


2022.02.01
1. 增加支持新站点ssd
2. 支持Plex媒体服务

2022.01.31
1. 新增支持hdchina；
2. 优化归一化实现及部分打分逻辑，增强选种效果；
3. 优化剧集选择逻辑，增加文件尺寸估算算法，来确认资源是否真的包含全集资源（很多站资源标题规则不一致，比如 权力的游戏第八季，无法通过名字准确识别到底包含了整季资源还是部分资源）；


2022.01.30
1. 重新设计实现了剧集（综艺、电视剧）的选种逻辑，如果你在豆瓣点了一部想看的电视剧，如果这部剧还没更新完，初次下载，会帮你把已更新剧集的种子，都下上。如果你已经有了最新的剧集，只要出新的，就自动帮你下最新一集；如果一部剧已经完整的更新完，则会选择全集资源包优先下载；
2. 加速PT站点第一次访问速度；

2022.01.28
1. 修复tjupt初次下载或很久没在页面点下载需要手动确认导致失败的BUG；
2. 修复Qbit下载工具web api登陆过期无法正常使用的BUG；
3. 修复cookie对多余分号处理错误的BUG；

2022.01.27
1. 增加pt站点北洋园支持
2. 豆瓣支持cookie登陆，解决极其罕见的电影信息需要登陆获取的问题
3. 修复hdsky下载数取成正在下载数的BUG；
4. 修复单个pt站点挂了，导致其他pt站搜索不可用的BUG；

# 赞赏一下
<img src="https://yee-1254270141.cos.ap-beijing.myqcloud.com/movie_robot/pay.jpg" width="310" height="310" alt="赞赏码" style="float: left;"/>

# 作者微信
微信号：yipengfei329
