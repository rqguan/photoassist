功能说明
三个滑块：

相机到凸面镜（0–5 m，2 m 内 5 cm 步进，2 m 外 10 cm 步进）
物体到凸面镜（10 cm → ∞，对数映射，滑到最右即无穷远）
曲率半径 R（5–250 cm，对应球体直径 10–500 cm，小半径处分辨率更高）

实时显示：

SVG 示意图：光轴、凸面镜（带背面斜线示意）、焦点 F、相机图标、物体箭头、虚像（虚线箭头）、实际光线（物→反射点→相机）、虚像延长线
结果卡片：对焦距离（主要结果）、虚像位置、焦距 f、放大倍率

核心公式： 1/d_o + 1/d_i = −2/R → D_focus = d_camera + |d_i|
发布到 GitHub Pages
既然你已有仓库，把 index.html 放在仓库根目录即可：
A. 如果仓库名是 你的用户名.github.io（user/organization site）

把 index.html 复制到仓库根目录，git add index.html && git commit -m "add convex mirror focus calc" && git push
访问 https://你的用户名.github.io/ 即可

B. 如果是普通项目仓库（比如 photo-tools）

同样把 index.html 放仓库根目录并 push
到 GitHub 仓库页面 → Settings → Pages → Build and deployment → Source 选 "Deploy from a branch"，Branch 选 main（或 master），folder 选 / (root) → Save
一两分钟后访问 https://你的用户名.github.io/photo-tools/

如果想放子目录（例如 /mirror/ 下，和其他页面共存）：把文件改成 mirror/index.html 放进仓库，URL 对应变成 https://你的用户名.github.io/<repo>/mirror/。
需要的话我可以改文件名、加自定义 favicon、或者调整曲率/距离滑块的手感，告诉我就行。IndexCode · HTML Google ChromeYou said: 镜面请用实线表示。然后三者之间的距离可以不用真实比例等比表示，大致示意一下就行了，然后凸面镜可以画大一点。也是示意就行，不用真实比例，10厘米直径和5米直径可以让镜面高度一样，弧度变化就好了。镜面请用实线表示。然后三者之间的距离可以不用真实比例等比表示，大致示意一下就行了，然后凸面镜可以画大一点。也是示意就行，不用真实比例，10厘米直径和5米直径可以让镜面高度一样，弧度变化就好了。Claude responded: 收到——把镜面改成纯实线，去掉斜线阴影；距离采用对数示意（不按真实比例）；镜面固定在恒定高度，只让曲率变化。重写绘图函数。 Let me render a few SVG samples directly so I can verify the new layout visually.收到——把镜面改成纯实线，去掉斜线阴影；距离采用对数示意（不按真实比例）；镜面固定在恒定高度，只让曲率变化。重写绘图函数。Edited a file, ran a commandEdited a file, ran a commandLet me render a few SVG samples directly so I can verify the new layout visually.Ran 5 commands, read 5 filesRan 5 commands, read 5 filesThe layout is working. Let me fix two small overlaps (F label and img label collide) and handle the infinity-object case more gracefully.Edited 4 filesEdited 4 filesLet me re-render to verify the fixes.Read 2 files, ran a commandRead 2 files, ran a commandGood — the fixes work. Let me clean up the test PNGs so the outputs folder only contains the deliverable.Ran 2 commands, loaded tools, used a toolRan 2 commands, loaded tools, used a tool已按你的要求更新：

镜面改成纯实线，去掉斜线阴影等额外装饰
固定镜面高度 — 不管 R=5cm 还是 R=250cm，镜面的屏幕上垂直高度都一样，只有弧度随 R 变化（小 R 变半球，大 R 近乎竖直线）
距离采用对数示意 — 10cm 到 5m 的距离都会在同一张图里清楚分布，不再按真实比例，相机、物体、虚像始终可见
顺手修了两个小问题：F 标签移到轴下方避免和「虚像」碰撞；物体 @ ∞ 时在左边缘淡化显示物体箭头，并多画一条水平平行光线+经 F 的虚线，示意「无穷远光经 F 成像」

打开 index.html
文件就一个 index.html，放到你仓库的根目录 push 一下，按之前说的 Pages 设置就能用。如果还要调（比如镜面再大一点、颜色、字号等），告诉我就行。IndexCode · HTML Google ChromeYou said: 简单告诉我如何文件逻辑，需要上传哪些至github？简单告诉我如何文件逻辑，需要上传哪些至github？Claude responded: 只需要上传 一个文件 到仓库根目录：只需要上传 一个文件 到仓库根目录：
index.html — 全部内容（HTML 结构、CSS 样式、JavaScript 物理计算和 SVG 绘图）都打包在这一个文件里，不依赖任何外部资源、不用打包、不用构建。
放进仓库后的目录结构：
你的仓库/
└── index.html
就这样。GitHub Pages 看到根目录有 index.html 就会把它作为首页提供。访问 https://你的用户名.github.io/仓库名/ 即可（如果仓库就叫 你的用户名.github.io，那就是 https://你的用户名.github.io/）。
