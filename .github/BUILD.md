# 构建发布流程（自己用）
#
# 1) 打包（在项目根目录）
#    python -m PyInstaller build.spec --noconfirm
# 2) 压缩
#    Compress-Archive dist/JX3WorkbenchLocal.exe JX3WorkbenchLocal_vX.Y.Z.zip
# 3) 发布（私有仓库 + Release 附件，不开源）
#    gh release create vX.Y.Z JX3WorkbenchLocal_vX.Y.Z.zip --title ... --notes ...
#    （或网页拖拽上传）
#
# 注意：Release 附件对私有仓库同样只有协作者可见 —— 不开源+公开下载
# 二者天然矛盾，见下。

# 不开源但可公开下载 exe 的方案对比：
# 方案 A：public 仓库 + 只有 exe/README，不放源码
#   - Releases 任何人可下载；仓库里没有 .py 源文件即"不开源"
#   - 最简单直接 ✅
# 方案 B：private 仓库 + Release
#   - 附件只有协作者能下，分享要拉人 ❌
# 方案 C：GitHub Releases 的 public 附件 + private 源码仓
#   - 需要两个仓库，发布走 gh CLI 跨仓传附件
#   - 源码彻底私有，exe 公开 🔒
#
# 推荐 A（简单）或 C（源码更私）。本仓按方案 A 组织。
