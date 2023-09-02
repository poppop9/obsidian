---

excalidraw-plugin: parsed
tags: [excalidraw]

---
==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠==


# Text Elements
运行 ^oxOP0Utq

就绪 ^iLJcKvzQ

阻塞 ^aPPCLE2Z

外围设备发出
中断请求 ^j6PemskW

中断请求完成 ^AYP7mVcA

调度 ^Loj536g4

取消调度 ^1ZbCAwKp

发起之后就被阻塞了 ^e03kQ2OF

当I/O完成了，
系统也决定不切换回Process0，
而是先运行完Process1 ^HLLBvgGb

目前还不清楚这是不是一个很好的决定 ^HdkSqwvW

A的周转时间为10 ^MhAath92

B的周转时间是20 ^9z061qqw

C的周转时间是30 ^f4iyWtOc

所以平均周转时间为20 ^mG0oQvM6

平均周转时间为110 ^TQvfup9D

（10+20+120）/3=50 ^KAdgCxNx

（100+100+110）/3=103 ^sY7Rd6ze

（120+10+20）/3=50 ^OOuJVjKR

平均响应时间：（0+5+10）/3=5 ^RziUoLz1

平均响应时间：（0+1+2）/3=1 ^cfsaKuZR

这里的时间片长度为1 ^YVP4Jram

IO操作占用的时间 ^DmyZqJbE

采用STCF，把A分解成了5个子任务。
当A完成时，则会调用B【重叠】 ^rgOvQoGA

如果A的优先级 > B的优先级，运行A
如果A的优先级 = B的优先级，轮转运行A和B ^OwaWQP2e

一个队列中可以有多个工作 ^fW50daGl

短工作 ^oety4ZOH

长工作【优先级低】 ^mMYjQ05I

每次都在时间片以内，
始终保持优先级队列 ^0SuYh6wv

交互型工作 ^MjJj6myH

密集型工作 ^MYUE1qIw

定期提升优先级，
保证了Q2上的长任务有机会执行 ^v9YaSvNj

在此刻加入了 2 个交互型任务后，
这个长任务就没有机会执行了 ^DLDzDS37

一个颜色代表一个任务 ^KB8FqAPF

这个任务打擦边球，
在高优先级一直占
用CPU ^CwvZs3S9

时间份额用完，降低优先级 ^rjfDbLvF

时间份额用完，降低优先级 ^MyfwWWIS

2个任务优先级相同，
轮转运行 ^dBmA5gCq

B只占用了20%，而不是25%。 ^abM8uh58

大家行程值都相同，随机运行 ^fCy4FSNu

C的行程值最少，运行C ^WyPe77Xy

正好是票数比例：200：100：50 ^DlhrJSer

物理内存 ^xNYtLlHM

同时放进进程A,B,C ^haj0Q2jl

堆和栈都会增长，
所以放在首尾 ^iJEbhNnt

假设只有这
三个部分 ^i4NuqFoW

进程自己世界里的内存模样
【以为整个物理内存都是它的】 ^LWNZJvRj

进程实际在物理内存中的模样 ^FSIZyEcZ

段寄存器 ^f3mZCbHq

00 代码段
01 堆
10 栈 ^mAhLhW3L

这是段内偏移【与基址寄存器的偏移量不同，
这是在虚拟地址空间中某一段的偏移量，
而基址寄存器里的是虚拟地址与实际物理内存地址的偏移量】 ^9LY24N69

空闲列表： ^CjkU7Vqh

记录了内存中的空闲空间 ^VCOzUOze

申请一块 1 字节的空间，
对malloc()的调用返回20 ^4Q83cSMf

调用free(10) ^96apIcZw

分割 ^tau57uKD

合并 ^bUmgmTni

头块 ^t2vs7l5I

幻数【提供完整性检查】 ^88N7V51M

所分配的空间大小 ^JgNmTv4P

什么都没有分配的堆，
已经有了一块头块【就是空闲列表】 ^OhHXyy46

head指针，
永远指向最
新释放空间
的空闲列表 ^DN22q8o9

分配了一个
100字节
的空间 ^RPX2gkTz

8字节 ^Ztxvw7Do

8字节 ^DUFF65Ov

再多分配两块100字节的空间 ^dITK0Dp8

free(16500) ^U00k7YMD

16384 ^2aL1wv1h

16500 ^kaElSfA7

head指针指向了最近空闲的内存块，
next指针指向了下一个空闲空间 ^yn1S2BAQ

效率太低，进行改进 ^hTkWhbS1

有一个15字节的内存请求 ^9tleUbQN

有一个15字节的内存请求 ^wDdTu4s3

请求7KB空间时 ^3iX0xWbR

由于是64字节的虚拟地址空间，
所以需要6位 ^dMBD23zU

1页是16字节，我们许需要4个页，
所以是2位 ^ZHuOcDcF

1页是16字节，需要4位 ^Dv28gwor

通过检索页表，
查看第1页对应的物理内存
的页帧是多少 ^EsYfloZR

转换成汇编语言 ^NZXMgOdr

一次循环，
有10次内存访问【
取指令4次，
更新数组内容1次，
为取指令和更新数组内容转换地址访问页表5次】 ^0SqMivvV

左侧是虚拟地址 ^jAeC0Mnb

右侧是实际物理地址 ^FXFMavz5


# Embedded files
454670cd9adffa50c0af576e05b867602ba3ef08: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/F2BFC2F7D79770F61232BE642A007198.png
a0344871c2a64517e259279b4b10259e1a13c17c: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230726094836.png
34a27741a5e7174bfade884abb1246971002a3e3: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230728092835.png
f1e77ce44f535f26f301777d20799984f279d22f: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230728095009.png
1a626a2966d1506daa8a8d49aa7343f7a83dcd39: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230728095438.png
52985c51d47488539f08e5dc22967bce6a89f137: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230728103605.png
f9dabb7062e80ba2721ef40b5407083d16a0f3a8: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230728110326.png
3f4086b97cd8da9c677349ec9664ec1c968ce1c1: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230728214113.png
accac7ae132ac6ff81539bef638aab7fb894549f: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230728214335.png
fd470d5e48d8b3277ccf52859b79ed014318ff0e: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230730102128.png
136b227d07f37bb6b34c272c4d9bf4ec4de206ac: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230730110141.png
a1b9705d0b40a5f5f3f5724db67ef20f7b9e86f8: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230730200139.png
3ad3865931a4221b5e2d986391f8c4b039ec3f3b: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230731151343.png
55dd212aa228686f79648c6a9d4f0636e6110cdf: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230731153217.png
eb511ed232f8c7a646a78978586fd895a67788ff: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230731165131.png
c7e0d943887f8fbf110d5e85eb4b4557709543ac: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230802123059.png
dbc8c15eaa293b2602301df3136b0f95e1508dc9: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230805102410.png
70f8389cc1c9b5eccab3104e7e2cfba95ac3e253: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230805103538.png
889b093b5c1af4caca62a4472a7b861da309a87f: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230805110633.png
27e14326786f518d58092c806822f8f3001069a2: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230805115612.png
58059b01d99a02d27936ec69963f77216e1c6c6c: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230805115646.png
9816f3eb4e7f0d7b970cd033c5a64ae595e925ce: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230807220908.png
d63bd18816e78c7a6c5c337825b92402518f4297: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230807223003.png
9165f3ba06d92e72b786ca67fd61fc11cd5607c7: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230810222612.png
344bf0e8d16402d22ca7d0a7501b90963234407c: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230812093911.png
4b30d1da827c9272daf1ea66bfa08a7d4290b01d: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230812093949.png
5774fbd4e902a80afea12f63535d5da8fff81e26: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230812094432.png
816d06f5c9e22b960e8a91b1025efbf7ab1abf2c: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230812094717.png
54e6ed166ef74e32fb43fbbb9bcc02964e675fc8: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230812094746.png
92ba2bbae35919cf05722392beb53b474b271c68: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230812095645.png
91440f29495dde4eeb4977c0da92426097f4a710: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230812102235.png
771ede9c64847bcb37135bde6607367e3c85870a: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230812102541.png
bee97a857575f2db63d1ad2dd78ce33d3f642596: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230812103044.png
d14cd6a75258249e3d9bb7ef2911d7d9d01f0775: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230812103912.png
7ad283b1c9740c65f79ddf0c29a1c90eab55876d: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230814202309.png
04d8afd8f2d1092479b19ca2efb233766bafa5bd: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230814202411.png
d45fc0ee2c4264733677a01eaff1a751e39fa075: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230814202756.png
e513217fd720598d5c5cc32bea61835cdf22912a: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230815201059.png
4fcfa8e12ab188ba46a43795a3ca39fe8b6937e1: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230815205232.png
227e27e893c2025f22851992d4c40a498cd05475: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230816111309.png
1bf3b5ac9073f798754998ea32c44112d213a3d0: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230816113452.png
45dd7c8c8ca8e96b0ddfcbd0628c42bec2a91b9b: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230816211302.png
557466c35827834b1f191decd741a931d15faef9: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230816211330.png
57a567fe869705a49cc0f28cf46c2ae21a97f3fe: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230816211446.png

