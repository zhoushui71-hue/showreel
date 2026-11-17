Showreel 素材说明
==================

本目录（demo_media/）存放 showreel.html 的全部媒体文件，同名替换即可生效。

Showreel 视频：自动识别，不用改文件名
------------------------------------
把视频（mp4 / mov / mkv / webm / avi 都行）丢进 showreel/ 目录，
然后双击 showreel\打开作品集.cmd（它会先跑 tools\scan_showreel.ps1）：

  1. 自动挑出 showreel/ 里最新的那个视频
  2. 浏览器能直接放的（mp4/webm + H.264/VP8/VP9/AV1）→ 直接用
     放不了的（.mov、HEVC、ProRes、.mkv 等）→ 自动用 ffmpeg 转成 H.264 的
     showreel_web.mp4（1920 上限、CRF 20、faststart）
  3. 自动从这个视频抽一帧做封面 posters/showreel_auto.jpg（16:9）
  4. 把结果写进 showreel/auto.js，页面读它来播放

想手动刷一次（不打开网页）：右键「打开作品集.cmd」→ 运行；
或命令行执行：powershell -ExecutionPolicy Bypass -File tools\scan_showreel.ps1

目录结构
--------
showreel/                    主 Showreel 视频（放任意名字的视频，自动识别）
showreel/auto.js             自动生成，勿手改（记录当前播放哪个文件）
posters/showreel_auto.jpg    自动生成的封面（每次扫描重新抽帧）
posters/showreel.jpg         兜底封面（自动抽帧失败时用）

hero/<key>.jpg               首屏海报带用图（共 27 张，均来自公开渠道）

hero 海报清单（key ← 作品）
---------------------------
shengmingzhiguang  生命之光（方特，官网图）—— 已按要求从页面移除，文件保留备用
nezha2             哪吒之魔童闹海
shoulongzhe        守龙者
earth3             流浪地球3
hotpot             火锅艺术家
jiubu              九部的检察官
chunhuayan         春花焰
tianyuan           王者荣耀 · 敬我三分 / 天元（B站封面）
oncehuman          七日世界 · 雪国人生（Steam）
baoshuiguan        爆水管
mingrileyuan       明日乐园
marvelrivals       漫威争锋 · 永夜降临（Steam）
beihuigui          北回归线以北
huangyanzhiqu      谎言之躯
teliduxing         特立独行
mingyue            明月苍茫
fanying            凡应（B站封面）
qunxing            群星闪耀时
wangu              万古最强宗
wuzhen             永劫无间 · 巫真（B站封面）
xiaoyao            逍遥
hearthstone        炉石传说 · 大地的裂变（B站封面）
sanguo             三国的星空
yuelin             月鳞绮纪
endfield           明日方舟：终末地 · 莱万汀（B站封面）
shenghuan          生还
ziyegui            子夜归
linglong2          灵笼 第二季

说明
----
- 海报来自豆瓣 / B站 / Steam / 方特官网，版权归原方，仅作个人作品集展示。
- 顺序、增删、作品名在 showreel.html 顶部 DATA.heroWorks 里维护。
- 视频若需转码/抽帧（本机 ffmpeg）：
  C:\Users\zhouhaibin\AppData\Local\ffmpeg\ffmpeg-9.0.2-full_build\bin\ffmpeg.exe
  例：ffmpeg -i "源.mov" -vf "scale=1280:-2" -c:v libx264 -crf 21 -preset veryfast -an "showreel_2025.mp4"
