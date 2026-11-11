# PaddleOCR-VL 论文学习课程 V3

在线入口：[PaddleOCR-VL 论文学习课程](https://imYuu-dev.github.io/paddleocr-vl-study/)。本地入口为 `index.html`。正文、交互、论文图表和 PPT 预览均使用仓库内资源，外部参考链接需要网络。

本地预览：在仓库目录运行 `python -m http.server 8766 --bind 127.0.0.1`，打开 `http://127.0.0.1:8766/`。也可直接打开 `index.html`；本轮浏览器验收使用 Edge 的本地 HTTP 页面，未将文件协议访问记为已验收。

## 内容与原始材料

- 保留原 V2 的 9 个模块 ID，与现有 14 页 PPT 的映射不变；课堂 PPT、下载目录中的原 V2 均未改动。
- 课程按“先看同一页文档，再命名任务，再让方法沿着问题出现”的顺序展开：hero 只做简短课程入口；m1 从人读页面、程序批量整理和跨论文对照的需要讲起，再给文档解析命名；m2–m9 用承接上一模块的导语、图前说明和图后解释推进。学习目标已移到每模块正文之后，作为回看提示。
- 9 个模块的 ID、14 页 PPT 映射、23 道测验的答案与原索引/显示顺序均保持不变；没有新增卡片或交互。同一张合成文档贯穿区域定位到文档重建，教学示例没有实际运行模型。
- 正文与补充材料是技术和数值依据；官方实现、教学简化及分析判断分别标注。原始图表出处、裁剪位置与 SHA256 见 `assets/paper/sources.json`，本轮官方资料记录见 `assets/paper/official-sources.json`。
- 论文原图包括 Figures 2、3、4（含局部）、S1、S5、S12，以及 Tables 1、2、7、S2。点击可放大。
- 当前没有接入新的 RTX 3090 实测产物。P13 的结果仍待补，网页不声称已完成论文实验复现。

## 学习记录

继续使用 `paddleocr-vl-study-progress-v2`。已有完成记录和练习文字会保留；新增测验与自检独立保存。测验的显示顺序调整不改变保存的原选项索引。

浏览器会按来源隔离本地记录。跨文件、端口或浏览器学习时，先在原页面导出，再到 V3 的“学习工具”中导入；不能保证浏览器自动迁移不同文件来源的 localStorage。导入采用合并方式，同一模块的导入练习覆盖当前同名练习，导入前建议先导出当前记录。

## 脱稿演练

点击顶栏“脱稿演练”或本节“进入脱稿演练”，会立即打开独立演练面板。面板展示当前模块对应的 PPT 和复述任务，先用自己的话讲，再展开参考要点检查。多页模块可以切换 PPT，图片可放大。卡住的地方可以记在面板中，记录会自动同步到原有模块练习。关闭面板或按 Escape 返回学习。手机端还可从“学习工具”进入。

## 维护

- `assets/course/modules.js`：课程数据。
- `assets/course/course.js`：导航、记录、测验与教学交互。
- `assets/course/course.css`：阅读布局和响应式样式。
- `maintenance/build_content.py`：文案生成源；依赖 Python 与 BeautifulSoup。修改文案后运行 `python maintenance/build_content.py`，重新生成 `modules.js` 和供审查阅读的文本。
- `maintenance/base-modules.json`：保留模块 ID、PPT 映射和原始题目结构的基础数据。最终文案与修正以生成脚本为准。
- `review/`：公开审核摘要、浏览器验收 JSON 与真实截图。9 份模块审查和整站会话保留在本地，由 `.gitignore` 排除。
- `review/叙事调整说明.md`：本轮开场与 m2–m9 文字引导的改动范围、保留项和验收记录。

## 验收与边界

2026-11-11 完成浏览器验收：1893、1440、1280、390px × 9 模块无整页横向溢出，运行期 JavaScript 错误为 0。1893px 下主阅读容器约 1216px，正文 17px，交互解释 16px，移动端正文 16px。实际检查导航、PPT 面板、原图放大、脱稿、23 道测验错答与重答、进度刷新保存及导入导出。本轮叙事重写后另在 1256px 检查 m1/m2 的导语、目标回看、测验错答与重答，在 390px 检查表格滑动提示、键盘聚焦和文档放大。

生成流程已重跑：`python maintenance/build_content.py` 输出 9 个模块，`node --check assets/course/course.js` 与 `node --check assets/course/modules.js` 均通过；测验仍为 23 题，正确项的显示位置为 8/8/7，原选项索引和 localStorage 键未改。

9 个模块均按“承接上一模块—说明本节看什么—读图/读表—回到问题”的顺序补充了正文引导，技术讲解与原有图表、交互均保留。

脱稿功能随后按实际使用反馈改为独立演练面板，单独完成了四种宽度、PPT 切换与放大、提示展开、记录同步和刷新保存的浏览器检查，见 `review/browser-rehearsal.json`。

移动端使用 390×844 模拟视口；未做真机、Safari、Firefox 或完整读屏验收。打印入口保留，打印排版未专项验收。未测试模型推理，教学交互结果不能作为复现实验结果。

## 发布

本课程独立仓库为 [imYuu-dev/paddleocr-vl-study](https://github.com/imYuu-dev/paddleocr-vl-study)。GitHub Pages 使用 `main` 分支根目录，`.nojekyll` 让静态文件直接发布。部署时不上传实验环境、模型权重或其他课程资料。