%%
# Drawing
```json
{
	"type": "excalidraw",
	"version": 2,
	"source": "https://github.com/zsviczian/obsidian-excalidraw-plugin/releases/tag/1.9.16",
	"elements": [
		{
			"type": "ellipse",
			"version": 114,
			"versionNonce": 1171136984,
			"isDeleted": false,
			"id": "Rtlv2f-IRxbCmA8eWSrGi",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -307.59999084472656,
			"y": -247.4499969482422,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 148,
			"height": 132,
			"seed": 1082961384,
			"groupIds": [
				"GzXvyvVvRqv8jMFTf5NpS"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "oxOP0Utq"
				},
				{
					"id": "NQTY63-glZv0vm_4it5V1",
					"type": "arrow"
				},
				{
					"id": "LkEB4YwZNwgUZxLr8e4wd",
					"type": "arrow"
				},
				{
					"id": "KJqlrlIN6VlmCkJM--ekJ",
					"type": "arrow"
				}
			],
			"updated": 1692192358617,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 44,
			"versionNonce": 1593804712,
			"isDeleted": false,
			"id": "oxOP0Utq",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -253.4258926525311,
			"y": -194.11904450655433,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 40,
			"height": 25,
			"seed": 805189272,
			"groupIds": [
				"GzXvyvVvRqv8jMFTf5NpS"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358617,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "运行",
			"rawText": "运行",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "Rtlv2f-IRxbCmA8eWSrGi",
			"originalText": "运行",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "ellipse",
			"version": 211,
			"versionNonce": 945563352,
			"isDeleted": false,
			"id": "lUzkA58_CB57XNUZYSebn",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 44.5999755859375,
			"y": -251.04999542236328,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 148,
			"height": 132,
			"seed": 960937880,
			"groupIds": [
				"GzXvyvVvRqv8jMFTf5NpS"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "iLJcKvzQ"
				},
				{
					"id": "Io5xQu7oTa5_pWmIuxtTs",
					"type": "arrow"
				},
				{
					"id": "LkEB4YwZNwgUZxLr8e4wd",
					"type": "arrow"
				},
				{
					"id": "KJqlrlIN6VlmCkJM--ekJ",
					"type": "arrow"
				}
			],
			"updated": 1692192358617,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 98,
			"versionNonce": 671109800,
			"isDeleted": false,
			"id": "iLJcKvzQ",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 98.77407377813299,
			"y": -197.71904298067543,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 40,
			"height": 25,
			"seed": 1495495656,
			"groupIds": [
				"GzXvyvVvRqv8jMFTf5NpS"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358617,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "就绪",
			"rawText": "就绪",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "lUzkA58_CB57XNUZYSebn",
			"originalText": "就绪",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "ellipse",
			"version": 182,
			"versionNonce": 350325720,
			"isDeleted": false,
			"id": "YJsZfOqA7Gtu-ar9iyGnR",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -146,
			"y": 19.550025939941406,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 148,
			"height": 132,
			"seed": 27113880,
			"groupIds": [
				"GzXvyvVvRqv8jMFTf5NpS"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "aPPCLE2Z"
				},
				{
					"id": "NQTY63-glZv0vm_4it5V1",
					"type": "arrow"
				},
				{
					"id": "Io5xQu7oTa5_pWmIuxtTs",
					"type": "arrow"
				}
			],
			"updated": 1692192358617,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 75,
			"versionNonce": 1286585768,
			"isDeleted": false,
			"id": "aPPCLE2Z",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -91.82590180780451,
			"y": 72.88097838162926,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 40,
			"height": 25,
			"seed": 81415320,
			"groupIds": [
				"GzXvyvVvRqv8jMFTf5NpS"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358617,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "阻塞",
			"rawText": "阻塞",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "YJsZfOqA7Gtu-ar9iyGnR",
			"originalText": "阻塞",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 430,
			"versionNonce": 692745253,
			"isDeleted": false,
			"id": "NQTY63-glZv0vm_4it5V1",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -208.2310420611622,
			"y": -107.86849501176921,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 79.20161926475106,
			"height": 131.9222424084445,
			"seed": 593684376,
			"groupIds": [
				"GzXvyvVvRqv8jMFTf5NpS"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "j6PemskW"
				}
			],
			"updated": 1693060909244,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "Rtlv2f-IRxbCmA8eWSrGi",
				"gap": 11.087545791284299,
				"focus": 0.22404905801162076
			},
			"endBinding": {
				"elementId": "YJsZfOqA7Gtu-ar9iyGnR",
				"gap": 14.451435034824556,
				"focus": -0.2395632459917809
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					79.20161926475106,
					131.9222424084445
				]
			]
		},
		{
			"type": "text",
			"version": 130,
			"versionNonce": 507103400,
			"isDeleted": false,
			"id": "j6PemskW",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -238.39999389648438,
			"y": -91.64998626708984,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 120,
			"height": 50,
			"seed": 839228056,
			"groupIds": [
				"GzXvyvVvRqv8jMFTf5NpS"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358617,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "外围设备发出\n中断请求",
			"rawText": "外围设备发出\n中断请求",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "NQTY63-glZv0vm_4it5V1",
			"originalText": "外围设备发出\n中断请求",
			"lineHeight": 1.25,
			"baseline": 43
		},
		{
			"type": "arrow",
			"version": 370,
			"versionNonce": 311601029,
			"isDeleted": false,
			"id": "Io5xQu7oTa5_pWmIuxtTs",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -8.441578168472645,
			"y": 30.792711801131333,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 82.09718858279156,
			"height": 150.32885526858826,
			"seed": 33872616,
			"groupIds": [
				"GzXvyvVvRqv8jMFTf5NpS"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "AYP7mVcA"
				}
			],
			"updated": 1693060909246,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "YJsZfOqA7Gtu-ar9iyGnR",
				"gap": 13.585005876849507,
				"focus": 0.4088685544582503
			},
			"endBinding": {
				"elementId": "lUzkA58_CB57XNUZYSebn",
				"gap": 11.138046142882217,
				"focus": 0.11135914987346074
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					82.09718858279156,
					-150.32885526858826
				]
			]
		},
		{
			"type": "text",
			"version": 69,
			"versionNonce": 1749709736,
			"isDeleted": false,
			"id": "AYP7mVcA",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -30.79998779296875,
			"y": -62.34998321533203,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 120,
			"height": 25,
			"seed": 646310808,
			"groupIds": [
				"GzXvyvVvRqv8jMFTf5NpS"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358617,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "中断请求完成",
			"rawText": "中断请求完成",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "Io5xQu7oTa5_pWmIuxtTs",
			"originalText": "中断请求完成",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 340,
			"versionNonce": 1044105573,
			"isDeleted": false,
			"id": "LkEB4YwZNwgUZxLr8e4wd",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -152.0257020554332,
			"y": -226.2503177121891,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 189.64425902931373,
			"height": 2.4005536722719114,
			"seed": 1966973928,
			"groupIds": [
				"GzXvyvVvRqv8jMFTf5NpS"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "1ZbCAwKp"
				}
			],
			"updated": 1693060909239,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "Rtlv2f-IRxbCmA8eWSrGi",
				"gap": 21.115641554272898,
				"focus": -0.6943680085382985
			},
			"endBinding": {
				"elementId": "lUzkA58_CB57XNUZYSebn",
				"gap": 17.464899741750017,
				"focus": 0.572286156302868
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					189.64425902931373,
					2.4005536722719114
				]
			]
		},
		{
			"type": "text",
			"version": 47,
			"versionNonce": 554548904,
			"isDeleted": false,
			"id": "1ZbCAwKp",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -97.19998168945312,
			"y": -237.54999542236328,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 80,
			"height": 25,
			"seed": 213580008,
			"groupIds": [
				"GzXvyvVvRqv8jMFTf5NpS"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358617,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "取消调度",
			"rawText": "取消调度",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "LkEB4YwZNwgUZxLr8e4wd",
			"originalText": "取消调度",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 333,
			"versionNonce": 1093096645,
			"isDeleted": false,
			"id": "KJqlrlIN6VlmCkJM--ekJ",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 28.000020073594946,
			"y": -183.84999875952695,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 168.8000078665637,
			"height": 2.3999941818902357,
			"seed": 2113140888,
			"groupIds": [
				"GzXvyvVvRqv8jMFTf5NpS"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "Loj536g4"
				}
			],
			"updated": 1693060909241,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "lUzkA58_CB57XNUZYSebn",
				"gap": 16.609515705116394,
				"focus": 0.0013354542720273859
			},
			"endBinding": {
				"elementId": "Rtlv2f-IRxbCmA8eWSrGi",
				"gap": 18.800003051758168,
				"focus": 0.019988679018667053
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-168.8000078665637,
					2.3999941818902357
				]
			]
		},
		{
			"type": "text",
			"version": 40,
			"versionNonce": 422554024,
			"isDeleted": false,
			"id": "Loj536g4",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -76.39999389648438,
			"y": -195.1500015258789,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 40,
			"height": 25,
			"seed": 1859582872,
			"groupIds": [
				"GzXvyvVvRqv8jMFTf5NpS"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358618,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "调度",
			"rawText": "调度",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "KJqlrlIN6VlmCkJM--ekJ",
			"originalText": "调度",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "image",
			"version": 117,
			"versionNonce": 305603800,
			"isDeleted": false,
			"id": "hJsj1Yfi",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -388.4000549316406,
			"y": 206.89010667212216,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 500,
			"height": 398.91975308641975,
			"seed": 89387,
			"groupIds": [
				"jshBrvj3v-5xmGj6pZngD",
				"XtD9BB7-vShxy4ccPM3U2"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "q4xVOtoLXjkmvSE0buQ6l",
					"type": "arrow"
				}
			],
			"updated": 1692192358618,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "454670cd9adffa50c0af576e05b867602ba3ef08",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "arrow",
			"version": 171,
			"versionNonce": 735851688,
			"isDeleted": false,
			"id": "IfBwVKApnuAJT8kHXJgC1",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -8.00006103515625,
			"y": 336.7499465942383,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 116.79998779296875,
			"height": 2.884269507591398,
			"seed": 106432232,
			"groupIds": [
				"jshBrvj3v-5xmGj6pZngD",
				"XtD9BB7-vShxy4ccPM3U2"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358618,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "e03kQ2OF",
				"focus": 0.14972247039855127,
				"gap": 8
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					116.79998779296875,
					-2.884269507591398
				]
			]
		},
		{
			"type": "text",
			"version": 163,
			"versionNonce": 917293528,
			"isDeleted": false,
			"id": "e03kQ2OF",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 116.7999267578125,
			"y": 321.14994049072266,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 180,
			"height": 25,
			"seed": 1781916824,
			"groupIds": [
				"jshBrvj3v-5xmGj6pZngD",
				"XtD9BB7-vShxy4ccPM3U2"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "IfBwVKApnuAJT8kHXJgC1",
					"type": "arrow"
				}
			],
			"updated": 1692192358618,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "发起之后就被阻塞了",
			"rawText": "发起之后就被阻塞了",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "发起之后就被阻塞了",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 184,
			"versionNonce": 1858035624,
			"isDeleted": false,
			"id": "q4xVOtoLXjkmvSE0buQ6l",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -52.800048828125,
			"y": 477.54996490478516,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 194.39996337890625,
			"height": 19.677315600107192,
			"seed": 584986776,
			"groupIds": [
				"jshBrvj3v-5xmGj6pZngD",
				"XtD9BB7-vShxy4ccPM3U2"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358618,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "HLLBvgGb",
				"focus": 0.7407624313656578,
				"gap": 3.99993896484375
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					194.39996337890625,
					-19.677315600107192
				]
			]
		},
		{
			"type": "text",
			"version": 315,
			"versionNonce": 1730531032,
			"isDeleted": false,
			"id": "HLLBvgGb",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 145.599853515625,
			"y": 443.9499282836914,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 289.35992431640625,
			"height": 75,
			"seed": 1105722776,
			"groupIds": [
				"jshBrvj3v-5xmGj6pZngD",
				"XtD9BB7-vShxy4ccPM3U2"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "q4xVOtoLXjkmvSE0buQ6l",
					"type": "arrow"
				},
				{
					"id": "QcWyf7Qiygf5_TgN1317F",
					"type": "arrow"
				}
			],
			"updated": 1692192358618,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "当I/O完成了，\n系统也决定不切换回Process0，\n而是先运行完Process1",
			"rawText": "当I/O完成了，\n系统也决定不切换回Process0，\n而是先运行完Process1",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "当I/O完成了，\n系统也决定不切换回Process0，\n而是先运行完Process1",
			"lineHeight": 1.25,
			"baseline": 68
		},
		{
			"type": "line",
			"version": 124,
			"versionNonce": 1644505768,
			"isDeleted": false,
			"id": "I8t6JnKgQph27HkdAh6Ft",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 125.83540344238293,
			"y": 521.2688295340832,
			"strokeColor": "#e03131",
			"backgroundColor": "#ffffff",
			"width": 320.0000678168402,
			"height": 2.6666937934028283,
			"seed": 1186164774,
			"groupIds": [
				"XtD9BB7-vShxy4ccPM3U2"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358618,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": null,
			"points": [
				[
					0,
					0
				],
				[
					320.0000678168402,
					2.6666937934028283
				]
			]
		},
		{
			"type": "text",
			"version": 147,
			"versionNonce": 204878808,
			"isDeleted": false,
			"id": "HdkSqwvW",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 120.50215148925793,
			"y": 572.3799406451943,
			"strokeColor": "#e03131",
			"backgroundColor": "#ffffff",
			"width": 340,
			"height": 25,
			"seed": 1120494438,
			"groupIds": [
				"XtD9BB7-vShxy4ccPM3U2"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "QcWyf7Qiygf5_TgN1317F",
					"type": "arrow"
				}
			],
			"updated": 1692192358618,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "目前还不清楚这是不是一个很好的决定",
			"rawText": "目前还不清楚这是不是一个很好的决定",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "目前还不清楚这是不是一个很好的决定",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 174,
			"versionNonce": 542741928,
			"isDeleted": false,
			"id": "QcWyf7Qiygf5_TgN1317F",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 239.34604091225796,
			"y": 529.2688430974513,
			"strokeColor": "#e03131",
			"backgroundColor": "#ffffff",
			"width": 5.36085246833332,
			"height": 40,
			"seed": 2007432486,
			"groupIds": [
				"XtD9BB7-vShxy4ccPM3U2"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358618,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "HLLBvgGb",
				"focus": 0.29727440182339127,
				"gap": 10.318914813759875
			},
			"endBinding": {
				"elementId": "HdkSqwvW",
				"focus": -0.34139561304407695,
				"gap": 3.111097547743043
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-5.36085246833332,
					40
				]
			]
		},
		{
			"type": "image",
			"version": 58,
			"versionNonce": 1542584536,
			"isDeleted": false,
			"id": "lwSh7jW0",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -791.8378134833441,
			"y": -80.67658669083977,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 500.00000000000006,
			"height": 193.22412509307523,
			"seed": 82460,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358618,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "a0344871c2a64517e259279b4b10259e1a13c17c",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "image",
			"version": 70,
			"versionNonce": 250126504,
			"isDeleted": false,
			"id": "zYtSx3RS",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1109.1122483147512,
			"y": 191.20869336518112,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 675.8520231254464,
			"height": 160.5646760921448,
			"seed": 71644,
			"groupIds": [
				"7pTxY_ukorL-ve6TqCuFL"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "QMmSiJLRmqeG1feP4YA-r",
					"type": "arrow"
				}
			],
			"updated": 1692192358618,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "34a27741a5e7174bfade884abb1246971002a3e3",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "arrow",
			"version": 239,
			"versionNonce": 703405528,
			"isDeleted": false,
			"id": "QMmSiJLRmqeG1feP4YA-r",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1072.0011778937446,
			"y": 296.1577116412881,
			"strokeColor": "#e03131",
			"backgroundColor": "#ffffff",
			"width": 19.085025821972067,
			"height": 60.44443766276038,
			"seed": 1951341906,
			"groupIds": [
				"7pTxY_ukorL-ve6TqCuFL"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358618,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "MhAath92",
				"focus": -0.4612834804267647,
				"gap": 13.333333333333371
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-19.085025821972067,
					60.44443766276038
				]
			]
		},
		{
			"type": "text",
			"version": 65,
			"versionNonce": 224283560,
			"isDeleted": false,
			"id": "MhAath92",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1138.4456087748208,
			"y": 369.9354826373818,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 152.29998779296875,
			"height": 25,
			"seed": 1264102030,
			"groupIds": [
				"7pTxY_ukorL-ve6TqCuFL"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "QMmSiJLRmqeG1feP4YA-r",
					"type": "arrow"
				}
			],
			"updated": 1692192358618,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "A的周转时间为10",
			"rawText": "A的周转时间为10",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "A的周转时间为10",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "text",
			"version": 130,
			"versionNonce": 926655192,
			"isDeleted": false,
			"id": "9z061qqw",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1141.778942108154,
			"y": 399.04660731186095,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 162.53997802734375,
			"height": 25,
			"seed": 1082093902,
			"groupIds": [
				"7pTxY_ukorL-ve6TqCuFL"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358618,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "B的周转时间是20",
			"rawText": "B的周转时间是20",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "B的周转时间是20",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "text",
			"version": 122,
			"versionNonce": 635868840,
			"isDeleted": false,
			"id": "f4iyWtOc",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1144.223332299126,
			"y": 426.15774554970824,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 160.25997924804688,
			"height": 25,
			"seed": 47923918,
			"groupIds": [
				"7pTxY_ukorL-ve6TqCuFL"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "ZhUUVWDzyTDL5qncKaPf3",
					"type": "arrow"
				}
			],
			"updated": 1692192358618,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "C的周转时间是30",
			"rawText": "C的周转时间是30",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "C的周转时间是30",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "text",
			"version": 80,
			"versionNonce": 40994776,
			"isDeleted": false,
			"id": "mG0oQvM6",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1108.2233729892305,
			"y": 483.93545551064574,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 207.99998474121094,
			"height": 25,
			"seed": 1386714062,
			"groupIds": [
				"7pTxY_ukorL-ve6TqCuFL"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "ZhUUVWDzyTDL5qncKaPf3",
					"type": "arrow"
				}
			],
			"updated": 1692192358618,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "所以平均周转时间为20",
			"rawText": "所以平均周转时间为20",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "所以平均周转时间为20",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 91,
			"versionNonce": 1026392488,
			"isDeleted": false,
			"id": "ZhUUVWDzyTDL5qncKaPf3",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1034.6196419522616,
			"y": 453.4910517563054,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 11.782072831210598,
			"height": 25.77779134114587,
			"seed": 205153106,
			"groupIds": [
				"7pTxY_ukorL-ve6TqCuFL"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358618,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "f4iyWtOc",
				"focus": -0.2643648672766667,
				"gap": 2.3333062065971717
			},
			"endBinding": {
				"elementId": "mG0oQvM6",
				"focus": -0.09814642711471155,
				"gap": 4.666612413194457
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					11.782072831210598,
					25.77779134114587
				]
			]
		},
		{
			"type": "arrow",
			"version": 85,
			"versionNonce": 396545240,
			"isDeleted": false,
			"id": "EkoGf5pEinMC-C2ae6kip",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -654.2234001159666,
			"y": 314.8243647445868,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 11.450172984496248,
			"height": 91.55554877387152,
			"seed": 129205454,
			"groupIds": [
				"7pTxY_ukorL-ve6TqCuFL"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358619,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "TQvfup9D",
				"focus": -0.4224189395613407,
				"gap": 13.3333333333332
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-11.450172984496248,
					91.55554877387152
				]
			]
		},
		{
			"type": "text",
			"version": 87,
			"versionNonce": 1113525416,
			"isDeleted": false,
			"id": "TQvfup9D",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -715.778914981418,
			"y": 419.7132468517915,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 164.59999084472656,
			"height": 25,
			"seed": 1447354578,
			"groupIds": [
				"7pTxY_ukorL-ve6TqCuFL"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "EkoGf5pEinMC-C2ae6kip",
					"type": "arrow"
				}
			],
			"updated": 1692192358619,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "平均周转时间为110",
			"rawText": "平均周转时间为110",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "平均周转时间为110",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "image",
			"version": 116,
			"versionNonce": 1617129944,
			"isDeleted": false,
			"id": "Imt0J5rF",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1191.3345383538137,
			"y": 600.1311007907466,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 400.4444715711806,
			"height": 177.66198386608718,
			"seed": 75784,
			"groupIds": [
				"dZpyBogxGOJOk9jP9dzyo"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358619,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "f1e77ce44f535f26f301777d20799984f279d22f",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "arrow",
			"version": 101,
			"versionNonce": 1596405672,
			"isDeleted": false,
			"id": "hvfx8Fk_kPIEyig2p0Bpz",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1072.0011439853242,
			"y": 758.15769807792,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 7.611220850104246,
			"height": 66.6667005750869,
			"seed": 1503277266,
			"groupIds": [
				"dZpyBogxGOJOk9jP9dzyo"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358619,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "KAdgCxNx",
				"focus": -0.4734177642391372,
				"gap": 14.222208658854242
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-7.611220850104246,
					66.6667005750869
				]
			]
		},
		{
			"type": "text",
			"version": 61,
			"versionNonce": 1942451928,
			"isDeleted": false,
			"id": "KAdgCxNx",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1136.667858123779,
			"y": 839.0466073118612,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 207.679931640625,
			"height": 25,
			"seed": 1908322450,
			"groupIds": [
				"dZpyBogxGOJOk9jP9dzyo"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "hvfx8Fk_kPIEyig2p0Bpz",
					"type": "arrow"
				}
			],
			"updated": 1692192358619,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "（10+20+120）/3=50",
			"rawText": "（10+20+120）/3=50",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "（10+20+120）/3=50",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "image",
			"version": 124,
			"versionNonce": 665977512,
			"isDeleted": false,
			"id": "T6ZvE4VN",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -694.4456359015569,
			"y": 687.8388538302652,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 500,
			"height": 227.74869109947645,
			"seed": 27670,
			"groupIds": [
				"ZxKwdC7wNzpD-Vvo4YX-0"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358619,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "1a626a2966d1506daa8a8d49aa7343f7a83dcd39",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "arrow",
			"version": 87,
			"versionNonce": 1717754840,
			"isDeleted": false,
			"id": "v0fG15qAq4l4dYQgKEzwO",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -553.3344569736054,
			"y": 896.1577116412881,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 40,
			"height": 67.55557590060766,
			"seed": 1680691666,
			"groupIds": [
				"ZxKwdC7wNzpD-Vvo4YX-0"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358619,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "sY7Rd6ze",
				"focus": -0.5959504580143908,
				"gap": 8.888821072048586
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-40,
					67.55557590060766
				]
			]
		},
		{
			"type": "text",
			"version": 77,
			"versionNonce": 1252748712,
			"isDeleted": false,
			"id": "sY7Rd6ze",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -646.8900939093693,
			"y": 972.6021086139443,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 224.2399444580078,
			"height": 25,
			"seed": 929459666,
			"groupIds": [
				"ZxKwdC7wNzpD-Vvo4YX-0"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "v0fG15qAq4l4dYQgKEzwO",
					"type": "arrow"
				}
			],
			"updated": 1692192358619,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "（100+100+110）/3=103",
			"rawText": "（100+100+110）/3=103",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "（100+100+110）/3=103",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "image",
			"version": 52,
			"versionNonce": 441032920,
			"isDeleted": false,
			"id": "P7lQVDnC",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -947.3344976637096,
			"y": 1058.0124396227252,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 500,
			"height": 237.17948717948718,
			"seed": 78394,
			"groupIds": [
				"busAsaLR62mCdgfszcjuM"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358619,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "52985c51d47488539f08e5dc22967bce6a89f137",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "arrow",
			"version": 131,
			"versionNonce": 1094678696,
			"isDeleted": false,
			"id": "i7XFL2He6_ClHzDhZcz5M",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -799.5567198859318,
			"y": 1274.6021628674166,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 33.77777099609375,
			"height": 77.33330620659717,
			"seed": 293973390,
			"groupIds": [
				"busAsaLR62mCdgfszcjuM"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358619,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "OOuJVjKR",
				"focus": -0.27246119990990975,
				"gap": 8.222181532118157
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-33.77777099609375,
					77.33330620659717
				]
			]
		},
		{
			"type": "text",
			"version": 66,
			"versionNonce": 252691928,
			"isDeleted": false,
			"id": "OOuJVjKR",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -916.4455884297686,
			"y": 1360.157650606132,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 207.679931640625,
			"height": 25,
			"seed": 1719186446,
			"groupIds": [
				"busAsaLR62mCdgfszcjuM"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "i7XFL2He6_ClHzDhZcz5M",
					"type": "arrow"
				}
			],
			"updated": 1692192358619,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "（120+10+20）/3=50",
			"rawText": "（120+10+20）/3=50",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "（120+10+20）/3=50",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "image",
			"version": 71,
			"versionNonce": 2132419496,
			"isDeleted": false,
			"id": "festMAZT",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -980.2234272427027,
			"y": 1468.0865918366492,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 828.8888888888889,
			"height": 203.43487090223383,
			"seed": 85173,
			"groupIds": [
				"yp-5EW-eq_3YSbgusgF34"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "ULyL0IfBfJyTyjXSpg6KJ",
					"type": "arrow"
				}
			],
			"updated": 1692192358619,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "f9dabb7062e80ba2721ef40b5407083d16a0f3a8",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "arrow",
			"version": 53,
			"versionNonce": 835275480,
			"isDeleted": false,
			"id": "MpH-LxBDwIT2m2Z70tRmc",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -874.2233662075464,
			"y": 1663.6665028453726,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 17.777777777777715,
			"height": 64.88888210720484,
			"seed": 1265462606,
			"groupIds": [
				"yp-5EW-eq_3YSbgusgF34"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358619,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "RziUoLz1",
				"focus": -0.514642426306259,
				"gap": 8.444485134548586
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-17.777777777777715,
					64.88888210720484
				]
			]
		},
		{
			"type": "text",
			"version": 110,
			"versionNonce": 577203880,
			"isDeleted": false,
			"id": "RziUoLz1",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -968.4456087748207,
			"y": 1736.999870087126,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 298.61993408203125,
			"height": 25,
			"seed": 912762958,
			"groupIds": [
				"yp-5EW-eq_3YSbgusgF34"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "MpH-LxBDwIT2m2Z70tRmc",
					"type": "arrow"
				}
			],
			"updated": 1692192358619,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "平均响应时间：（0+5+10）/3=5",
			"rawText": "平均响应时间：（0+5+10）/3=5",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "平均响应时间：（0+5+10）/3=5",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "text",
			"version": 110,
			"versionNonce": 755642328,
			"isDeleted": false,
			"id": "cfsaKuZR",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -489.33448410034157,
			"y": 1722.5553917342615,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 279.79998779296875,
			"height": 25,
			"seed": 202813390,
			"groupIds": [
				"yp-5EW-eq_3YSbgusgF34"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "ULyL0IfBfJyTyjXSpg6KJ",
					"type": "arrow"
				}
			],
			"updated": 1692192358619,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "平均响应时间：（0+1+2）/3=1",
			"rawText": "平均响应时间：（0+1+2）/3=1",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "平均响应时间：（0+1+2）/3=1",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 56,
			"versionNonce": 601053608,
			"isDeleted": false,
			"id": "ULyL0IfBfJyTyjXSpg6KJ",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -341.77894210815407,
			"y": 1674.3331762937232,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 8.8888888888888,
			"height": 43.55553521050365,
			"seed": 490510158,
			"groupIds": [
				"yp-5EW-eq_3YSbgusgF34"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358619,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "festMAZT",
				"focus": -0.5637196102351656,
				"gap": 2.811713554840253
			},
			"endBinding": {
				"elementId": "cfsaKuZR",
				"focus": -0.03325175704591671,
				"gap": 4.666680230034672
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-8.8888888888888,
					43.55553521050365
				]
			]
		},
		{
			"type": "arrow",
			"version": 72,
			"versionNonce": 954627288,
			"isDeleted": false,
			"id": "VpDTWua-DNfD0vaAhChIZ",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -513.029620365645,
			"y": 1579.7003076443136,
			"strokeColor": "#e03131",
			"backgroundColor": "#ffffff",
			"width": 68.21057771381572,
			"height": 230.7368549547698,
			"seed": 1982673424,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358619,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "YVP4Jram",
				"focus": -0.184372259509609,
				"gap": 4.631604646381447
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-68.21057771381572,
					230.7368549547698
				]
			]
		},
		{
			"type": "text",
			"version": 85,
			"versionNonce": 109700264,
			"isDeleted": false,
			"id": "YVP4Jram",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -661.2401980794607,
			"y": 1815.0687672454649,
			"strokeColor": "#e03131",
			"backgroundColor": "#ffffff",
			"width": 185.4199981689453,
			"height": 25,
			"seed": 1438646800,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "VpDTWua-DNfD0vaAhChIZ",
					"type": "arrow"
				}
			],
			"updated": 1692192358619,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "这里的时间片长度为1",
			"rawText": "这里的时间片长度为1",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "这里的时间片长度为1",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "image",
			"version": 106,
			"versionNonce": 1794251224,
			"isDeleted": false,
			"id": "B6QGS9l6",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -99.32586928129979,
			"y": 707.2192505999724,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 477,
			"height": 273,
			"seed": 8435,
			"groupIds": [
				"koRIDrUDIp2h3I2euIkzh",
				"ADvieBq_bqEaKdy2T8B_2"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358620,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "3f4086b97cd8da9c677349ec9664ec1c968ce1c1",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "arrow",
			"version": 247,
			"versionNonce": 137826216,
			"isDeleted": false,
			"id": "NF0J9BBcIifBn-nVULlQ5",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 13.296266776092523,
			"y": 847.9465013919466,
			"strokeColor": "#e03131",
			"backgroundColor": "#ffffff",
			"width": 47.543305675321534,
			"height": 148.34939918172336,
			"seed": 1179353232,
			"groupIds": [
				"koRIDrUDIp2h3I2euIkzh",
				"ADvieBq_bqEaKdy2T8B_2"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358620,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "DmyZqJbE",
				"focus": 0.05662344590103729,
				"gap": 4.359013520287135
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-47.543305675321534,
					148.34939918172336
				]
			]
		},
		{
			"type": "text",
			"version": 219,
			"versionNonce": 1891704299,
			"isDeleted": false,
			"id": "DmyZqJbE",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -160.59195815813865,
			"y": 1000.6549140939571,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 225.73599243164062,
			"height": 33.6,
			"seed": 656742512,
			"groupIds": [
				"koRIDrUDIp2h3I2euIkzh",
				"ADvieBq_bqEaKdy2T8B_2"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "NF0J9BBcIifBn-nVULlQ5",
					"type": "arrow"
				}
			],
			"updated": 1693060909681,
			"link": null,
			"locked": false,
			"fontSize": 28,
			"fontFamily": 4,
			"text": "IO操作占用的时间",
			"rawText": "IO操作占用的时间",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "IO操作占用的时间",
			"lineHeight": 1.2,
			"baseline": 24
		},
		{
			"type": "image",
			"version": 141,
			"versionNonce": 1359403688,
			"isDeleted": false,
			"id": "G84ILDmh",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 451.8942127667408,
			"y": 675.5903897933418,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 462,
			"height": 276,
			"seed": 8882,
			"groupIds": [
				"L7eyDsENygUyB1dhmWiJP",
				"ADvieBq_bqEaKdy2T8B_2"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "Uo8LciEJZ7efCSXYPKoPi",
					"type": "arrow"
				}
			],
			"updated": 1692192358620,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "accac7ae132ac6ff81539bef638aab7fb894549f",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "arrow",
			"version": 220,
			"versionNonce": 1265075160,
			"isDeleted": false,
			"id": "Uo8LciEJZ7efCSXYPKoPi",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 577.4862543590864,
			"y": 876.1391322486627,
			"strokeColor": "#e03131",
			"backgroundColor": "#ffffff",
			"width": 17.544181115329707,
			"height": 99.92543818175034,
			"seed": 103429232,
			"groupIds": [
				"L7eyDsENygUyB1dhmWiJP",
				"ADvieBq_bqEaKdy2T8B_2"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358620,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "rgOvQoGA",
				"focus": -0.5537977664641012,
				"gap": 13.572048148360238
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-17.544181115329707,
					99.92543818175034
				]
			]
		},
		{
			"type": "text",
			"version": 375,
			"versionNonce": 1306020421,
			"isDeleted": false,
			"id": "rgOvQoGA",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 451.7980092473035,
			"y": 989.6366185787732,
			"strokeColor": "#e03131",
			"backgroundColor": "#ffffff",
			"width": 462.251953125,
			"height": 67.2,
			"seed": 1426357392,
			"groupIds": [
				"L7eyDsENygUyB1dhmWiJP",
				"ADvieBq_bqEaKdy2T8B_2"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "Uo8LciEJZ7efCSXYPKoPi",
					"type": "arrow"
				}
			],
			"updated": 1693060909686,
			"link": null,
			"locked": false,
			"fontSize": 28,
			"fontFamily": 4,
			"text": "采用STCF，把A分解成了5个子任务。\n当A完成时，则会调用B【重叠】",
			"rawText": "采用STCF，把A分解成了5个子任务。\n当A完成时，则会调用B【重叠】",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "采用STCF，把A分解成了5个子任务。\n当A完成时，则会调用B【重叠】",
			"lineHeight": 1.2,
			"baseline": 58
		},
		{
			"type": "image",
			"version": 255,
			"versionNonce": 1215908056,
			"isDeleted": false,
			"id": "8sJzfdun",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 164.8465994948752,
			"y": 1148.8593742131457,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 378,
			"height": 429,
			"seed": 23647,
			"groupIds": [
				"DKKDrgeeXRo68jorwS_Jb"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "BQKtLwGyrSGsRHgvP8WFV",
					"type": "arrow"
				}
			],
			"updated": 1692192358620,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "fd470d5e48d8b3277ccf52859b79ed014318ff0e",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "line",
			"version": 290,
			"versionNonce": 222187688,
			"isDeleted": false,
			"id": "_yNwD2oTnlBuNOfkZ17-y",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 375.70545473034775,
			"y": 1198.1657120251718,
			"strokeColor": "#e03131",
			"backgroundColor": "#ffffff",
			"width": 161.86669921874983,
			"height": 2.7333246866860463,
			"seed": 1367334376,
			"groupIds": [
				"DKKDrgeeXRo68jorwS_Jb"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358620,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": null,
			"points": [
				[
					0,
					0
				],
				[
					161.86669921874983,
					2.7333246866860463
				]
			]
		},
		{
			"type": "arrow",
			"version": 564,
			"versionNonce": 688549336,
			"isDeleted": false,
			"id": "BQKtLwGyrSGsRHgvP8WFV",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 549.5053916606862,
			"y": 1187.1657043957773,
			"strokeColor": "#e03131",
			"backgroundColor": "#ffffff",
			"width": 64.00001525878906,
			"height": 0.9999847412109375,
			"seed": 211542248,
			"groupIds": [
				"DKKDrgeeXRo68jorwS_Jb"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358620,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "Ip-o-Hv9E3J-xXrz6Z60a",
				"focus": 0.21484217681100773,
				"gap": 2.639854330166827
			},
			"endBinding": {
				"elementId": "OwaWQP2e",
				"focus": 0.07978386384745711,
				"gap": 4.7499847412109375
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					64.00001525878906,
					-0.9999847412109375
				]
			]
		},
		{
			"type": "text",
			"version": 386,
			"versionNonce": 1381771403,
			"isDeleted": false,
			"id": "OwaWQP2e",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 618.2553916606862,
			"y": 1151.1656815075937,
			"strokeColor": "#e03131",
			"backgroundColor": "#ffffff",
			"width": 557.3119506835938,
			"height": 67.2,
			"seed": 725582824,
			"groupIds": [
				"DKKDrgeeXRo68jorwS_Jb"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "BQKtLwGyrSGsRHgvP8WFV",
					"type": "arrow"
				}
			],
			"updated": 1693060909689,
			"link": null,
			"locked": false,
			"fontSize": 28,
			"fontFamily": 4,
			"text": "如果A的优先级 > B的优先级，运行A\n如果A的优先级 = B的优先级，轮转运行A和B",
			"rawText": "如果A的优先级 > B的优先级，运行A\n如果A的优先级 = B的优先级，轮转运行A和B",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "如果A的优先级 > B的优先级，运行A\n如果A的优先级 = B的优先级，轮转运行A和B",
			"lineHeight": 1.2,
			"baseline": 58
		},
		{
			"type": "rectangle",
			"version": 155,
			"versionNonce": 103740120,
			"isDeleted": false,
			"id": "Ip-o-Hv9E3J-xXrz6Z60a",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 276.9988788018736,
			"y": 1146.0998530920751,
			"strokeColor": "#1971c2",
			"backgroundColor": "#ffffff",
			"width": 269.86665852864576,
			"height": 70.40000406901049,
			"seed": 1496526370,
			"groupIds": [
				"DKKDrgeeXRo68jorwS_Jb"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [
				{
					"id": "BQKtLwGyrSGsRHgvP8WFV",
					"type": "arrow"
				}
			],
			"updated": 1692192358620,
			"link": null,
			"locked": false
		},
		{
			"type": "arrow",
			"version": 253,
			"versionNonce": 1854949032,
			"isDeleted": false,
			"id": "drQviaWS0sIKKQ4coNZH4",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 542.598854387811,
			"y": 1214.3665156897314,
			"strokeColor": "#1971c2",
			"backgroundColor": "#ffffff",
			"width": 83.20003255208337,
			"height": 51.19999186197924,
			"seed": 154116862,
			"groupIds": [
				"DKKDrgeeXRo68jorwS_Jb"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358620,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "fW50daGl",
				"focus": -0.7624163741169672,
				"gap": 2.1333007812498863
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					83.20003255208337,
					51.19999186197924
				]
			]
		},
		{
			"type": "text",
			"version": 277,
			"versionNonce": 792770981,
			"isDeleted": false,
			"id": "fW50daGl",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 627.9321877211443,
			"y": 1261.8331904944191,
			"strokeColor": "#1971c2",
			"backgroundColor": "#ffffff",
			"width": 336,
			"height": 33.6,
			"seed": 250814626,
			"groupIds": [
				"DKKDrgeeXRo68jorwS_Jb"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "drQviaWS0sIKKQ4coNZH4",
					"type": "arrow"
				}
			],
			"updated": 1693060909691,
			"link": null,
			"locked": false,
			"fontSize": 28,
			"fontFamily": 4,
			"text": "一个队列中可以有多个工作",
			"rawText": "一个队列中可以有多个工作",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "一个队列中可以有多个工作",
			"lineHeight": 1.2,
			"baseline": 24
		},
		{
			"type": "image",
			"version": 185,
			"versionNonce": 622932392,
			"isDeleted": false,
			"id": "QgKhxsbJ",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 411.83217144510274,
			"y": 1677.3332311845227,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 413,
			"height": 417,
			"seed": 68111,
			"groupIds": [
				"PN4rbExeWbxpvDbNeOYZc"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "XvTImYvHGM-NlXIXnYseG",
					"type": "arrow"
				}
			],
			"updated": 1692192358620,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "136b227d07f37bb6b34c272c4d9bf4ec4de206ac",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "arrow",
			"version": 153,
			"versionNonce": 503454936,
			"isDeleted": false,
			"id": "zCyViPL8UVv_2KZOMC0te",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 644.9989194919776,
			"y": 1713.033182356398,
			"strokeColor": "#1971c2",
			"backgroundColor": "#ffffff",
			"width": 90.66666666666663,
			"height": 35.199991861979015,
			"seed": 1163221758,
			"groupIds": [
				"PN4rbExeWbxpvDbNeOYZc"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358620,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "oety4ZOH",
				"focus": 0.4024150320642706,
				"gap": 8.799967447916629
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					90.66666666666663,
					-35.199991861979015
				]
			]
		},
		{
			"type": "text",
			"version": 147,
			"versionNonce": 1836900139,
			"isDeleted": false,
			"id": "oety4ZOH",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 744.4655536065609,
			"y": 1654.6331579423356,
			"strokeColor": "#1971c2",
			"backgroundColor": "#ffffff",
			"width": 84,
			"height": 33.6,
			"seed": 1785198014,
			"groupIds": [
				"PN4rbExeWbxpvDbNeOYZc"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "zCyViPL8UVv_2KZOMC0te",
					"type": "arrow"
				}
			],
			"updated": 1693060909692,
			"link": null,
			"locked": false,
			"fontSize": 28,
			"fontFamily": 4,
			"text": "短工作",
			"rawText": "短工作",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "短工作",
			"lineHeight": 1.2,
			"baseline": 24
		},
		{
			"type": "arrow",
			"version": 158,
			"versionNonce": 2119746008,
			"isDeleted": false,
			"id": "XvTImYvHGM-NlXIXnYseG",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 733.532203997186,
			"y": 1974.3665156897312,
			"strokeColor": "#1971c2",
			"backgroundColor": "#ffffff",
			"width": 94.93334960937489,
			"height": 52.26668294270826,
			"seed": 564941538,
			"groupIds": [
				"PN4rbExeWbxpvDbNeOYZc"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358620,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "QgKhxsbJ",
				"focus": -0.47163954797315727,
				"gap": 3.633382161458144
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					94.93334960937489,
					-52.26668294270826
				]
			]
		},
		{
			"type": "text",
			"version": 185,
			"versionNonce": 1554267397,
			"isDeleted": false,
			"id": "mMYjQ05I",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 834.0655698826027,
			"y": 1899.6998490230646,
			"strokeColor": "#1971c2",
			"backgroundColor": "#ffffff",
			"width": 249.3679962158203,
			"height": 33.6,
			"seed": 1607688126,
			"groupIds": [
				"PN4rbExeWbxpvDbNeOYZc"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1693060909693,
			"link": null,
			"locked": false,
			"fontSize": 28,
			"fontFamily": 4,
			"text": "长工作【优先级低】",
			"rawText": "长工作【优先级低】",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "长工作【优先级低】",
			"lineHeight": 1.2,
			"baseline": 24
		},
		{
			"type": "image",
			"version": 63,
			"versionNonce": 1184024280,
			"isDeleted": false,
			"id": "tt8Dp40J",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1077.6189593287068,
			"y": 1882.2501103796012,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 430,
			"height": 374,
			"seed": 72626,
			"groupIds": [
				"rvh5arxWSfuiTztOfjjqi"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "lFP2EfMBEYOpCN5gK0gZy",
					"type": "arrow"
				},
				{
					"id": "HFU5Wecy6Yz0yDpLIN4HZ",
					"type": "arrow"
				},
				{
					"id": "KHSUcU3ckg8MbXzXRB8fd",
					"type": "arrow"
				}
			],
			"updated": 1692192358621,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "a1b9705d0b40a5f5f3f5724db67ef20f7b9e86f8",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "arrow",
			"version": 115,
			"versionNonce": 906212008,
			"isDeleted": false,
			"id": "lFP2EfMBEYOpCN5gK0gZy",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -700.273293955039,
			"y": 1930.6828611728697,
			"strokeColor": "#1971c2",
			"backgroundColor": "#ffffff",
			"width": 68.8139677617279,
			"height": 2.372890237829324,
			"seed": 797276553,
			"groupIds": [
				"rvh5arxWSfuiTztOfjjqi"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358621,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "0SuYh6wv",
				"focus": 0.3572652290428218,
				"gap": 6.327747531459522
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					68.8139677617279,
					2.372890237829324
				]
			]
		},
		{
			"type": "text",
			"version": 171,
			"versionNonce": 1552794059,
			"isDeleted": false,
			"id": "0SuYh6wv",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -625.1315786618516,
			"y": 1918.2251195351596,
			"strokeColor": "#1971c2",
			"backgroundColor": "#ffffff",
			"width": 279.7760009765625,
			"height": 67.2,
			"seed": 1226622857,
			"groupIds": [
				"rvh5arxWSfuiTztOfjjqi"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "lFP2EfMBEYOpCN5gK0gZy",
					"type": "arrow"
				}
			],
			"updated": 1693060909696,
			"link": null,
			"locked": false,
			"fontSize": 28,
			"fontFamily": 4,
			"text": "每次都在时间片以内，\n始终保持优先级队列",
			"rawText": "每次都在时间片以内，\n始终保持优先级队列",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "每次都在时间片以内，\n始终保持优先级队列",
			"lineHeight": 1.2,
			"baseline": 58
		},
		{
			"type": "arrow",
			"version": 110,
			"versionNonce": 54992296,
			"isDeleted": false,
			"id": "HFU5Wecy6Yz0yDpLIN4HZ",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1019.0323840213318,
			"y": 1937.010578531393,
			"strokeColor": "#1971c2",
			"backgroundColor": "#ffffff",
			"width": 83.84232288954013,
			"height": 11.864481362082188,
			"seed": 1819688775,
			"groupIds": [
				"rvh5arxWSfuiTztOfjjqi"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358621,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "MjJj6myH",
				"focus": 0.00721860100204296,
				"gap": 2.5714995972598444
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-83.84232288954013,
					11.864481362082188
				]
			]
		},
		{
			"type": "text",
			"version": 90,
			"versionNonce": 1300255845,
			"isDeleted": false,
			"id": "MjJj6myH",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1245.4462065081318,
			"y": 1942.1518356845336,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 140,
			"height": 33.6,
			"seed": 1599805961,
			"groupIds": [
				"rvh5arxWSfuiTztOfjjqi"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "HFU5Wecy6Yz0yDpLIN4HZ",
					"type": "arrow"
				}
			],
			"updated": 1693060909697,
			"link": null,
			"locked": false,
			"fontSize": 28,
			"fontFamily": 4,
			"text": "交互型工作",
			"rawText": "交互型工作",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "交互型工作",
			"lineHeight": 1.2,
			"baseline": 24
		},
		{
			"type": "arrow",
			"version": 110,
			"versionNonce": 1256532136,
			"isDeleted": false,
			"id": "KHSUcU3ckg8MbXzXRB8fd",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1013.4955898448364,
			"y": 2202.7749489728612,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 71.18688817249347,
			"height": 24.519916079128507,
			"seed": 1227979817,
			"groupIds": [
				"rvh5arxWSfuiTztOfjjqi"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358621,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "MYUE1qIw",
				"focus": 0.6367106562420293,
				"gap": 1.5828531629592817
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-71.18688817249347,
					24.519916079128507
				]
			]
		},
		{
			"type": "text",
			"version": 89,
			"versionNonce": 145313899,
			"isDeleted": false,
			"id": "MYUE1qIw",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1226.2653311802892,
			"y": 2209.102636158448,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 140,
			"height": 33.6,
			"seed": 1547964295,
			"groupIds": [
				"rvh5arxWSfuiTztOfjjqi"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "KHSUcU3ckg8MbXzXRB8fd",
					"type": "arrow"
				}
			],
			"updated": 1693060909699,
			"link": null,
			"locked": false,
			"fontSize": 28,
			"fontFamily": 4,
			"text": "密集型工作",
			"rawText": "密集型工作",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "密集型工作",
			"lineHeight": 1.2,
			"baseline": 24
		},
		{
			"type": "image",
			"version": 79,
			"versionNonce": 680121256,
			"isDeleted": false,
			"id": "2Sty2oba",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 456.99805609799176,
			"y": -209.54270950737015,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 605.8669183609074,
			"height": 329.43504040081643,
			"seed": 30166,
			"groupIds": [
				"ZxQ4fz4o_7ME7bBkpMpXQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "UCLQfaXiVNX61KpFMDmGo",
					"type": "arrow"
				},
				{
					"id": "68cdwPZwSAlKCzCUMsA5J",
					"type": "arrow"
				}
			],
			"updated": 1692192358621,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "3ad3865931a4221b5e2d986391f8c4b039ec3f3b",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "arrow",
			"version": 186,
			"versionNonce": 1550621400,
			"isDeleted": false,
			"id": "UCLQfaXiVNX61KpFMDmGo",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 867.0122232735557,
			"y": 56.558031124515935,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 33.66577644979748,
			"height": 85.69467980976725,
			"seed": 2049064281,
			"groupIds": [
				"ZxQ4fz4o_7ME7bBkpMpXQ"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358621,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "v9YaSvNj",
				"focus": -0.5915901689777846,
				"gap": 3.825655088048336
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-27.544763333838546,
					11.47696526414478
				],
				[
					-15.302620352193003,
					41.317057438461916
				],
				[
					-33.66577644979748,
					85.69467980976725
				]
			]
		},
		{
			"type": "text",
			"version": 218,
			"versionNonce": 765624261,
			"isDeleted": false,
			"id": "v9YaSvNj",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 745.3563797986485,
			"y": 146.07836602233152,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 395.33197021484375,
			"height": 67.2,
			"seed": 137314295,
			"groupIds": [
				"ZxQ4fz4o_7ME7bBkpMpXQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "UCLQfaXiVNX61KpFMDmGo",
					"type": "arrow"
				}
			],
			"updated": 1693060909701,
			"link": null,
			"locked": false,
			"fontSize": 28,
			"fontFamily": 4,
			"text": "定期提升优先级，\n保证了Q2上的长任务有机会执行",
			"rawText": "定期提升优先级，\n保证了Q2上的长任务有机会执行",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "定期提升优先级，\n保证了Q2上的长任务有机会执行",
			"lineHeight": 1.2,
			"baseline": 58
		},
		{
			"type": "arrow",
			"version": 48,
			"versionNonce": 1187217368,
			"isDeleted": false,
			"id": "68cdwPZwSAlKCzCUMsA5J",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 625.2833125847264,
			"y": 52.35247784612875,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 11.996289469937892,
			"height": 91.97136616452929,
			"seed": 2079167127,
			"groupIds": [
				"ZxQ4fz4o_7ME7bBkpMpXQ"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358621,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "DLDzDS37",
				"focus": 0.5440075710678751,
				"gap": 3.498871152483275
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-11.996289469937892,
					91.97136616452929
				]
			]
		},
		{
			"type": "text",
			"version": 228,
			"versionNonce": 1402604299,
			"isDeleted": false,
			"id": "DLDzDS37",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 270.56030913813566,
			"y": 147.8227151631413,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 434.58795166015625,
			"height": 67.2,
			"seed": 1215716121,
			"groupIds": [
				"ZxQ4fz4o_7ME7bBkpMpXQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "68cdwPZwSAlKCzCUMsA5J",
					"type": "arrow"
				}
			],
			"updated": 1693060909703,
			"link": null,
			"locked": false,
			"fontSize": 28,
			"fontFamily": 4,
			"text": "在此刻加入了 2 个交互型任务后，\n这个长任务就没有机会执行了",
			"rawText": "在此刻加入了 2 个交互型任务后，\n这个长任务就没有机会执行了",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "在此刻加入了 2 个交互型任务后，\n这个长任务就没有机会执行了",
			"lineHeight": 1.2,
			"baseline": 58
		},
		{
			"type": "rectangle",
			"version": 158,
			"versionNonce": 1861600472,
			"isDeleted": false,
			"id": "vD7MVGtzi84ME7YBQs0Ct",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 300.4063676673774,
			"y": -88.89528839718062,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 158,
			"height": 78,
			"seed": 1486835065,
			"groupIds": [
				"ZxQ4fz4o_7ME7bBkpMpXQ"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [
				{
					"type": "text",
					"id": "KB8FqAPF"
				}
			],
			"updated": 1692192358621,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 167,
			"versionNonce": 2010617000,
			"isDeleted": false,
			"id": "KB8FqAPF",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 309.4063676673774,
			"y": -83.49528839718062,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 140,
			"height": 67.2,
			"seed": 1085862201,
			"groupIds": [
				"ZxQ4fz4o_7ME7bBkpMpXQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358621,
			"link": null,
			"locked": false,
			"fontSize": 28,
			"fontFamily": 4,
			"text": "一个颜色代\n表一个任务",
			"rawText": "一个颜色代表一个任务",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "vD7MVGtzi84ME7YBQs0Ct",
			"originalText": "一个颜色代表一个任务",
			"lineHeight": 1.2,
			"baseline": 62
		},
		{
			"type": "image",
			"version": 73,
			"versionNonce": 1117219288,
			"isDeleted": false,
			"id": "W1yV2Wft",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1073.9944609570368,
			"y": 2319.100963103452,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 500.00000000000006,
			"height": 268.2767624020888,
			"seed": 47510,
			"groupIds": [
				"KsLaYf-4tNOcK2O-Cg2MX"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "tx8refr6OLHRhaY4bsIpC",
					"type": "arrow"
				}
			],
			"updated": 1692192358621,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "55dd212aa228686f79648c6a9d4f0636e6110cdf",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "arrow",
			"version": 103,
			"versionNonce": 1682882472,
			"isDeleted": false,
			"id": "tx8refr6OLHRhaY4bsIpC",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1044.9827161130402,
			"y": 2345.4679016532295,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 46.92765690613987,
			"height": 22.29950209871413,
			"seed": 1595288953,
			"groupIds": [
				"KsLaYf-4tNOcK2O-Cg2MX"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358621,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "CwvZs3S9",
				"focus": 0.6110840624477063,
				"gap": 6.648941989006289
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-44.95953550273043,
					5.69910693681868
				],
				[
					-46.92765690613987,
					22.29950209871413
				]
			]
		},
		{
			"type": "text",
			"version": 329,
			"versionNonce": 1395146533,
			"isDeleted": false,
			"id": "CwvZs3S9",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1244.411399991797,
			"y": 2374.41634574095,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 179.79998779296875,
			"height": 72,
			"seed": 746275353,
			"groupIds": [
				"KsLaYf-4tNOcK2O-Cg2MX"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "tx8refr6OLHRhaY4bsIpC",
					"type": "arrow"
				}
			],
			"updated": 1693060909707,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "这个任务打擦边球，\n在高优先级一直占\n用CPU",
			"rawText": "这个任务打擦边球，\n在高优先级一直占\n用CPU",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "这个任务打擦边球，\n在高优先级一直占\n用CPU",
			"lineHeight": 1.2,
			"baseline": 66
		},
		{
			"type": "arrow",
			"version": 144,
			"versionNonce": 782797480,
			"isDeleted": false,
			"id": "H_HMzA2vlUp5BQ19sIHW7",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -776.4340950899812,
			"y": 2350.6095000932714,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 30.745189434606573,
			"height": 0.370997095522398,
			"seed": 1410573881,
			"groupIds": [
				"KsLaYf-4tNOcK2O-Cg2MX"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358622,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "rjfDbLvF",
				"focus": -0.13963710063362472,
				"gap": 6.673943227745667
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					30.745189434606573,
					0.370997095522398
				]
			]
		},
		{
			"type": "text",
			"version": 146,
			"versionNonce": 31093163,
			"isDeleted": false,
			"id": "rjfDbLvF",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -739.0149624276289,
			"y": 2338.630169845605,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 239.79998779296875,
			"height": 24,
			"seed": 3610009,
			"groupIds": [
				"KsLaYf-4tNOcK2O-Cg2MX"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "H_HMzA2vlUp5BQ19sIHW7",
					"type": "arrow"
				}
			],
			"updated": 1693060909710,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "时间份额用完，降低优先级",
			"rawText": "时间份额用完，降低优先级",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "时间份额用完，降低优先级",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 83,
			"versionNonce": 1100019112,
			"isDeleted": false,
			"id": "YymOt_zts0Dyf4-7P_E9V",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -766.2896932369043,
			"y": 2416.8150148757827,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 23.88230185025509,
			"height": 0.19465810012707152,
			"seed": 453699799,
			"groupIds": [
				"KsLaYf-4tNOcK2O-Cg2MX"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358622,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "MyfwWWIS",
				"focus": 0.28554310698328095,
				"gap": 2.7259872558100824
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					23.88230185025509,
					0.19465810012707152
				]
			]
		},
		{
			"type": "text",
			"version": 193,
			"versionNonce": 1954484869,
			"isDeleted": false,
			"id": "MyfwWWIS",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -739.6814041308392,
			"y": 2409.7147343249662,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 239.79998779296875,
			"height": 24,
			"seed": 358112119,
			"groupIds": [
				"KsLaYf-4tNOcK2O-Cg2MX"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "YymOt_zts0Dyf4-7P_E9V",
					"type": "arrow"
				}
			],
			"updated": 1693060909710,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "时间份额用完，降低优先级",
			"rawText": "时间份额用完，降低优先级",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "时间份额用完，降低优先级",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 89,
			"versionNonce": 1379139752,
			"isDeleted": false,
			"id": "F6-T95G2L_x9SvrvAzU-A",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -578.9187371179457,
			"y": 2498.837773071327,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 23.969294355531247,
			"height": 4.454539598729298,
			"seed": 1088290905,
			"groupIds": [
				"KsLaYf-4tNOcK2O-Cg2MX"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358622,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "dBmA5gCq",
				"focus": 0.6347914063710927,
				"gap": 2.536090279640007
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					23.969294355531247,
					-4.454539598729298
				]
			]
		},
		{
			"type": "text",
			"version": 151,
			"versionNonce": 1687487563,
			"isDeleted": false,
			"id": "dBmA5gCq",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -552.4133524827745,
			"y": 2478.699781426915,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 189.97998046875,
			"height": 48,
			"seed": 501637849,
			"groupIds": [
				"KsLaYf-4tNOcK2O-Cg2MX"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "F6-T95G2L_x9SvrvAzU-A",
					"type": "arrow"
				}
			],
			"updated": 1693060909712,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "2个任务优先级相同，\n轮转运行",
			"rawText": "2个任务优先级相同，\n轮转运行",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "2个任务优先级相同，\n轮转运行",
			"lineHeight": 1.2,
			"baseline": 42
		},
		{
			"type": "image",
			"version": 36,
			"versionNonce": 272477096,
			"isDeleted": false,
			"id": "t0nRXtI5",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -66.57366226997692,
			"y": 2212.0535954797697,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 500.00000000000006,
			"height": 154.12186379928318,
			"seed": 53087,
			"groupIds": [
				"gNLSnUJw6VdaBgp8i_MFn"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "ygOgeVxs17hufFZyzU4-E",
					"type": "arrow"
				}
			],
			"updated": 1692192358622,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "eb511ed232f8c7a646a78978586fd895a67788ff",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "arrow",
			"version": 205,
			"versionNonce": 1552040664,
			"isDeleted": false,
			"id": "ygOgeVxs17hufFZyzU4-E",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -62.31904972403197,
			"y": 2344.954072303387,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 21.534285045736397,
			"height": 43.06857009147279,
			"seed": 61840335,
			"groupIds": [
				"gNLSnUJw6VdaBgp8i_MFn"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358622,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "abM8uh58",
				"focus": -0.6245822465759139,
				"gap": 6.460269084365791
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-21.534285045736397,
					43.06857009147279
				]
			]
		},
		{
			"type": "text",
			"version": 120,
			"versionNonce": 509901285,
			"isDeleted": false,
			"id": "abM8uh58",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -136.61232217891873,
			"y": 2394.4829114792255,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 251.8599395751953,
			"height": 24,
			"seed": 1731254177,
			"groupIds": [
				"gNLSnUJw6VdaBgp8i_MFn"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "ygOgeVxs17hufFZyzU4-E",
					"type": "arrow"
				}
			],
			"updated": 1693060909714,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "B只占用了20%，而不是25%。",
			"rawText": "B只占用了20%，而不是25%。",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "B只占用了20%，而不是25%。",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "image",
			"version": 74,
			"versionNonce": 98838488,
			"isDeleted": false,
			"id": "uzk614lh",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -284.8157999516598,
			"y": 1816.791350090615,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 499.99999999999994,
			"height": 223.1467473524962,
			"seed": 87668,
			"groupIds": [
				"pMCjEYj0rE2Nft0lJGDh-",
				"BBAr4sHn5JCrjsh5oLmF-"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "MpJP-iT1GQH3zQcAaUWNF",
					"type": "arrow"
				},
				{
					"id": "PYAp-hnWaQt6mLBBO_v1T",
					"type": "arrow"
				}
			],
			"updated": 1692192358622,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "c7e0d943887f8fbf110d5e85eb4b4557709543ac",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "arrow",
			"version": 239,
			"versionNonce": 1471472040,
			"isDeleted": false,
			"id": "MpJP-iT1GQH3zQcAaUWNF",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -277.511879725653,
			"y": 1881.4113178655723,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 33.00093217561866,
			"height": 182.68378146384043,
			"seed": 1757552907,
			"groupIds": [
				"pMCjEYj0rE2Nft0lJGDh-",
				"BBAr4sHn5JCrjsh5oLmF-"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358622,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "uzk614lh",
				"focus": -1.0666677182963449,
				"gap": 24.157001886301487
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-12.9646599547456,
					1.178609537723787
				],
				[
					-33.00093217561866,
					132.5930671914973
				],
				[
					-19.446978692064818,
					182.68378146384043
				]
			]
		},
		{
			"type": "text",
			"version": 201,
			"versionNonce": 1134838507,
			"isDeleted": false,
			"id": "fCy4FSNu",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -298.1374679554414,
			"y": 2063.5057608403904,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 259.8399658203125,
			"height": 24,
			"seed": 724970821,
			"groupIds": [
				"pMCjEYj0rE2Nft0lJGDh-",
				"BBAr4sHn5JCrjsh5oLmF-"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1693060909716,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "大家行程值都相同，随机运行",
			"rawText": "大家行程值都相同，随机运行",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "大家行程值都相同，随机运行",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 166,
			"versionNonce": 1425697960,
			"isDeleted": false,
			"id": "PYAp-hnWaQt6mLBBO_v1T",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 91.98082782411424,
			"y": 1936.8057413375113,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 15.32185655008567,
			"height": 119.62840723675163,
			"seed": 1322651013,
			"groupIds": [
				"pMCjEYj0rE2Nft0lJGDh-",
				"BBAr4sHn5JCrjsh5oLmF-"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358622,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "WyPe77Xy",
				"focus": -0.5910959680082434,
				"gap": 4.861772773150278
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					12.375343945830195,
					5.893025208511062
				],
				[
					15.32185655008567,
					119.62840723675163
				]
			]
		},
		{
			"type": "text",
			"version": 129,
			"versionNonce": 1776678213,
			"isDeleted": false,
			"id": "WyPe77Xy",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 66.0515079146231,
			"y": 2061.2959213474132,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 204.79998779296875,
			"height": 24,
			"seed": 831299083,
			"groupIds": [
				"pMCjEYj0rE2Nft0lJGDh-",
				"BBAr4sHn5JCrjsh5oLmF-"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "PYAp-hnWaQt6mLBBO_v1T",
					"type": "arrow"
				}
			],
			"updated": 1693060909718,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "C的行程值最少，运行C",
			"rawText": "C的行程值最少，运行C",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "C的行程值最少，运行C",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "line",
			"version": 134,
			"versionNonce": 1196857256,
			"isDeleted": false,
			"id": "oux-7etVEiqGaAwDorWrA",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 164.17038662837373,
			"y": 1863.7322422400393,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 30.643758060385665,
			"height": 148.5042172703911,
			"seed": 1859625957,
			"groupIds": [
				"BBAr4sHn5JCrjsh5oLmF-"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358622,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": null,
			"points": [
				[
					0,
					0
				],
				[
					26.51861343829944,
					70.12698649321646
				],
				[
					-4.125144622086225,
					148.5042172703911
				]
			]
		},
		{
			"type": "rectangle",
			"version": 214,
			"versionNonce": 1891505880,
			"isDeleted": false,
			"id": "8wLv-IXTKOTpryf5tFyQi",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 195.55716840865625,
			"y": 1893.7866618114024,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 156,
			"height": 82,
			"seed": 884026027,
			"groupIds": [
				"BBAr4sHn5JCrjsh5oLmF-"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [
				{
					"type": "text",
					"id": "DlhrJSer"
				}
			],
			"updated": 1692192358622,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 304,
			"versionNonce": 1060990693,
			"isDeleted": false,
			"id": "DlhrJSer",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 203.55716840865625,
			"y": 1898.7866618114024,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 140,
			"height": 72,
			"seed": 417982981,
			"groupIds": [
				"BBAr4sHn5JCrjsh5oLmF-"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1693060909253,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "正好是票数比例\n：200：100：5\n0",
			"rawText": "正好是票数比例：200：100：50",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "8wLv-IXTKOTpryf5tFyQi",
			"originalText": "正好是票数比例：200：100：50",
			"lineHeight": 1.2,
			"baseline": 68
		},
		{
			"type": "image",
			"version": 173,
			"versionNonce": 1267039192,
			"isDeleted": false,
			"id": "jzxFcBcn",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -340.73421014987093,
			"y": 2625.197861359538,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 500,
			"height": 429.15980230642504,
			"seed": 53038,
			"groupIds": [
				"ja-PtKhzAYK7BmY5QDnTr",
				"dCsu5xxhZFmJ0UPdwwtvl"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "n2GRGWrwyGK3XFX4V9ySr",
					"type": "arrow"
				},
				{
					"id": "GcUALo2A0fQh8Co23VbYh",
					"type": "arrow"
				},
				{
					"id": "5hrbaGMM_Mo4pexqrRKv2",
					"type": "arrow"
				}
			],
			"updated": 1692192358622,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "889b093b5c1af4caca62a4472a7b861da309a87f",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "arrow",
			"version": 390,
			"versionNonce": 914541992,
			"isDeleted": false,
			"id": "4QQQa1vDOyi4lLx_lWYMS",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -39.21250887660062,
			"y": 2741.027739532127,
			"strokeColor": "#e03131",
			"backgroundColor": "#ffffff",
			"width": 103.90208501105131,
			"height": 37.020571396219566,
			"seed": 836226891,
			"groupIds": [
				"ja-PtKhzAYK7BmY5QDnTr",
				"dCsu5xxhZFmJ0UPdwwtvl"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358622,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "iJEbhNnt",
				"focus": 0.5021146156643282,
				"gap": 8.372334190477957
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-1.7173649290211301,
					34.34782268660456
				],
				[
					102.18472008203018,
					37.020571396219566
				]
			]
		},
		{
			"type": "line",
			"version": 278,
			"versionNonce": 35143896,
			"isDeleted": false,
			"id": "E8Mnkmrn_YTcpTzMXKxxq",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -50.37551194178354,
			"y": 2912.766852965149,
			"strokeColor": "#e03131",
			"backgroundColor": "#ffffff",
			"width": 84.15212627421738,
			"height": 133.9564953751028,
			"seed": 42800613,
			"groupIds": [
				"ja-PtKhzAYK7BmY5QDnTr",
				"dCsu5xxhZFmJ0UPdwwtvl"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358622,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": null,
			"points": [
				[
					0,
					0
				],
				[
					5.152160300336163,
					-121.93477708877299
				],
				[
					84.15212627421738,
					-133.9564953751028
				]
			]
		},
		{
			"type": "text",
			"version": 314,
			"versionNonce": 127053195,
			"isDeleted": false,
			"id": "iJEbhNnt",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 71.34454539590752,
			"y": 2768.2913172382914,
			"strokeColor": "#e03131",
			"backgroundColor": "#ffffff",
			"width": 179.77499389648438,
			"height": 54.010875521483285,
			"seed": 1067074469,
			"groupIds": [
				"ja-PtKhzAYK7BmY5QDnTr",
				"dCsu5xxhZFmJ0UPdwwtvl"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "4QQQa1vDOyi4lLx_lWYMS",
					"type": "arrow"
				}
			],
			"updated": 1693060909721,
			"link": null,
			"locked": false,
			"fontSize": 22.504531467284703,
			"fontFamily": 4,
			"text": "堆和栈都会增长，\n所以放在首尾",
			"rawText": "堆和栈都会增长，\n所以放在首尾",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "堆和栈都会增长，\n所以放在首尾",
			"lineHeight": 1.2,
			"baseline": 45
		},
		{
			"type": "arrow",
			"version": 367,
			"versionNonce": 1141532120,
			"isDeleted": false,
			"id": "n2GRGWrwyGK3XFX4V9ySr",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -260.3266174216169,
			"y": 2669.75601400875,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 111.63035821819187,
			"height": 56.673910708560925,
			"seed": 1002412389,
			"groupIds": [
				"dCsu5xxhZFmJ0UPdwwtvl"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358623,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "i4NuqFoW",
				"focus": 0.3949671547422544,
				"gap": 2.146722539594066
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-80.717396416175,
					4.293477835825797
				],
				[
					-111.63035821819187,
					56.673910708560925
				]
			]
		},
		{
			"type": "arrow",
			"version": 320,
			"versionNonce": 614040488,
			"isDeleted": false,
			"id": "GcUALo2A0fQh8Co23VbYh",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -254.31570914349754,
			"y": 2721.2777480386562,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 104.76089850210718,
			"height": 33.48914022209419,
			"seed": 922982053,
			"groupIds": [
				"dCsu5xxhZFmJ0UPdwwtvl"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358623,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "i4NuqFoW",
				"focus": 0.6557321870825134,
				"gap": 2.2239503954152156
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-42.934778358255585,
					-1.7173976856574882
				],
				[
					-79.85871395166441,
					-10.304353357308628
				],
				[
					-104.76089850210718,
					23.184786864785565
				]
			]
		},
		{
			"type": "arrow",
			"version": 322,
			"versionNonce": 779086552,
			"isDeleted": false,
			"id": "5hrbaGMM_Mo4pexqrRKv2",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -249.16354884316138,
			"y": 2973.7342251312175,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 105.61958096661783,
			"height": 205.22822089847978,
			"seed": 46213317,
			"groupIds": [
				"dCsu5xxhZFmJ0UPdwwtvl"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358623,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "i4NuqFoW",
				"focus": -0.8237169147289304,
				"gap": 6.517428231240729
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-3.4347953713149764,
					-51.52170127327054
				],
				[
					-42.934778358255585,
					-72.13040798788779
				],
				[
					-105.61958096661783,
					-205.22822089847978
				]
			]
		},
		{
			"type": "text",
			"version": 220,
			"versionNonce": 1918960805,
			"isDeleted": false,
			"id": "i4NuqFoW",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -475.00050921289494,
			"y": 2728.576647256905,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 113.699951171875,
			"height": 54.59477566655387,
			"seed": 1547722539,
			"groupIds": [
				"dCsu5xxhZFmJ0UPdwwtvl"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "n2GRGWrwyGK3XFX4V9ySr",
					"type": "arrow"
				},
				{
					"id": "GcUALo2A0fQh8Co23VbYh",
					"type": "arrow"
				},
				{
					"id": "5hrbaGMM_Mo4pexqrRKv2",
					"type": "arrow"
				}
			],
			"updated": 1693060909723,
			"link": null,
			"locked": false,
			"fontSize": 22.747823194397448,
			"fontFamily": 4,
			"text": "假设只有这\n三个部分",
			"rawText": "假设只有这\n三个部分",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "假设只有这\n三个部分",
			"lineHeight": 1.2,
			"baseline": 47
		},
		{
			"type": "image",
			"version": 60,
			"versionNonce": 467455960,
			"isDeleted": false,
			"id": "Dm3sIqfT",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1089.0277160802407,
			"y": 2639.9320207681676,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 499.99999999999994,
			"height": 120.17804154302671,
			"seed": 19802,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358623,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "27e14326786f518d58092c806822f8f3001069a2",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "image",
			"version": 56,
			"versionNonce": 955955624,
			"isDeleted": false,
			"id": "WQQCmjec",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1073.1222070767963,
			"y": 2809.389318954856,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 500.00000000000006,
			"height": 131.66666666666669,
			"seed": 81243,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358623,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "58059b01d99a02d27936ec69963f77216e1c6c6c",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "image",
			"version": 33,
			"versionNonce": 1952781528,
			"isDeleted": false,
			"id": "PR7398nF",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1239.4119854407088,
			"y": -403.3910338985555,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 176.04409913546695,
			"height": 547.5330756784728,
			"seed": 16444,
			"groupIds": [
				"MOmJl9XwRqZ0oXw8QZf_Q"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358623,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "9816f3eb4e7f0d7b970cd033c5a64ae595e925ce",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "text",
			"version": 157,
			"versionNonce": 597345323,
			"isDeleted": false,
			"id": "LWNZJvRj",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1223.03371487836,
			"y": 150.27246779223395,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 278.239990234375,
			"height": 48,
			"seed": 1477139344,
			"groupIds": [
				"MOmJl9XwRqZ0oXw8QZf_Q"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1693060909726,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "进程自己世界里的内存模样\n【以为整个物理内存都是它的】",
			"rawText": "进程自己世界里的内存模样\n【以为整个物理内存都是它的】",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "进程自己世界里的内存模样\n【以为整个物理内存都是它的】",
			"lineHeight": 1.2,
			"baseline": 42
		},
		{
			"type": "image",
			"version": 121,
			"versionNonce": 2107423192,
			"isDeleted": false,
			"id": "KRmcymtT",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 988.379988991145,
			"y": 275.2774068829366,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 293.48739048473306,
			"height": 332.26422187002163,
			"seed": 20335,
			"groupIds": [
				"YhNy9SwIQM7cK_4tSBiH_"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358623,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "d63bd18816e78c7a6c5c337825b92402518f4297",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "text",
			"version": 155,
			"versionNonce": 193144837,
			"isDeleted": false,
			"id": "FSIZyEcZ",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 983.5369029109597,
			"y": 608.2699209465359,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 260.0199890136719,
			"height": 24,
			"seed": 926719856,
			"groupIds": [
				"YhNy9SwIQM7cK_4tSBiH_"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1693060909727,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "进程实际在物理内存中的模样",
			"rawText": "进程实际在物理内存中的模样",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "进程实际在物理内存中的模样",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "image",
			"version": 54,
			"versionNonce": 714587864,
			"isDeleted": false,
			"id": "DtatQbpZ",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1432.9720005786796,
			"y": 266.34536979277846,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 437,
			"height": 127,
			"seed": 92705,
			"groupIds": [
				"ki5JpmeAR5ojDEjMEi7iv"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358623,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "9165f3ba06d92e72b786ca67fd61fc11cd5607c7",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "rectangle",
			"version": 81,
			"versionNonce": 988428968,
			"isDeleted": false,
			"id": "6Y6PgUpXxcHrbCvAhQEFU",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1432.7865471273503,
			"y": 263.3491959960601,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 444.0995553564294,
			"height": 137.7421239041322,
			"seed": 1676470808,
			"groupIds": [
				"ki5JpmeAR5ojDEjMEi7iv"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [],
			"updated": 1692192358623,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 108,
			"versionNonce": 1067910859,
			"isDeleted": false,
			"id": "f3mZCbHq",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1887.96875281963,
			"y": 272.05701857247743,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 114.27996826171875,
			"height": 34.291071280663395,
			"seed": 688964456,
			"groupIds": [
				"ki5JpmeAR5ojDEjMEi7iv"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1693060909730,
			"link": null,
			"locked": false,
			"fontSize": 28.575892733886164,
			"fontFamily": 4,
			"text": "段寄存器",
			"rawText": "段寄存器",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "段寄存器",
			"lineHeight": 1.2,
			"baseline": 24
		},
		{
			"type": "arrow",
			"version": 204,
			"versionNonce": 974955944,
			"isDeleted": false,
			"id": "lifU3eSCL8S7Z8a_asjVq",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1482.856602436643,
			"y": 389.4148871295903,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 9.286467506659164,
			"height": 53.830335152536634,
			"seed": 2003863576,
			"groupIds": [
				"ki5JpmeAR5ojDEjMEi7iv"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358623,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "mAhLhW3L",
				"focus": -0.7470640890886459,
				"gap": 20.977947187898906
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-9.286467506659164,
					53.830335152536634
				]
			]
		},
		{
			"type": "text",
			"version": 133,
			"versionNonce": 927588197,
			"isDeleted": false,
			"id": "mAhLhW3L",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1454.1603291397787,
			"y": 464.2231694700258,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 109.40090942382812,
			"height": 89.41570554874919,
			"seed": 1103138664,
			"groupIds": [
				"ki5JpmeAR5ojDEjMEi7iv"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "lifU3eSCL8S7Z8a_asjVq",
					"type": "arrow"
				}
			],
			"updated": 1693060909732,
			"link": null,
			"locked": false,
			"fontSize": 24.837695985763663,
			"fontFamily": 4,
			"text": "00 代码段\n01 堆\n10 栈",
			"rawText": "00 代码段\n01 堆\n10 栈",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "00 代码段\n01 堆\n10 栈",
			"lineHeight": 1.2,
			"baseline": 80
		},
		{
			"type": "arrow",
			"version": 232,
			"versionNonce": 499757224,
			"isDeleted": false,
			"id": "GD3dZFWnC-OI0lyrBbnpu",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1688.678179039697,
			"y": 390.206526580692,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 0.05536622689282922,
			"height": 68.07939230300707,
			"seed": 924743192,
			"groupIds": [
				"ki5JpmeAR5ojDEjMEi7iv"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358623,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "9LY24N69",
				"focus": -0.7145986176918743,
				"gap": 6.728799443556454
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-0.05536622689282922,
					68.07939230300707
				]
			]
		},
		{
			"type": "text",
			"version": 430,
			"versionNonce": 575796587,
			"isDeleted": false,
			"id": "9LY24N69",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1610.1097376478467,
			"y": 465.01471832725554,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 549.8323974609375,
			"height": 73.58321850628874,
			"seed": 2062487320,
			"groupIds": [
				"ki5JpmeAR5ojDEjMEi7iv"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "GD3dZFWnC-OI0lyrBbnpu",
					"type": "arrow"
				}
			],
			"updated": 1693060909736,
			"link": null,
			"locked": false,
			"fontSize": 20.439782918413542,
			"fontFamily": 4,
			"text": "这是段内偏移【与基址寄存器的偏移量不同，\n这是在虚拟地址空间中某一段的偏移量，\n而基址寄存器里的是虚拟地址与实际物理内存地址的偏移量】",
			"rawText": "这是段内偏移【与基址寄存器的偏移量不同，\n这是在虚拟地址空间中某一段的偏移量，\n而基址寄存器里的是虚拟地址与实际物理内存地址的偏移量】",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "这是段内偏移【与基址寄存器的偏移量不同，\n这是在虚拟地址空间中某一段的偏移量，\n而基址寄存器里的是虚拟地址与实际物理内存地址的偏移量】",
			"lineHeight": 1.2,
			"baseline": 66
		},
		{
			"type": "image",
			"version": 238,
			"versionNonce": 1033722792,
			"isDeleted": false,
			"id": "Hw28W6x9",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1425.9350334254498,
			"y": 684.0365632403942,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 393.15875003869405,
			"height": 78.8172022483231,
			"seed": 58593,
			"groupIds": [
				"kCbpw4YUlxUSUqPcPHXaz",
				"IYbtp213juZ1iN_TXFM7O",
				"bD-L-w2z4sBMPZBQ2ceIW"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358623,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "344bf0e8d16402d22ca7d0a7501b90963234407c",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "image",
			"version": 275,
			"versionNonce": 2050331352,
			"isDeleted": false,
			"id": "KxXgsaVd",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1434.2718545653381,
			"y": 772.8570453103197,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 380.99845161345047,
			"height": 101.38156223190526,
			"seed": 87002,
			"groupIds": [
				"kCbpw4YUlxUSUqPcPHXaz",
				"IYbtp213juZ1iN_TXFM7O",
				"bD-L-w2z4sBMPZBQ2ceIW"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358623,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "4b30d1da827c9272daf1ea66bfa08a7d4290b01d",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "text",
			"version": 264,
			"versionNonce": 1543678661,
			"isDeleted": false,
			"id": "CjkU7Vqh",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1336.2924922039085,
			"y": 816.0514267863368,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 100,
			"height": 24,
			"seed": 53112040,
			"groupIds": [
				"kCbpw4YUlxUSUqPcPHXaz",
				"IYbtp213juZ1iN_TXFM7O",
				"bD-L-w2z4sBMPZBQ2ceIW"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "oalv4H9i9Xukcul11gGbj",
					"type": "arrow"
				}
			],
			"updated": 1693060909738,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "空闲列表：",
			"rawText": "空闲列表：",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "空闲列表：",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 745,
			"versionNonce": 816674776,
			"isDeleted": false,
			"id": "oalv4H9i9Xukcul11gGbj",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1431.6471745197907,
			"y": 811.4668774474379,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 19.28418728445945,
			"height": 13.540203734442798,
			"seed": 1294764440,
			"groupIds": [
				"kCbpw4YUlxUSUqPcPHXaz",
				"IYbtp213juZ1iN_TXFM7O",
				"bD-L-w2z4sBMPZBQ2ceIW"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358623,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "CjkU7Vqh",
				"focus": 0.32396021966228017,
				"gap": 4.58454933889891
			},
			"endBinding": {
				"elementId": "VCOzUOze",
				"focus": -0.5918122008871513,
				"gap": 6.017772675950937
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					19.28418728445945,
					-13.540203734442798
				]
			]
		},
		{
			"type": "text",
			"version": 331,
			"versionNonce": 1525026827,
			"isDeleted": false,
			"id": "VCOzUOze",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1291.3469781331194,
			"y": 767.9089010370442,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 220.0399932861328,
			"height": 24,
			"seed": 207921304,
			"groupIds": [
				"kCbpw4YUlxUSUqPcPHXaz",
				"IYbtp213juZ1iN_TXFM7O",
				"bD-L-w2z4sBMPZBQ2ceIW"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "oalv4H9i9Xukcul11gGbj",
					"type": "arrow"
				}
			],
			"updated": 1693060909739,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "记录了内存中的空闲空间",
			"rawText": "记录了内存中的空闲空间",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "记录了内存中的空闲空间",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "rectangle",
			"version": 259,
			"versionNonce": 2027994328,
			"isDeleted": false,
			"id": "0liEF2j1KrpJoFFcZaXH8",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1280.6278223475285,
			"y": 667.8628922654768,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 559.6560440240247,
			"height": 207.61433382106486,
			"seed": 986231784,
			"groupIds": [
				"kCbpw4YUlxUSUqPcPHXaz",
				"IYbtp213juZ1iN_TXFM7O",
				"bD-L-w2z4sBMPZBQ2ceIW"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [
				{
					"id": "OO6EjAK-seeBaetEdtaTA",
					"type": "arrow"
				},
				{
					"id": "1mi6XAlF1zNHNVdohF6Qf",
					"type": "arrow"
				}
			],
			"updated": 1692192358623,
			"link": null,
			"locked": false
		},
		{
			"type": "arrow",
			"version": 433,
			"versionNonce": 272112808,
			"isDeleted": false,
			"id": "OO6EjAK-seeBaetEdtaTA",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1407.0017659210087,
			"y": 884.5039711858894,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 42.87685270348857,
			"height": 48.89468276972059,
			"seed": 1902966504,
			"groupIds": [
				"IYbtp213juZ1iN_TXFM7O",
				"bD-L-w2z4sBMPZBQ2ceIW"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358623,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "0liEF2j1KrpJoFFcZaXH8",
				"focus": 0,
				"gap": 9.026745099347693
			},
			"endBinding": {
				"elementId": "_LKBnIMcS01h0LUj7RUd7",
				"focus": -0.3536359142929165,
				"gap": 5.124492954986124
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					0,
					0
				],
				[
					-42.87685270348857,
					48.89468276972059
				]
			]
		},
		{
			"type": "text",
			"version": 298,
			"versionNonce": 977996325,
			"isDeleted": false,
			"id": "4Q83cSMf",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1272.3533203540298,
			"y": 946.9386855192098,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 225.19996643066406,
			"height": 48,
			"seed": 972680424,
			"groupIds": [
				"Bw_9t16Qt_3Ug4DSNE3hP",
				"IYbtp213juZ1iN_TXFM7O",
				"bD-L-w2z4sBMPZBQ2ceIW"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "OO6EjAK-seeBaetEdtaTA",
					"type": "arrow"
				}
			],
			"updated": 1693060909742,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "申请一块 1 字节的空间，\n对malloc()的调用返回20",
			"rawText": "申请一块 1 字节的空间，\n对malloc()的调用返回20",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "申请一块 1 字节的空间，\n对malloc()的调用返回20",
			"lineHeight": 1.2,
			"baseline": 42
		},
		{
			"type": "image",
			"version": 262,
			"versionNonce": 794707880,
			"isDeleted": false,
			"id": "g4xQHS0f",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1219.4098499355437,
			"y": 1000.5667855980323,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 323.2802915583749,
			"height": 71.09483590287913,
			"seed": 21231,
			"groupIds": [
				"Bw_9t16Qt_3Ug4DSNE3hP",
				"IYbtp213juZ1iN_TXFM7O",
				"bD-L-w2z4sBMPZBQ2ceIW"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358623,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "5774fbd4e902a80afea12f63535d5da8fff81e26",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "rectangle",
			"version": 153,
			"versionNonce": 843671256,
			"isDeleted": false,
			"id": "_LKBnIMcS01h0LUj7RUd7",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1210.670820431418,
			"y": 938.5231469105962,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 336.2449493218121,
			"height": 142.1707044546282,
			"seed": 1155168744,
			"groupIds": [
				"Bw_9t16Qt_3Ug4DSNE3hP",
				"IYbtp213juZ1iN_TXFM7O",
				"bD-L-w2z4sBMPZBQ2ceIW"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [
				{
					"id": "OO6EjAK-seeBaetEdtaTA",
					"type": "arrow"
				}
			],
			"updated": 1692192358623,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 187,
			"versionNonce": 727570091,
			"isDeleted": false,
			"id": "tau57uKD",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1249.0343292803732,
			"y": 905.6132929722712,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 58.03997802734375,
			"height": 34.832059685048755,
			"seed": 511360488,
			"groupIds": [
				"IYbtp213juZ1iN_TXFM7O",
				"bD-L-w2z4sBMPZBQ2ceIW"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1693060909743,
			"link": null,
			"locked": false,
			"fontSize": 29.026716404207296,
			"fontFamily": 4,
			"text": "分割",
			"rawText": "分割",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "分割",
			"lineHeight": 1.2,
			"baseline": 25
		},
		{
			"type": "text",
			"version": 174,
			"versionNonce": 588283269,
			"isDeleted": false,
			"id": "96apIcZw",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1696.608790485788,
			"y": 953.0035182254336,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 109.83993530273438,
			"height": 24,
			"seed": 435014888,
			"groupIds": [
				"3QwqlFzgfFci7a1uruXyh",
				"IYbtp213juZ1iN_TXFM7O",
				"bD-L-w2z4sBMPZBQ2ceIW"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1693060909744,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "调用free(10)",
			"rawText": "调用free(10)",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "调用free(10)",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "image",
			"version": 165,
			"versionNonce": 610172328,
			"isDeleted": false,
			"id": "0Xt0N4H3",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1615.3424142471465,
			"y": 983.7222742137213,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 361.5904823794772,
			"height": 69.53663122682254,
			"seed": 91010,
			"groupIds": [
				"3QwqlFzgfFci7a1uruXyh",
				"IYbtp213juZ1iN_TXFM7O",
				"bD-L-w2z4sBMPZBQ2ceIW"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358623,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "816d06f5c9e22b960e8a91b1025efbf7ab1abf2c",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "image",
			"version": 207,
			"versionNonce": 890212568,
			"isDeleted": false,
			"id": "k4yj2CZU",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1663.501221676121,
			"y": 1057.5440450547867,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 241.20171942744307,
			"height": 80.40057314248102,
			"seed": 66313,
			"groupIds": [
				"3QwqlFzgfFci7a1uruXyh",
				"IYbtp213juZ1iN_TXFM7O",
				"bD-L-w2z4sBMPZBQ2ceIW"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358623,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "54e6ed166ef74e32fb43fbbb9bcc02964e675fc8",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "rectangle",
			"version": 183,
			"versionNonce": 303073448,
			"isDeleted": false,
			"id": "a9NTxYEhumDYPcBllgA2M",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1613.3467989011751,
			"y": 940.7798475330034,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 366.3339848724095,
			"height": 196.3309741847313,
			"seed": 934065560,
			"groupIds": [
				"3QwqlFzgfFci7a1uruXyh",
				"IYbtp213juZ1iN_TXFM7O",
				"bD-L-w2z4sBMPZBQ2ceIW"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [
				{
					"id": "1mi6XAlF1zNHNVdohF6Qf",
					"type": "arrow"
				}
			],
			"updated": 1692192358623,
			"link": null,
			"locked": false
		},
		{
			"type": "arrow",
			"version": 359,
			"versionNonce": 999798232,
			"isDeleted": false,
			"id": "1mi6XAlF1zNHNVdohF6Qf",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1738.6209255703016,
			"y": 891.1329503525741,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 22.61053301478796,
			"height": 38.36350884895535,
			"seed": 641255576,
			"groupIds": [
				"IYbtp213juZ1iN_TXFM7O",
				"bD-L-w2z4sBMPZBQ2ceIW"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358624,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "0liEF2j1KrpJoFFcZaXH8",
				"focus": -0.31599272681525414,
				"gap": 15.655724266032337
			},
			"endBinding": {
				"elementId": "a9NTxYEhumDYPcBllgA2M",
				"focus": 0.12125052946052535,
				"gap": 11.283388331473873
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					22.61053301478796,
					38.36350884895535
				]
			]
		},
		{
			"type": "text",
			"version": 121,
			"versionNonce": 845400395,
			"isDeleted": false,
			"id": "bUmgmTni",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1859.8077966274807,
			"y": 898.4194908521912,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 66.99346923828125,
			"height": 40.17884643459474,
			"seed": 881974424,
			"groupIds": [
				"IYbtp213juZ1iN_TXFM7O",
				"bD-L-w2z4sBMPZBQ2ceIW"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1693060909746,
			"link": null,
			"locked": false,
			"fontSize": 33.48237202882895,
			"fontFamily": 4,
			"text": "合并",
			"rawText": "合并",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "合并",
			"lineHeight": 1.2,
			"baseline": 29
		},
		{
			"type": "line",
			"version": 30,
			"versionNonce": 1741896408,
			"isDeleted": false,
			"id": "kkBUWPZKiMoTR7V1kcron",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1766.9786179946248,
			"y": 1045.3750628665587,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 0.5324646711765126,
			"height": 16.239796709046914,
			"seed": 1277197800,
			"groupIds": [
				"bD-L-w2z4sBMPZBQ2ceIW"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358624,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": null,
			"points": [
				[
					0,
					0
				],
				[
					-0.5324646711765126,
					16.239796709046914
				]
			]
		},
		{
			"type": "line",
			"version": 42,
			"versionNonce": 506756776,
			"isDeleted": false,
			"id": "UmtNIGhUSGG4_ONFwb_xq",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1781.6210613130431,
			"y": 1046.173739561873,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 5.058302663198219,
			"height": 16.239806864771936,
			"seed": 1026748392,
			"groupIds": [
				"bD-L-w2z4sBMPZBQ2ceIW"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358624,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": null,
			"points": [
				[
					0,
					0
				],
				[
					-5.058302663198219,
					16.239806864771936
				]
			]
		},
		{
			"type": "line",
			"version": 56,
			"versionNonce": 1817583576,
			"isDeleted": false,
			"id": "QWhSoowoUb9f4rCPLVIAy",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1757.394457027954,
			"y": 1054.1605268264648,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 38.33658293233111,
			"height": 11.98018089688776,
			"seed": 2071942120,
			"groupIds": [
				"bD-L-w2z4sBMPZBQ2ceIW"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358624,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": null,
			"points": [
				[
					0,
					0
				],
				[
					14.376221138555593,
					10.91528202171071
				],
				[
					38.33658293233111,
					-1.0648988751770503
				]
			]
		},
		{
			"type": "image",
			"version": 96,
			"versionNonce": 1132358056,
			"isDeleted": false,
			"id": "5gcdSplk",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1328.9405808304275,
			"y": 1187.6486617941928,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 431.451558461378,
			"height": 209.9538520271923,
			"seed": 67723,
			"groupIds": [
				"hpYTfzerspshhWbChz0ls"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358624,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "92ba2bbae35919cf05722392beb53b474b271c68",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "line",
			"version": 134,
			"versionNonce": 154428632,
			"isDeleted": false,
			"id": "LoltwleJYZ69iBoQzhl7-",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1330.8420866727124,
			"y": 1195.3081153001074,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 45.917427905161,
			"height": 106.91216283762986,
			"seed": 224364008,
			"groupIds": [
				"hpYTfzerspshhWbChz0ls"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358624,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": null,
			"points": [
				[
					0,
					0
				],
				[
					-31.52536626681062,
					52.08542070861796
				],
				[
					14.392061638350375,
					106.91216283762986
				]
			]
		},
		{
			"type": "text",
			"version": 138,
			"versionNonce": 1838187749,
			"isDeleted": false,
			"id": "t2vs7l5I",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1256.0103706873294,
			"y": 1230.460470249557,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 40,
			"height": 24,
			"seed": 1876545256,
			"groupIds": [
				"hpYTfzerspshhWbChz0ls"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1693060909747,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "头块",
			"rawText": "头块",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "头块",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 158,
			"versionNonce": 1543637464,
			"isDeleted": false,
			"id": "NUwm9JHSx5oMlSeQADASJ",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1547.5251095101528,
			"y": 1265.1923497008434,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 58.59419620935955,
			"height": 5.456481379449997,
			"seed": 1125931672,
			"groupIds": [
				"hpYTfzerspshhWbChz0ls"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358624,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "88N7V51M",
				"focus": 0.050329046120777994,
				"gap": 4.8367857607113365
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					58.59419620935955,
					-5.456481379449997
				]
			]
		},
		{
			"type": "text",
			"version": 146,
			"versionNonce": 1431463915,
			"isDeleted": false,
			"id": "88N7V51M",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1610.9560914802237,
			"y": 1238.2445222330255,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 218.1199951171875,
			"height": 24,
			"seed": 616395752,
			"groupIds": [
				"hpYTfzerspshhWbChz0ls"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "NUwm9JHSx5oMlSeQADASJ",
					"type": "arrow"
				}
			],
			"updated": 1693060909749,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "幻数【提供完整性检查】",
			"rawText": "幻数【提供完整性检查】",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "幻数【提供完整性检查】",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 98,
			"versionNonce": 802361048,
			"isDeleted": false,
			"id": "llQjbGZ-l3uo4Db1iPLOH",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1549.1834529260525,
			"y": 1219.864753211693,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 38.141519004864904,
			"height": 19.899931210382192,
			"seed": 1649098136,
			"groupIds": [
				"hpYTfzerspshhWbChz0ls"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358624,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "JgNmTv4P",
				"focus": 0.8032186785987308,
				"gap": 9.397124720872398
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					38.141519004864904,
					-19.899931210382192
				]
			]
		},
		{
			"type": "text",
			"version": 103,
			"versionNonce": 760782917,
			"isDeleted": false,
			"id": "JgNmTv4P",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1596.7220966517898,
			"y": 1184.4871117843772,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 160,
			"height": 24,
			"seed": 455830504,
			"groupIds": [
				"hpYTfzerspshhWbChz0ls"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "llQjbGZ-l3uo4Db1iPLOH",
					"type": "arrow"
				}
			],
			"updated": 1693060909751,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "所分配的空间大小",
			"rawText": "所分配的空间大小",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "所分配的空间大小",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "image",
			"version": 225,
			"versionNonce": 1295741912,
			"isDeleted": false,
			"id": "acHtzckA",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1211.5870242978026,
			"y": 1544.2194246187455,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 395.0361649461472,
			"height": 181.00728300938013,
			"seed": 39474,
			"groupIds": [
				"o9Xu2uv_3UUlUO783z1tr"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "e1rh6DlV_BeoGi80SxJn7",
					"type": "arrow"
				}
			],
			"updated": 1692192358624,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "91440f29495dde4eeb4977c0da92426097f4a710",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "text",
			"version": 233,
			"versionNonce": 1781805707,
			"isDeleted": false,
			"id": "OhHXyy46",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1282.2113231240876,
			"y": 1721.7869043261726,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 318.20001220703125,
			"height": 48,
			"seed": 13364120,
			"groupIds": [
				"o9Xu2uv_3UUlUO783z1tr"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1693060909753,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "什么都没有分配的堆，\n已经有了一块头块【就是空闲列表】",
			"rawText": "什么都没有分配的堆，\n已经有了一块头块【就是空闲列表】",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "什么都没有分配的堆，\n已经有了一块头块【就是空闲列表】",
			"lineHeight": 1.2,
			"baseline": 42
		},
		{
			"type": "line",
			"version": 39,
			"versionNonce": 1246705880,
			"isDeleted": false,
			"id": "Kuic65vLbOB1utpI2nTVD",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1216.8774867848151,
			"y": 1576.9530995743548,
			"strokeColor": "#e03131",
			"backgroundColor": "#ffffff",
			"width": 32.32623709429913,
			"height": 1.3194177048451365,
			"seed": 1922091496,
			"groupIds": [
				"o9Xu2uv_3UUlUO783z1tr"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358624,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": null,
			"points": [
				[
					0,
					0
				],
				[
					32.32623709429913,
					1.3194177048451365
				]
			]
		},
		{
			"type": "text",
			"version": 334,
			"versionNonce": 675696549,
			"isDeleted": false,
			"id": "DN22q8o9",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1208.1361809093987,
			"y": 1584.0450578198763,
			"strokeColor": "#e03131",
			"backgroundColor": "#ffffff",
			"width": 70.31745910644531,
			"height": 66.02237876618705,
			"seed": 831369624,
			"groupIds": [
				"o9Xu2uv_3UUlUO783z1tr"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1693060909756,
			"link": null,
			"locked": false,
			"fontSize": 13.754662242955634,
			"fontFamily": 4,
			"text": "head指针，\n永远指向最\n新释放空间\n的空闲列表",
			"rawText": "head指针，\n永远指向最\n新释放空间\n的空闲列表",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "head指针，\n永远指向最\n新释放空间\n的空闲列表",
			"lineHeight": 1.2,
			"baseline": 62
		},
		{
			"type": "arrow",
			"version": 1559,
			"versionNonce": 1520590296,
			"isDeleted": false,
			"id": "e1rh6DlV_BeoGi80SxJn7",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1610.9503924678902,
			"y": 1603.7547661983067,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 190.71578653088204,
			"height": 14.814219835695894,
			"seed": 1616109208,
			"groupIds": [
				"o9Xu2uv_3UUlUO783z1tr"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "RPX2gkTz"
				}
			],
			"updated": 1692192358624,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "acHtzckA",
				"focus": -0.14445080112100797,
				"gap": 4.327203223940273
			},
			"endBinding": {
				"elementId": "kmJVe3rT",
				"focus": 0.3428428405492537,
				"gap": 11.238317381156094
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					190.71578653088204,
					-14.814219835695894
				]
			]
		},
		{
			"type": "text",
			"version": 91,
			"versionNonce": 1570573224,
			"isDeleted": false,
			"id": "RPX2gkTz",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1697.2298822768557,
			"y": 1554.7327377442653,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 100,
			"height": 72,
			"seed": 1597406184,
			"groupIds": [
				"o9Xu2uv_3UUlUO783z1tr"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358624,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "分配了一个\n100字节\n的空间",
			"rawText": "分配了一个\n100字节\n的空间",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "e1rh6DlV_BeoGi80SxJn7",
			"originalText": "分配了一个\n100字节\n的空间",
			"lineHeight": 1.2,
			"baseline": 68
		},
		{
			"type": "image",
			"version": 895,
			"versionNonce": 524870360,
			"isDeleted": false,
			"id": "kmJVe3rT",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1812.9044963799283,
			"y": 1483.72162480832,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 318.9181600486743,
			"height": 292.79517082967027,
			"seed": 791,
			"groupIds": [
				"K8u4-n0LfZRki0crDSLss",
				"o9Xu2uv_3UUlUO783z1tr"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "e1rh6DlV_BeoGi80SxJn7",
					"type": "arrow"
				},
				{
					"id": "awcj7RpfyZgPcmNMH1uZ9",
					"type": "arrow"
				}
			],
			"updated": 1692192358624,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "771ede9c64847bcb37135bde6607367e3c85870a",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "line",
			"version": 330,
			"versionNonce": 5068456,
			"isDeleted": false,
			"id": "4aeE9WOTF7q3FiW9YSslv",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 2001.2158396508726,
			"y": 1501.5264990037715,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 16.27117097317432,
			"height": 52.30027791794282,
			"seed": 299609240,
			"groupIds": [
				"K8u4-n0LfZRki0crDSLss",
				"o9Xu2uv_3UUlUO783z1tr"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358624,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": null,
			"points": [
				[
					0,
					0
				],
				[
					16.27117097317432,
					19.757891636099657
				],
				[
					0,
					52.30027791794282
				]
			]
		},
		{
			"type": "text",
			"version": 335,
			"versionNonce": 566470955,
			"isDeleted": false,
			"id": "Ztxvw7Do",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 2021.2642617852198,
			"y": 1514.3110158172626,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 49.839996337890625,
			"height": 24,
			"seed": 1916092392,
			"groupIds": [
				"K8u4-n0LfZRki0crDSLss",
				"o9Xu2uv_3UUlUO783z1tr"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1693060909757,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "8字节",
			"rawText": "8字节",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "8字节",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "line",
			"version": 338,
			"versionNonce": 482099624,
			"isDeleted": false,
			"id": "RHDKvLpsJvRbxPFDbk0KL",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 2001.2158396508726,
			"y": 1635.763892293806,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 16.852276305163286,
			"height": 54.043616081658,
			"seed": 656748008,
			"groupIds": [
				"K8u4-n0LfZRki0crDSLss",
				"o9Xu2uv_3UUlUO783z1tr"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358624,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": null,
			"points": [
				[
					0,
					0
				],
				[
					16.852276305163286,
					27.89347712268659
				],
				[
					0,
					54.043616081658
				]
			]
		},
		{
			"type": "text",
			"version": 337,
			"versionNonce": 210178821,
			"isDeleted": false,
			"id": "DUFF65Ov",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 2019.6661888706276,
			"y": 1651.453957934991,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 49.839996337890625,
			"height": 24,
			"seed": 2053922456,
			"groupIds": [
				"K8u4-n0LfZRki0crDSLss",
				"o9Xu2uv_3UUlUO783z1tr"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1693060909758,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "8字节",
			"rawText": "8字节",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "8字节",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "image",
			"version": 368,
			"versionNonce": 1108724904,
			"isDeleted": false,
			"id": "uZFGMfYL",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1836.9680263450393,
			"y": 1911.4295842031158,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 276.9571639586411,
			"height": 500.00000000000006,
			"seed": 79859,
			"groupIds": [
				"o9Xu2uv_3UUlUO783z1tr"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "awcj7RpfyZgPcmNMH1uZ9",
					"type": "arrow"
				},
				{
					"id": "FkbyuF-5IZa33T49UbgH6",
					"type": "arrow"
				}
			],
			"updated": 1692192358624,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "bee97a857575f2db63d1ad2dd78ce33d3f642596",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "arrow",
			"version": 1349,
			"versionNonce": 1819849176,
			"isDeleted": false,
			"id": "awcj7RpfyZgPcmNMH1uZ9",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1950.391658920599,
			"y": 1794.4688495270846,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 4.152209352749196,
			"height": 104.13301913107011,
			"seed": 548948712,
			"groupIds": [
				"o9Xu2uv_3UUlUO783z1tr"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "dITK0Dp8"
				}
			],
			"updated": 1692192358624,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "kmJVe3rT",
				"focus": 0.17256990342937836,
				"gap": 17.952053889094145
			},
			"endBinding": {
				"elementId": "uZFGMfYL",
				"focus": -0.0702117038133096,
				"gap": 12.82771554496128
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					4.152209352749196,
					104.13301913107011
				]
			]
		},
		{
			"type": "text",
			"version": 62,
			"versionNonce": 973469608,
			"isDeleted": false,
			"id": "dITK0Dp8",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1999.2526989990993,
			"y": 1834.9070357968576,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 215.185546875,
			"height": 48,
			"seed": 1451920792,
			"groupIds": [
				"o9Xu2uv_3UUlUO783z1tr"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358624,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "再多分配两块100字节的\n空间",
			"rawText": "再多分配两块100字节的空间",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "awcj7RpfyZgPcmNMH1uZ9",
			"originalText": "再多分配两块100字节的空间",
			"lineHeight": 1.2,
			"baseline": 44
		},
		{
			"type": "image",
			"version": 204,
			"versionNonce": 1261745880,
			"isDeleted": false,
			"id": "kp595uwB",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1285.0813356352264,
			"y": 1896.2461164171746,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 353.1976744186046,
			"height": 499.99999999999994,
			"seed": 1325,
			"groupIds": [
				"o9Xu2uv_3UUlUO783z1tr"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "FkbyuF-5IZa33T49UbgH6",
					"type": "arrow"
				}
			],
			"updated": 1692192358624,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "d14cd6a75258249e3d9bb7ef2911d7d9d01f0775",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "arrow",
			"version": 489,
			"versionNonce": 951632552,
			"isDeleted": false,
			"id": "FkbyuF-5IZa33T49UbgH6",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1813.7962259949077,
			"y": 2167.517326240841,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 153.21801083683795,
			"height": 3.8960219555960975,
			"seed": 552403688,
			"groupIds": [
				"o9Xu2uv_3UUlUO783z1tr"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "U00k7YMD"
				}
			],
			"updated": 1692192358624,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "uZFGMfYL",
				"focus": -0.007799354959709257,
				"gap": 23.171800350131548
			},
			"endBinding": {
				"elementId": "kp595uwB",
				"focus": 0.11876591899756453,
				"gap": 22.29920510423881
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-153.21801083683795,
					3.8960219555960975
				]
			]
		},
		{
			"type": "text",
			"version": 26,
			"versionNonce": 1579686872,
			"isDeleted": false,
			"id": "U00k7YMD",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1710.3855563600187,
			"y": 2162.0662987402056,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 108.984375,
			"height": 24,
			"seed": 666874344,
			"groupIds": [
				"o9Xu2uv_3UUlUO783z1tr"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358624,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "free(16500)",
			"rawText": "free(16500)",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "FkbyuF-5IZa33T49UbgH6",
			"originalText": "free(16500)",
			"lineHeight": 1.2,
			"baseline": 20
		},
		{
			"type": "arrow",
			"version": 108,
			"versionNonce": 215625128,
			"isDeleted": false,
			"id": "fYwk0bC425f0h5kVxDyJJ",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1442.6560881321334,
			"y": 1918.0808135989566,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 24.278013685093583,
			"height": 14.473432605363769,
			"seed": 275883928,
			"groupIds": [
				"o9Xu2uv_3UUlUO783z1tr"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358624,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "2aL1wv1h",
				"focus": 0.40376873383399214,
				"gap": 3.735095468711279
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					24.278013685093583,
					-14.473432605363769
				]
			]
		},
		{
			"type": "text",
			"version": 61,
			"versionNonce": 829115339,
			"isDeleted": false,
			"id": "2aL1wv1h",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1470.6691972859383,
			"y": 1886.5660658009263,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 43.0999755859375,
			"height": 24,
			"seed": 1629081752,
			"groupIds": [
				"o9Xu2uv_3UUlUO783z1tr"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "fYwk0bC425f0h5kVxDyJJ",
					"type": "arrow"
				}
			],
			"updated": 1693060909760,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "16384",
			"rawText": "16384",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "16384",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 175,
			"versionNonce": 1335244968,
			"isDeleted": false,
			"id": "bBgDflAoXqmXFICDmT5aF",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1442.1892101036722,
			"y": 2083.7375231651704,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 21.607270974626545,
			"height": 1.0419197153146342,
			"seed": 467049960,
			"groupIds": [
				"o9Xu2uv_3UUlUO783z1tr"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358624,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "kaElSfA7",
				"focus": 0.6824681151889775,
				"gap": 4.668851525634182
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					21.607270974626545,
					1.0419197153146342
				]
			]
		},
		{
			"type": "text",
			"version": 106,
			"versionNonce": 1721264741,
			"isDeleted": false,
			"id": "kaElSfA7",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1468.465332603933,
			"y": 2082.8735843502336,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 41.39996337890625,
			"height": 24,
			"seed": 2079159272,
			"groupIds": [
				"o9Xu2uv_3UUlUO783z1tr"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "bBgDflAoXqmXFICDmT5aF",
					"type": "arrow"
				}
			],
			"updated": 1693060909761,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "16500",
			"rawText": "16500",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "16500",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 121,
			"versionNonce": 345564072,
			"isDeleted": false,
			"id": "rZ1aHKc6WszkChSrVtTXK",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1439.1196696403733,
			"y": 2049.663792065341,
			"strokeColor": "#e03131",
			"backgroundColor": "#ffffff",
			"width": 50.899305835335326,
			"height": 7.984218647225816,
			"seed": 1695881624,
			"groupIds": [
				"o9Xu2uv_3UUlUO783z1tr"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358625,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "yn1S2BAQ",
				"focus": 0.662478523792419,
				"gap": 8.73272665313766
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					50.899305835335326,
					-7.984218647225816
				]
			]
		},
		{
			"type": "arrow",
			"version": 120,
			"versionNonce": 1217825496,
			"isDeleted": false,
			"id": "gzCOjB2mFwJwNIya-3F-8",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1438.1216208941576,
			"y": 2072.119374887695,
			"strokeColor": "#e03131",
			"backgroundColor": "#ffffff",
			"width": 51.8973545815511,
			"height": 27.44571233843226,
			"seed": 1631006872,
			"groupIds": [
				"o9Xu2uv_3UUlUO783z1tr"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358625,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "yn1S2BAQ",
				"focus": 0.8510755408584153,
				"gap": 8.73272665313766
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					51.8973545815511,
					-27.44571233843226
				]
			]
		},
		{
			"type": "text",
			"version": 250,
			"versionNonce": 1027971691,
			"isDeleted": false,
			"id": "yn1S2BAQ",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1498.7517021288463,
			"y": 2028.8299861070461,
			"strokeColor": "#e03131",
			"backgroundColor": "#ffffff",
			"width": 222.40060424804688,
			"height": 33.13736307482735,
			"seed": 1651720424,
			"groupIds": [
				"o9Xu2uv_3UUlUO783z1tr"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "rZ1aHKc6WszkChSrVtTXK",
					"type": "arrow"
				},
				{
					"id": "gzCOjB2mFwJwNIya-3F-8",
					"type": "arrow"
				}
			],
			"updated": 1693060909762,
			"link": null,
			"locked": false,
			"fontSize": 13.807234614511396,
			"fontFamily": 4,
			"text": "head指针指向了最近空闲的内存块，\nnext指针指向了下一个空闲空间",
			"rawText": "head指针指向了最近空闲的内存块，\nnext指针指向了下一个空闲空间",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "head指针指向了最近空闲的内存块，\nnext指针指向了下一个空闲空间",
			"lineHeight": 1.2,
			"baseline": 28
		},
		{
			"type": "image",
			"version": 213,
			"versionNonce": 2016374744,
			"isDeleted": false,
			"id": "RtI0hcqP",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 316.499253831479,
			"y": 2582.7664288150922,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 351,
			"height": 494,
			"seed": 18623,
			"groupIds": [
				"x_CuO9ifqROk26y02s9ay",
				"EC2cD0mUUxnnlOYv3Hu2-"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "FV_NQFkmRDAp4r8JKWQGw",
					"type": "arrow"
				},
				{
					"id": "hmSF-sw4uwbpmZY6VTCdO",
					"type": "arrow"
				}
			],
			"updated": 1692192358625,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "dbc8c15eaa293b2602301df3136b0f95e1508dc9",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "rectangle",
			"version": 279,
			"versionNonce": 2023889320,
			"isDeleted": false,
			"id": "FVXrrTD3L1fjZTiCDBnYv",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 336.57536927724834,
			"y": 2577.524622338659,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 308.2717217149295,
			"height": 443.0869159328613,
			"seed": 166443813,
			"groupIds": [
				"x_CuO9ifqROk26y02s9ay",
				"EC2cD0mUUxnnlOYv3Hu2-"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [],
			"updated": 1692192358625,
			"link": null,
			"locked": false
		},
		{
			"type": "arrow",
			"version": 480,
			"versionNonce": 1835250904,
			"isDeleted": false,
			"id": "FV_NQFkmRDAp4r8JKWQGw",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 643.9884085276675,
			"y": 2679.7093915556434,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 54.956463887948985,
			"height": 42.07609589374488,
			"seed": 1335009611,
			"groupIds": [
				"x_CuO9ifqROk26y02s9ay",
				"EC2cD0mUUxnnlOYv3Hu2-"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358625,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "xNYtLlHM",
				"focus": 0.7408594106583871,
				"gap": 4.508164830271426
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					54.956463887948985,
					-42.07609589374488
				]
			]
		},
		{
			"type": "text",
			"version": 231,
			"versionNonce": 1464325573,
			"isDeleted": false,
			"id": "xNYtLlHM",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 703.4530372458879,
			"y": 2616.8099347094717,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 125.82283020019531,
			"height": 37.73911597198742,
			"seed": 1890265189,
			"groupIds": [
				"x_CuO9ifqROk26y02s9ay",
				"EC2cD0mUUxnnlOYv3Hu2-"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "FV_NQFkmRDAp4r8JKWQGw",
					"type": "arrow"
				}
			],
			"updated": 1693060909764,
			"link": null,
			"locked": false,
			"fontSize": 31.449263309989515,
			"fontFamily": 4,
			"text": "物理内存",
			"rawText": "物理内存",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "物理内存",
			"lineHeight": 1.2,
			"baseline": 26
		},
		{
			"type": "image",
			"version": 225,
			"versionNonce": 499603928,
			"isDeleted": false,
			"id": "VIf6ZmiQ",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1169.6740197912986,
			"y": 2566.725276771392,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 360.18518518518516,
			"height": 500,
			"seed": 65492,
			"groupIds": [
				"UzZSjcTMuXBAKOEJEMTKM",
				"EC2cD0mUUxnnlOYv3Hu2-"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "svoHh_PQrTudj1WXr_S92",
					"type": "arrow"
				},
				{
					"id": "JQmWgtC9kI6sj0tzpqJ23",
					"type": "arrow"
				},
				{
					"id": "Zvw23pwXaEYy8_s7hyx_F",
					"type": "arrow"
				},
				{
					"id": "hmSF-sw4uwbpmZY6VTCdO",
					"type": "arrow"
				}
			],
			"updated": 1692192358625,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "70f8389cc1c9b5eccab3104e7e2cfba95ac3e253",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "arrow",
			"version": 459,
			"versionNonce": 139841448,
			"isDeleted": false,
			"id": "svoHh_PQrTudj1WXr_S92",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1460.5383536508452,
			"y": 2721.8394886642473,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 74.70655365132825,
			"height": 5.152160300336163,
			"seed": 1920339723,
			"groupIds": [
				"UzZSjcTMuXBAKOEJEMTKM",
				"EC2cD0mUUxnnlOYv3Hu2-"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358625,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "haj0Q2jl",
				"focus": 1.2649342335689784,
				"gap": 15.671167895454346
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					74.70655365132825,
					-5.152160300336163
				]
			]
		},
		{
			"type": "arrow",
			"version": 457,
			"versionNonce": 745430744,
			"isDeleted": false,
			"id": "JQmWgtC9kI6sj0tzpqJ23",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1461.3971016286284,
			"y": 2771.6438250084966,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 79.85864843839181,
			"height": 31.77174253643625,
			"seed": 436977893,
			"groupIds": [
				"UzZSjcTMuXBAKOEJEMTKM",
				"EC2cD0mUUxnnlOYv3Hu2-"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358625,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "haj0Q2jl",
				"focus": 0.8054698667816337,
				"gap": 9.660325130607589
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					79.85864843839181,
					-31.77174253643625
				]
			]
		},
		{
			"type": "arrow",
			"version": 475,
			"versionNonce": 1598921384,
			"isDeleted": false,
			"id": "Zvw23pwXaEYy8_s7hyx_F",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1463.1144665576496,
			"y": 2875.5459755328206,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 82.4347613451962,
			"height": 105.61954820998153,
			"seed": 124959627,
			"groupIds": [
				"UzZSjcTMuXBAKOEJEMTKM",
				"EC2cD0mUUxnnlOYv3Hu2-"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358625,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "haj0Q2jl",
				"focus": 0.7766836692863044,
				"gap": 11.206472394478851
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					82.4347613451962,
					-105.61954820998153
				]
			]
		},
		{
			"type": "text",
			"version": 287,
			"versionNonce": 35460363,
			"isDeleted": false,
			"id": "haj0Q2jl",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1550.9160751976278,
			"y": 2722.6982038853944,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 253.94456481933594,
			"height": 36.02175104296619,
			"seed": 1761022661,
			"groupIds": [
				"UzZSjcTMuXBAKOEJEMTKM",
				"EC2cD0mUUxnnlOYv3Hu2-"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "svoHh_PQrTudj1WXr_S92",
					"type": "arrow"
				},
				{
					"id": "JQmWgtC9kI6sj0tzpqJ23",
					"type": "arrow"
				},
				{
					"id": "Zvw23pwXaEYy8_s7hyx_F",
					"type": "arrow"
				}
			],
			"updated": 1693060909767,
			"link": null,
			"locked": false,
			"fontSize": 30.01812586913849,
			"fontFamily": 4,
			"text": "同时放进进程A,B,C",
			"rawText": "同时放进进程A,B,C",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "同时放进进程A,B,C",
			"lineHeight": 1.2,
			"baseline": 26
		},
		{
			"type": "arrow",
			"version": 669,
			"versionNonce": 991167912,
			"isDeleted": false,
			"id": "hmSF-sw4uwbpmZY6VTCdO",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 685.6045035823091,
			"y": 2812.249084849122,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 463.9382675249607,
			"height": 7.308504011265995,
			"seed": 1769005688,
			"groupIds": [
				"EC2cD0mUUxnnlOYv3Hu2-"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "hTkWhbS1"
				}
			],
			"updated": 1692192358625,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "RtI0hcqP",
				"focus": -0.057924303031513344,
				"gap": 18.105249750830126
			},
			"endBinding": {
				"elementId": "VIf6ZmiQ",
				"focus": 0.059084931043405,
				"gap": 20.131248684028833
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					463.9382675249607,
					-7.308504011265995
				]
			]
		},
		{
			"type": "text",
			"version": 123,
			"versionNonce": 878086360,
			"isDeleted": false,
			"id": "hTkWhbS1",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 679.5939535473508,
			"y": 2792.3312305618037,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 324,
			"height": 43.199999999999996,
			"seed": 72836872,
			"groupIds": [
				"EC2cD0mUUxnnlOYv3Hu2-"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358625,
			"link": null,
			"locked": false,
			"fontSize": 36,
			"fontFamily": 4,
			"text": "效率太低，进行改进",
			"rawText": "效率太低，进行改进",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "hmSF-sw4uwbpmZY6VTCdO",
			"originalText": "效率太低，进行改进",
			"lineHeight": 1.2,
			"baseline": 37
		},
		{
			"type": "image",
			"version": 5,
			"versionNonce": 1221922984,
			"isDeleted": false,
			"id": "uZHlLJiu",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1256.3180764979293,
			"y": 2770.152936373421,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 499.99999999999994,
			"height": 74.13793103448275,
			"seed": 23717,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358625,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "04d8afd8f2d1092479b19ca2efb233766bafa5bd",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "image",
			"version": 5,
			"versionNonce": 658484696,
			"isDeleted": false,
			"id": "sazgcBed",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1256.3180764979293,
			"y": 2770.152936373421,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 499.99999999999994,
			"height": 74.13793103448275,
			"seed": 83678,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358625,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "04d8afd8f2d1092479b19ca2efb233766bafa5bd",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "image",
			"version": 5,
			"versionNonce": 809286568,
			"isDeleted": false,
			"id": "H53Fi1rX",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1256.3180764979293,
			"y": 2770.152936373421,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 499.99999999999994,
			"height": 74.13793103448275,
			"seed": 98658,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358625,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "04d8afd8f2d1092479b19ca2efb233766bafa5bd",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "image",
			"version": 148,
			"versionNonce": 196883160,
			"isDeleted": false,
			"id": "jtoVfliw",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1025.038963526109,
			"y": 2971.5023154215055,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 401.10288448672327,
			"height": 63.76507394404319,
			"seed": 36941,
			"groupIds": [
				"RhUvMLAxtc-u9WNRyYozO"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "GfglkRtnF6sPXrR62BUnK",
					"type": "arrow"
				}
			],
			"updated": 1692192358625,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "7ad283b1c9740c65f79ddf0c29a1c90eab55876d",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "image",
			"version": 181,
			"versionNonce": 1131873960,
			"isDeleted": false,
			"id": "P1l7AaKG",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1030.7207104931736,
			"y": 3134.2662967935253,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 393.31564875419195,
			"height": 58.31921688424225,
			"seed": 16723,
			"groupIds": [
				"RhUvMLAxtc-u9WNRyYozO"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "GfglkRtnF6sPXrR62BUnK",
					"type": "arrow"
				}
			],
			"updated": 1692192358625,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "04d8afd8f2d1092479b19ca2efb233766bafa5bd",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "arrow",
			"version": 168,
			"versionNonce": 408950744,
			"isDeleted": false,
			"id": "GfglkRtnF6sPXrR62BUnK",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -842.2976236297301,
			"y": 3045.2111577036835,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 1.360727443094106,
			"height": 84.46710774399753,
			"seed": 568769318,
			"groupIds": [
				"RhUvMLAxtc-u9WNRyYozO"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "9tleUbQN"
				}
			],
			"updated": 1692192358625,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "jtoVfliw",
				"focus": 0.08522763519841978,
				"gap": 9.94376833813476
			},
			"endBinding": {
				"elementId": "P1l7AaKG",
				"focus": -0.0514343287900214,
				"gap": 4.588031345844229
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-1.360727443094106,
					84.46710774399753
				]
			]
		},
		{
			"type": "text",
			"version": 96,
			"versionNonce": 791671208,
			"isDeleted": false,
			"id": "9tleUbQN",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -945.9874745368372,
			"y": 3052.829326742395,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 223.45703125,
			"height": 24,
			"seed": 1639146746,
			"groupIds": [
				"RhUvMLAxtc-u9WNRyYozO"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358625,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "有一个15字节的内存请求",
			"rawText": "有一个15字节的内存请求",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "GfglkRtnF6sPXrR62BUnK",
			"originalText": "有一个15字节的内存请求",
			"lineHeight": 1.2,
			"baseline": 20
		},
		{
			"type": "image",
			"version": 175,
			"versionNonce": 289365208,
			"isDeleted": false,
			"id": "AZ6J6eVgjBikO3p7msvb6",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1044.3133422438268,
			"y": 3222.369430645972,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 401.10288448672327,
			"height": 63.76507394404319,
			"seed": 935632806,
			"groupIds": [
				"vhLvgzUymzijFORstmZZt"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "8nKU-HUc3YpyqsE5-f9P3",
					"type": "arrow"
				}
			],
			"updated": 1692192358625,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "7ad283b1c9740c65f79ddf0c29a1c90eab55876d",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "arrow",
			"version": 389,
			"versionNonce": 714308776,
			"isDeleted": false,
			"id": "8nKU-HUc3YpyqsE5-f9P3",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -858.0801745006377,
			"y": 3296.07827292815,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 6.295705638966979,
			"height": 81.01739333570868,
			"seed": 573664806,
			"groupIds": [
				"vhLvgzUymzijFORstmZZt"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "wDdTu4s3"
				}
			],
			"updated": 1692192358625,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "AZ6J6eVgjBikO3p7msvb6",
				"focus": 0.08653206440307536,
				"gap": 9.94376833813476
			},
			"endBinding": {
				"elementId": "24Oe6S2i",
				"focus": -0.03007650741086465,
				"gap": 12.483041384948365
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					6.295705638966979,
					81.01739333570868
				]
			]
		},
		{
			"type": "text",
			"version": 124,
			"versionNonce": 401474008,
			"isDeleted": false,
			"id": "wDdTu4s3",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -969.7223596603035,
			"y": 3326.3118268001485,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 223.45703125,
			"height": 24,
			"seed": 325892454,
			"groupIds": [
				"vhLvgzUymzijFORstmZZt"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358625,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "有一个15字节的内存请求",
			"rawText": "有一个15字节的内存请求",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "8nKU-HUc3YpyqsE5-f9P3",
			"originalText": "有一个15字节的内存请求",
			"lineHeight": 1.2,
			"baseline": 20
		},
		{
			"type": "image",
			"version": 95,
			"versionNonce": 659400616,
			"isDeleted": false,
			"id": "24Oe6S2i",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1050.462966644064,
			"y": 3389.5787076488073,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 417.20711739238527,
			"height": 66.98613403158717,
			"seed": 73511,
			"groupIds": [
				"vhLvgzUymzijFORstmZZt"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "8nKU-HUc3YpyqsE5-f9P3",
					"type": "arrow"
				}
			],
			"updated": 1692192358625,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "d45fc0ee2c4264733677a01eaff1a751e39fa075",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "image",
			"version": 100,
			"versionNonce": 2071987928,
			"isDeleted": false,
			"id": "Lyoa2p8V",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -439.56220420248667,
			"y": 3106.095292700159,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 346.8159891635053,
			"height": 226.66597817565705,
			"seed": 53066,
			"groupIds": [
				"FBD5VbFdGBANqX5xG5zjy"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358625,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "e513217fd720598d5c5cc32bea61835cdf22912a",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "text",
			"version": 250,
			"versionNonce": 162714917,
			"isDeleted": false,
			"id": "3iX0xWbR",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -295.60497039883785,
			"y": 3290.969528427821,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 133.83998107910156,
			"height": 24,
			"seed": 1367369944,
			"groupIds": [
				"FBD5VbFdGBANqX5xG5zjy"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1693060909769,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "请求7KB空间时",
			"rawText": "请求7KB空间时",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "请求7KB空间时",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "image",
			"version": 73,
			"versionNonce": 143223768,
			"isDeleted": false,
			"id": "YlbBv12U",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -43.026674943977355,
			"y": 3114.2657813772953,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 612.114836353003,
			"height": 278.386473519448,
			"seed": 55721,
			"groupIds": [
				"1r5aZTfdCyn8ka54ggHyg"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358625,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "4fcfa8e12ab188ba46a43795a3ca39fe8b6937e1",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "line",
			"version": 53,
			"versionNonce": 804642216,
			"isDeleted": false,
			"id": "lBO1-xl8u_INdeQtfeyTE",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 208.7240772759211,
			"y": 3252.985995253033,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 140.47892591908936,
			"height": 23.181344412911585,
			"seed": 596076200,
			"groupIds": [
				"1r5aZTfdCyn8ka54ggHyg"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358625,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": null,
			"points": [
				[
					0,
					0
				],
				[
					140.47892591908936,
					-23.181344412911585
				]
			]
		},
		{
			"type": "line",
			"version": 44,
			"versionNonce": 1495150808,
			"isDeleted": false,
			"id": "ZlyPIHPcq3x5YgmpCdB_y",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 150.7707162436422,
			"y": 3285.439877431109,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 196.11415251007713,
			"height": 60.27149547356976,
			"seed": 1922166440,
			"groupIds": [
				"1r5aZTfdCyn8ka54ggHyg"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358625,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": null,
			"points": [
				[
					0,
					0
				],
				[
					196.11415251007713,
					60.27149547356976
				]
			]
		},
		{
			"type": "line",
			"version": 51,
			"versionNonce": 1941694632,
			"isDeleted": false,
			"id": "IUb-4MZKEXtz_zekRP6k1",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 152.16157568526222,
			"y": 3314.648385540147,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 189.62340437200146,
			"height": 26.426753853873834,
			"seed": 1986653912,
			"groupIds": [
				"1r5aZTfdCyn8ka54ggHyg"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358625,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": null,
			"points": [
				[
					0,
					0
				],
				[
					189.62340437200146,
					-26.426753853873834
				]
			]
		},
		{
			"type": "line",
			"version": 76,
			"versionNonce": 617764312,
			"isDeleted": false,
			"id": "hgtFYZGCYYWRFv4YpPStx",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 149.37982143009773,
			"y": 3343.856858277261,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 196.5778076958749,
			"height": 139.08804879150694,
			"seed": 1698750936,
			"groupIds": [
				"1r5aZTfdCyn8ka54ggHyg"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358625,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": null,
			"points": [
				[
					0,
					0
				],
				[
					196.5778076958749,
					-139.08804879150694
				]
			]
		},
		{
			"type": "image",
			"version": 155,
			"versionNonce": 143168424,
			"isDeleted": false,
			"id": "NyhdJGp4",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1619.8552850161573,
			"y": -427.18661842995874,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 364.64536233972296,
			"height": 304.9055902117258,
			"seed": 5797,
			"groupIds": [
				"ewA7H2lA2FJDwRhXRAAJF",
				"4dizfF1NTI6_uKnF4uhAN"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "yBkcvpAZ6MHoU0wys4-d4",
					"type": "arrow"
				}
			],
			"updated": 1692192358626,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "227e27e893c2025f22851992d4c40a498cd05475",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "arrow",
			"version": 364,
			"versionNonce": 280615640,
			"isDeleted": false,
			"id": "KvwH-BDLUqWboJ-MfvFO7",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1974.9140410704872,
			"y": -363.22369366839933,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 113.40431957247847,
			"height": 64.64892328510496,
			"seed": 1675957720,
			"groupIds": [
				"ewA7H2lA2FJDwRhXRAAJF",
				"4dizfF1NTI6_uKnF4uhAN"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358626,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "dMBD23zU",
				"focus": 0.13412399595929647,
				"gap": 5.018909011534106
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					113.40431957247847,
					64.64892328510496
				]
			]
		},
		{
			"type": "text",
			"version": 309,
			"versionNonce": 1064057771,
			"isDeleted": false,
			"id": "dMBD23zU",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1975.4559291084415,
			"y": -293.5558613717603,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 278.8399658203125,
			"height": 48,
			"seed": 1114820264,
			"groupIds": [
				"ewA7H2lA2FJDwRhXRAAJF",
				"4dizfF1NTI6_uKnF4uhAN"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "KvwH-BDLUqWboJ-MfvFO7",
					"type": "arrow"
				}
			],
			"updated": 1693060909771,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "由于是64字节的虚拟地址空间，\n所以需要6位",
			"rawText": "由于是64字节的虚拟地址空间，\n所以需要6位",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "由于是64字节的虚拟地址空间，\n所以需要6位",
			"lineHeight": 1.2,
			"baseline": 42
		},
		{
			"type": "arrow",
			"version": 189,
			"versionNonce": 2137571288,
			"isDeleted": false,
			"id": "yBkcvpAZ6MHoU0wys4-d4",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1782.2425731091523,
			"y": -424.17353890487743,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 48.472471920171756,
			"height": 22.620486896080195,
			"seed": 895529176,
			"groupIds": [
				"ewA7H2lA2FJDwRhXRAAJF",
				"4dizfF1NTI6_uKnF4uhAN"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358626,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "ZHuOcDcF",
				"focus": 0.18451550831596003,
				"gap": 5.816657183421626
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					2.585159055410486,
					-16.80379273109702
				],
				[
					48.472471920171756,
					-22.620486896080195
				]
			]
		},
		{
			"type": "text",
			"version": 206,
			"versionNonce": 1766254725,
			"isDeleted": false,
			"id": "ZHuOcDcF",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1836.5317022127458,
			"y": -482.01736032715723,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 288.5599365234375,
			"height": 48,
			"seed": 782269656,
			"groupIds": [
				"ewA7H2lA2FJDwRhXRAAJF",
				"4dizfF1NTI6_uKnF4uhAN"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "yBkcvpAZ6MHoU0wys4-d4",
					"type": "arrow"
				}
			],
			"updated": 1693060909772,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "1页是16字节，我们许需要4个页，\n所以是2位",
			"rawText": "1页是16字节，我们许需要4个页，\n所以是2位",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "1页是16字节，我们许需要4个页，\n所以是2位",
			"lineHeight": 1.2,
			"baseline": 42
		},
		{
			"type": "arrow",
			"version": 212,
			"versionNonce": 1626539224,
			"isDeleted": false,
			"id": "nCGZ4XNP4o1LKfgvFUYdl",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1919.2580740133385,
			"y": -410.601256628979,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 38.13168777228475,
			"height": 1.9388939459320795,
			"seed": 1583278760,
			"groupIds": [
				"ewA7H2lA2FJDwRhXRAAJF",
				"4dizfF1NTI6_uKnF4uhAN"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358626,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "Dv28gwor",
				"focus": 0.18452680405903937,
				"gap": 3.8777385831162974
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					38.13168777228475,
					-1.9388939459320795
				]
			]
		},
		{
			"type": "text",
			"version": 150,
			"versionNonce": 1633521227,
			"isDeleted": false,
			"id": "Dv28gwor",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1961.2675003687395,
			"y": -426.43560238710995,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 188.71995544433594,
			"height": 24,
			"seed": 1998606808,
			"groupIds": [
				"ewA7H2lA2FJDwRhXRAAJF",
				"4dizfF1NTI6_uKnF4uhAN"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "nCGZ4XNP4o1LKfgvFUYdl",
					"type": "arrow"
				}
			],
			"updated": 1693060909773,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "1页是16字节，需要4位",
			"rawText": "1页是16字节，需要4位",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "1页是16字节，需要4位",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 309,
			"versionNonce": 49064408,
			"isDeleted": false,
			"id": "A86kpsAbvTxz0nqyekq-Z",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1718.1376994094767,
			"y": -276.8172291984301,
			"strokeColor": "#e03131",
			"backgroundColor": "#ffffff",
			"width": 46.437126633590196,
			"height": 15.855751288785257,
			"seed": 2142835112,
			"groupIds": [
				"ewA7H2lA2FJDwRhXRAAJF",
				"4dizfF1NTI6_uKnF4uhAN"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192358626,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "EsYfloZR",
				"focus": 0.6580501116564484,
				"gap": 2.3136277446947133
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-46.437126633590196,
					15.855751288785257
				]
			]
		},
		{
			"type": "text",
			"version": 277,
			"versionNonce": 398561253,
			"isDeleted": false,
			"id": "EsYfloZR",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1444.3869602899808,
			"y": -306.7261113885415,
			"strokeColor": "#e03131",
			"backgroundColor": "#ffffff",
			"width": 224.99998474121094,
			"height": 72,
			"seed": 1944320216,
			"groupIds": [
				"4dizfF1NTI6_uKnF4uhAN"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "A86kpsAbvTxz0nqyekq-Z",
					"type": "arrow"
				}
			],
			"updated": 1693060909775,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "通过检索页表，\n查看第1页对应的物理内存\n的页帧是多少",
			"rawText": "通过检索页表，\n查看第1页对应的物理内存\n的页帧是多少",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "通过检索页表，\n查看第1页对应的物理内存\n的页帧是多少",
			"lineHeight": 1.2,
			"baseline": 66
		},
		{
			"type": "image",
			"version": 90,
			"versionNonce": 1617538776,
			"isDeleted": false,
			"id": "Q6jjbvYN",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 1491.2608914929112,
			"y": -104.47430366536832,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 217.64110467758343,
			"height": 243.07967535418408,
			"seed": 65462,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192358626,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "1bf3b5ac9073f798754998ea32c44112d213a3d0",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "image",
			"version": 220,
			"versionNonce": 1917624792,
			"isDeleted": false,
			"id": "3G7VkHW3",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 2080.6911542782623,
			"y": -39.05438705280753,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 211.03792151880177,
			"height": 97.11479574316542,
			"seed": 25613,
			"groupIds": [
				"txqf_cfM8xTb9CPju8JVs"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "LHtEVoZfCqqt6GJoGhvka",
					"type": "arrow"
				}
			],
			"updated": 1692192490514,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "45dd7c8c8ca8e96b0ddfcbd0628c42bec2a91b9b",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "image",
			"version": 635,
			"versionNonce": 531171240,
			"isDeleted": false,
			"id": "Bc4AZkrD",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 2084.4981530226437,
			"y": 171.04284013418035,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 197.2521827497992,
			"height": 76.0679960072364,
			"seed": 96447,
			"groupIds": [
				"txqf_cfM8xTb9CPju8JVs"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "LHtEVoZfCqqt6GJoGhvka",
					"type": "arrow"
				},
				{
					"id": "4_YcWsn9_WhgV4aRhUO-O",
					"type": "arrow"
				}
			],
			"updated": 1692192490514,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "557466c35827834b1f191decd741a931d15faef9",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "arrow",
			"version": 1485,
			"versionNonce": 1359652568,
			"isDeleted": false,
			"id": "LHtEVoZfCqqt6GJoGhvka",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 2175.431290044426,
			"y": 68.44640310971135,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 0.39446361936961694,
			"height": 95.56003509299086,
			"seed": 1279313368,
			"groupIds": [
				"txqf_cfM8xTb9CPju8JVs"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "NZXMgOdr"
				}
			],
			"updated": 1692192490514,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "3G7VkHW3",
				"gap": 10.385994419353466,
				"focus": 0.10394430454489059
			},
			"endBinding": {
				"elementId": "Bc4AZkrD",
				"gap": 7.036401931478153,
				"focus": -0.07200062091895625
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					0.39446361936961694,
					95.56003509299086
				]
			]
		},
		{
			"type": "text",
			"version": 183,
			"versionNonce": 393859752,
			"isDeleted": false,
			"id": "NZXMgOdr",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 2074.654431815736,
			"y": 136.99279391022614,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 140,
			"height": 24,
			"seed": 1443017384,
			"groupIds": [
				"txqf_cfM8xTb9CPju8JVs"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1692192490514,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "转换成汇编语言",
			"rawText": "转换成汇编语言",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "LHtEVoZfCqqt6GJoGhvka",
			"originalText": "转换成汇编语言",
			"lineHeight": 1.2,
			"baseline": 20
		},
		{
			"type": "arrow",
			"version": 1636,
			"versionNonce": 331353048,
			"isDeleted": false,
			"id": "4_YcWsn9_WhgV4aRhUO-O",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 2291.977003750818,
			"y": 203.92521942643955,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 71.78047278405029,
			"height": 25.22830571693271,
			"seed": 990434008,
			"groupIds": [
				"txqf_cfM8xTb9CPju8JVs"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192490514,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "Bc4AZkrD",
				"focus": 0.45512948658576247,
				"gap": 10.226667978374962
			},
			"endBinding": {
				"elementId": "5pvr5y2J",
				"focus": -0.11704318811249301,
				"gap": 15.448866498451935
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					71.78047278405029,
					-25.22830571693271
				]
			]
		},
		{
			"type": "text",
			"version": 1191,
			"versionNonce": 1791724779,
			"isDeleted": false,
			"id": "0SqMivvV",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 2279.3436663494176,
			"y": 279.5083368303398,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 283.46820068359375,
			"height": 79.4890877622247,
			"seed": 647095976,
			"groupIds": [
				"txqf_cfM8xTb9CPju8JVs"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "JKGrnwa6LKdoIZ3il0qYD",
					"type": "arrow"
				}
			],
			"updated": 1693060909779,
			"link": null,
			"locked": false,
			"fontSize": 13.248181293704118,
			"fontFamily": 4,
			"text": "一次循环，\n有10次内存访问【\n取指令4次，\n更新数组内容1次，\n为取指令和更新数组内容转换地址访问页表5次】",
			"rawText": "一次循环，\n有10次内存访问【\n取指令4次，\n更新数组内容1次，\n为取指令和更新数组内容转换地址访问页表5次】",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "一次循环，\n有10次内存访问【\n取指令4次，\n更新数组内容1次，\n为取指令和更新数组内容转换地址访问页表5次】",
			"lineHeight": 1.2,
			"baseline": 75
		},
		{
			"type": "image",
			"version": 412,
			"versionNonce": 75550936,
			"isDeleted": false,
			"id": "5pvr5y2J",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 2379.20634303332,
			"y": -53.17181115926749,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 361.44930416568036,
			"height": 278.3889842690215,
			"seed": 5419,
			"groupIds": [
				"6-Zm2Ra9OVMK1oVHZ98S7",
				"txqf_cfM8xTb9CPju8JVs"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "4_YcWsn9_WhgV4aRhUO-O",
					"type": "arrow"
				},
				{
					"id": "cBfoQQYQbSL_yq26lBiMk",
					"type": "arrow"
				}
			],
			"updated": 1692192490514,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "57a567fe869705a49cc0f28cf46c2ae21a97f3fe",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "line",
			"version": 495,
			"versionNonce": 491997352,
			"isDeleted": false,
			"id": "hoivPejNACqIIkojnCMRE",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 2494.1488332392464,
			"y": 214.3565518199421,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 2.9503949166737584,
			"height": 247.83459393524163,
			"seed": 477264088,
			"groupIds": [
				"6-Zm2Ra9OVMK1oVHZ98S7",
				"txqf_cfM8xTb9CPju8JVs"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192490514,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": null,
			"points": [
				[
					0,
					0
				],
				[
					-2.9503949166737584,
					-247.83459393524163
				]
			]
		},
		{
			"type": "arrow",
			"version": 982,
			"versionNonce": 182515160,
			"isDeleted": false,
			"id": "cBfoQQYQbSL_yq26lBiMk",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 2430.600229558321,
			"y": 200.6670554332799,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 49.705282409674965,
			"height": 24.84114370910777,
			"seed": 1565613224,
			"groupIds": [
				"6-Zm2Ra9OVMK1oVHZ98S7",
				"txqf_cfM8xTb9CPju8JVs"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192490514,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "jAeC0Mnb",
				"focus": -0.41050929111424517,
				"gap": 2.06408405599295
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					1.1886730566943697,
					11.886609650094528
				],
				[
					-48.516609352980595,
					24.84114370910777
				]
			]
		},
		{
			"type": "text",
			"version": 725,
			"versionNonce": 590367557,
			"isDeleted": false,
			"id": "jAeC0Mnb",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 2332.83222851997,
			"y": 227.5722831983806,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 84.60823059082031,
			"height": 14.496142144304223,
			"seed": 1503032536,
			"groupIds": [
				"6-Zm2Ra9OVMK1oVHZ98S7",
				"txqf_cfM8xTb9CPju8JVs"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "cBfoQQYQbSL_yq26lBiMk",
					"type": "arrow"
				}
			],
			"updated": 1693060909781,
			"link": null,
			"locked": false,
			"fontSize": 12.080118453586852,
			"fontFamily": 4,
			"text": "左侧是虚拟地址",
			"rawText": "左侧是虚拟地址",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "左侧是虚拟地址",
			"lineHeight": 1.2,
			"baseline": 10
		},
		{
			"type": "arrow",
			"version": 845,
			"versionNonce": 2079619800,
			"isDeleted": false,
			"id": "IwZR2WPkVSB3XPQnF1BAs",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 2700.1538671443186,
			"y": 199.15647150275606,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 23.513589318938557,
			"height": 27.01666887975378,
			"seed": 715053784,
			"groupIds": [
				"6-Zm2Ra9OVMK1oVHZ98S7",
				"txqf_cfM8xTb9CPju8JVs"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192490514,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "FXFMavz5",
				"focus": 0.6076702970939758,
				"gap": 4.423176970079055
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					15.452598590965408,
					9.905508041745406
				],
				[
					-8.060990727973149,
					27.01666887975378
				]
			]
		},
		{
			"type": "text",
			"version": 540,
			"versionNonce": 524334987,
			"isDeleted": false,
			"id": "FXFMavz5",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 2590.7003711695606,
			"y": 230.5963173525889,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 100.21443176269531,
			"height": 13.360847137112776,
			"seed": 354864040,
			"groupIds": [
				"6-Zm2Ra9OVMK1oVHZ98S7",
				"txqf_cfM8xTb9CPju8JVs"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "IwZR2WPkVSB3XPQnF1BAs",
					"type": "arrow"
				}
			],
			"updated": 1693060909783,
			"link": null,
			"locked": false,
			"fontSize": 11.134039280927313,
			"fontFamily": 4,
			"text": "右侧是实际物理地址",
			"rawText": "右侧是实际物理地址",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "右侧是实际物理地址",
			"lineHeight": 1.2,
			"baseline": 10
		},
		{
			"type": "arrow",
			"version": 41,
			"versionNonce": 1783586776,
			"isDeleted": false,
			"id": "7pk5ClFBQ3XqIxKyzkbeW",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 2444.91233741617,
			"y": 212.52654912194876,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 49.13475320091766,
			"height": 1.056686064339658,
			"seed": 1621834664,
			"groupIds": [
				"txqf_cfM8xTb9CPju8JVs"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192490514,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					49.13475320091766,
					1.056686064339658
				]
			]
		},
		{
			"type": "line",
			"version": 42,
			"versionNonce": 750332328,
			"isDeleted": false,
			"id": "sqxRhIFIfL6A437lDrJ9H",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 2453.8939472665725,
			"y": 208.82824866788948,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 9.50993272834603,
			"height": 15.321605311084625,
			"seed": 258201512,
			"groupIds": [
				"txqf_cfM8xTb9CPju8JVs"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192490514,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": null,
			"points": [
				[
					0,
					0
				],
				[
					-6.868278030174679,
					5.811632274286808
				],
				[
					2.641654698171351,
					15.321605311084625
				]
			]
		},
		{
			"type": "arrow",
			"version": 133,
			"versionNonce": 1980081368,
			"isDeleted": false,
			"id": "JKGrnwa6LKdoIZ3il0qYD",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 2462.3472342390305,
			"y": 213.58323518628842,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "#ffffff",
			"width": 55.188466787169546,
			"height": 56.271479354971035,
			"seed": 1398405848,
			"groupIds": [
				"txqf_cfM8xTb9CPju8JVs"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1692192490514,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "0SqMivvV",
				"focus": -0.3451118191090806,
				"gap": 9.653622289080317
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-55.188466787169546,
					56.271479354971035
				]
			]
		}
	],
	"appState": {
		"theme": "light",
		"viewBackgroundColor": "#ffffff",
		"currentItemStrokeColor": "#1e1e1e",
		"currentItemBackgroundColor": "#ffffff",
		"currentItemFillStyle": "hachure",
		"currentItemStrokeWidth": 1,
		"currentItemStrokeStyle": "solid",
		"currentItemRoughness": 1,
		"currentItemOpacity": 100,
		"currentItemFontFamily": 4,
		"currentItemFontSize": 20,
		"currentItemTextAlign": "left",
		"currentItemStartArrowhead": null,
		"currentItemEndArrowhead": "arrow",
		"scrollX": 4377.831214649464,
		"scrollY": 1259.3929259900476,
		"zoom": {
			"value": 0.15000000000000002
		},
		"currentItemRoundness": "round",
		"gridSize": null,
		"currentStrokeOptions": null,
		"previousGridSize": null,
		"frameRendering": {
			"enabled": true,
			"clip": true,
			"name": true,
			"outline": true
		}
	},
	"files": {}
}
```
%%