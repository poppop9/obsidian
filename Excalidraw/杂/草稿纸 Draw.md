---

excalidraw-plugin: parsed
tags: [excalidraw]

---
==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠==


# Text Elements
内核态 ^RkkZ35Xu

用户态 ^ip3SfnHq

通过中断 ^gIHYhFdL

【硬件实现】 ^j611qUUj

通过特权指令 ^buUX6LiZ

内存中一次只能有两个进程 ^xfXd1eco

外存 ^8TGV6ZCw

内存 ^8Ukf8NSF

作业 ^aRXPaxlT

…… ^ZHDFo9us

进程1 ^D8wa35t0

进程2 ^1MKM1Fy2

CPU ^wdKBh90W

前提条件：
- 互斥信号量mutex，初始值为1
- empty为可使用的缓冲区数，初始值为n
- full为缓冲区内的产品数，初始值为0 ^UUWyKE73

只能分配给P0 ^5hsUN1ul

P0运行完后，需要归还已分配的资源
0 0 1 0 ^g2EqVbJq

所以可使用资源为2 4 4 1 ^VH8VYxsT

又只能够给P3提供 ^ia5FYkmt

…… ^soKqDiJ4

能找到序列为P0 P3 P4 P2 P1 ^e9dbQ5JL

只要能找到一个序列那就是安全的 ^jsleP9HS

说明尚需资源为0 10 7 2 ^5U1QKuoi

OPT: ^sjVGRUct

首先是2 3 1 进来了 ^u1FPTyIv

，2再进来了更新了原来的2，还是2 3 1，4进来，
3在后面要使用，2也要使用，所以淘汰1 ^AS2Z5zlN

FIFO: ^9ZF6Ahq9

4进来，那就淘汰最先进来的2 ^DcJpZnSJ

LRU: ^ZbcQ1bPp

2进来了，说明2使用了，4再进来，那就是3最久未使用，淘汰3 ^UixQAajl

2进来,块里没有2,
所以缺页 ^0ECahKRF

块里有2,所以不缺页 ^CUZ9gWMV

FCFS: ^kXjgrfO6

65到了就先从110移动到65，
然后再从65移动到68 ^UmbkbDQU

把移动的距离相加/移动的次数 ^Es8VMBLB

SSTF: ^do8UtMr8

110先到100，从100到68…… ^n2626deA

SCAN： ^7zMC1cGp

从110到160，再到170，再到194 ^avt4HuLj

再回去扫描100…… ^z2VSILIa

循环SCAN： ^LrxTWLfo

从110到160，再到170，再到194 ^LlrhoyQv

再到28，48…… ^a24n4JZR

客户端 ^lUKjFdyx

request ^mzGIOjNQ

response ^6ZhaS3ef

Servlet容器 ^nw1fXlc6

init()方法 ^hNBugFyE

service方法 ^kYo8j9A8

destroy方法 ^ndwy8y1j


# Embedded files
5da0c3aa0de4c7df4efcca15e0985a71085136f0: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240102163106.png
994562a6fef2ce98da3aeb82cfeba8d3501ca650: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240104224727.png
85d4ccb0a76bd2fd92092b1cfdd67101f1d671f1: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240104235700.png
a041a9e831914c2ddb555c4f0ebea45d6ce8d1a3: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240105105116.png
e1da97656258e1f8031b3dec765b6b218b788c4f: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240106132849.png
83dfcdad93975a5487f5d426f4d62ba754dc022b: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240106133632.png
d696d0f843efdf94f24b086030b9bfe87fc3a293: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240106223113.png
03680fe1d28f617aa1faf37271b950a2d32d434b: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111214055.png

%%
# Drawing
```json
{
	"type": "excalidraw",
	"version": 2,
	"source": "https://github.com/zsviczian/obsidian-excalidraw-plugin/releases/tag/2.0.17",
	"elements": [
		{
			"type": "rectangle",
			"version": 146,
			"versionNonce": 131885364,
			"isDeleted": false,
			"id": "9teYO3aieP3l4HsTksjkX",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -592.3579112242378,
			"y": -330.31248324791807,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 80.80003138950894,
			"height": 45.0285557338171,
			"seed": 2055551801,
			"groupIds": [
				"qx4T7IaayHInFrYxXCYYg"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [
				{
					"type": "text",
					"id": "RkkZ35Xu"
				},
				{
					"id": "05OXV3LLHobliFHQeLH2x",
					"type": "arrow"
				},
				{
					"id": "d2fd4suquYu5J1moE3Lcv",
					"type": "arrow"
				}
			],
			"updated": 1704551663325,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 146,
			"versionNonce": 2075776469,
			"isDeleted": false,
			"id": "RkkZ35Xu",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -581.9578955294833,
			"y": -319.7982053810095,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 60,
			"height": 24,
			"seed": 1432515481,
			"groupIds": [
				"qx4T7IaayHInFrYxXCYYg"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705286752214,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "内核态",
			"rawText": "内核态",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "9teYO3aieP3l4HsTksjkX",
			"originalText": "内核态",
			"lineHeight": 1.2,
			"baseline": 20
		},
		{
			"type": "rectangle",
			"version": 79,
			"versionNonce": 945889972,
			"isDeleted": false,
			"id": "PTPIghP7Guh-OSA3kilGE",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -268.9220293164318,
			"y": -334.959131277738,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 80.800048828125,
			"height": 44,
			"seed": 1728472441,
			"groupIds": [
				"qx4T7IaayHInFrYxXCYYg"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [
				{
					"type": "text",
					"id": "ip3SfnHq"
				},
				{
					"id": "05OXV3LLHobliFHQeLH2x",
					"type": "arrow"
				},
				{
					"id": "d2fd4suquYu5J1moE3Lcv",
					"type": "arrow"
				}
			],
			"updated": 1704551663325,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 66,
			"versionNonce": 47222965,
			"isDeleted": false,
			"id": "ip3SfnHq",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -258.5220049023693,
			"y": -324.959131277738,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 60,
			"height": 24,
			"seed": 1213099577,
			"groupIds": [
				"qx4T7IaayHInFrYxXCYYg"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705286752215,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "用户态",
			"rawText": "用户态",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "PTPIghP7Guh-OSA3kilGE",
			"originalText": "用户态",
			"lineHeight": 1.2,
			"baseline": 20
		},
		{
			"type": "arrow",
			"version": 366,
			"versionNonce": 769469157,
			"isDeleted": false,
			"id": "05OXV3LLHobliFHQeLH2x",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -502.66116802563386,
			"y": -316.4014516980084,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 226.53918753732705,
			"height": 7.332379697347051,
			"seed": 709204375,
			"groupIds": [
				"qx4T7IaayHInFrYxXCYYg"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1705369823748,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "9teYO3aieP3l4HsTksjkX",
				"gap": 8.896711809094938,
				"focus": -0.2941688717816047
			},
			"endBinding": {
				"elementId": "PTPIghP7Guh-OSA3kilGE",
				"gap": 7.199951171875,
				"focus": 0.5283835446480676
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
					226.53918753732705,
					-7.332379697347051
				]
			]
		},
		{
			"type": "text",
			"version": 110,
			"versionNonce": 1686648293,
			"isDeleted": false,
			"id": "gIHYhFdL",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -499.32199269533805,
			"y": -356.5591068636754,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 80,
			"height": 24,
			"seed": 258978905,
			"groupIds": [
				"qx4T7IaayHInFrYxXCYYg"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "05OXV3LLHobliFHQeLH2x",
					"type": "arrow"
				}
			],
			"updated": 1705369823897,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "通过中断",
			"rawText": "通过中断",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "通过中断",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "text",
			"version": 138,
			"versionNonce": 799688427,
			"isDeleted": false,
			"id": "j611qUUj",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -417.5220049023693,
			"y": -353.296353481255,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 102.16656494140625,
			"height": 20.75073143548313,
			"seed": 2002374199,
			"groupIds": [
				"qx4T7IaayHInFrYxXCYYg"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823899,
			"link": null,
			"locked": false,
			"fontSize": 17.292276196235942,
			"fontFamily": 4,
			"text": "【硬件实现】",
			"rawText": "【硬件实现】",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "【硬件实现】",
			"lineHeight": 1.2,
			"baseline": 14
		},
		{
			"type": "arrow",
			"version": 306,
			"versionNonce": 237073829,
			"isDeleted": false,
			"id": "d2fd4suquYu5J1moE3Lcv",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -273.72201710940055,
			"y": -303.75911907070673,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 231.19995117187494,
			"height": 0,
			"seed": 263879641,
			"groupIds": [
				"qx4T7IaayHInFrYxXCYYg"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1705369823748,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "PTPIghP7Guh-OSA3kilGE",
				"gap": 4.79998779296875,
				"focus": -0.418182373046875
			},
			"endBinding": {
				"elementId": "9teYO3aieP3l4HsTksjkX",
				"gap": 6.6359115534532975,
				"focus": 0.17940110423170466
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
					-231.19995117187494,
					0
				]
			]
		},
		{
			"type": "text",
			"version": 86,
			"versionNonce": 741486917,
			"isDeleted": false,
			"id": "buUX6LiZ",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -451.3220537304943,
			"y": -294.15914348476923,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 120,
			"height": 24,
			"seed": 1836028281,
			"groupIds": [
				"qx4T7IaayHInFrYxXCYYg"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823901,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "通过特权指令",
			"rawText": "通过特权指令",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "通过特权指令",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "image",
			"version": 48,
			"versionNonce": 1211141644,
			"isDeleted": false,
			"id": "iKBUfos2",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -760.2899031316629,
			"y": -181.22721526579937,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 500.00000000000006,
			"height": 207.03611457036115,
			"seed": 48117,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1704551663325,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "5da0c3aa0de4c7df4efcca15e0985a71085136f0",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "image",
			"version": 298,
			"versionNonce": 2070948020,
			"isDeleted": false,
			"id": "cB0t9FWX",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -833.843511237475,
			"y": 178.77781133347744,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 663.2000122070312,
			"height": 321.2733623148248,
			"seed": 77994,
			"groupIds": [
				"fNxzE4LOutlibQuXdoLKT",
				"DWOkBI9BjiVhmj2Tcibzi"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "kcRBsZx9COg3l23aTkztu",
					"type": "arrow"
				}
			],
			"updated": 1704551663325,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "994562a6fef2ce98da3aeb82cfeba8d3501ca650",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "line",
			"version": 268,
			"versionNonce": 1368059020,
			"isDeleted": false,
			"id": "Zsrer4-qthUhVp-tKFkel",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -725.4102940621817,
			"y": 210.7536800030967,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 190.3383832641598,
			"height": 1.3264050842286088,
			"seed": 1252763148,
			"groupIds": [
				"fNxzE4LOutlibQuXdoLKT",
				"DWOkBI9BjiVhmj2Tcibzi"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1704551663325,
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
					190.3383832641598,
					1.3264050842286088
				]
			]
		},
		{
			"type": "text",
			"version": 330,
			"versionNonce": 205009291,
			"isDeleted": false,
			"id": "xfXd1eco",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -771.9669227755604,
			"y": 148.51237504887337,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 318.29290771484375,
			"height": 31.8336005859375,
			"seed": 1099749556,
			"groupIds": [
				"fNxzE4LOutlibQuXdoLKT",
				"DWOkBI9BjiVhmj2Tcibzi"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823904,
			"link": null,
			"locked": false,
			"fontSize": 26.52800048828125,
			"fontFamily": 4,
			"text": "内存中一次只能有两个进程",
			"rawText": "内存中一次只能有两个进程",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "内存中一次只能有两个进程",
			"lineHeight": 1.2,
			"baseline": 22
		},
		{
			"type": "text",
			"version": 105,
			"versionNonce": 398835877,
			"isDeleted": false,
			"id": "8TGV6ZCw",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -221.69342960295353,
			"y": 255.39366834568733,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 40,
			"height": 24,
			"seed": 1553704372,
			"groupIds": [
				"VLNIQQmgGfXHq3xJjrX9W",
				"DWOkBI9BjiVhmj2Tcibzi"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823905,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "外存",
			"rawText": "外存",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "外存",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "text",
			"version": 107,
			"versionNonce": 15714347,
			"isDeleted": false,
			"id": "8Ukf8NSF",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -96.69342960295353,
			"y": 255.19365613865608,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 40.03999328613281,
			"height": 24,
			"seed": 12762636,
			"groupIds": [
				"VLNIQQmgGfXHq3xJjrX9W",
				"DWOkBI9BjiVhmj2Tcibzi"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823906,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "内存",
			"rawText": "内存",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "内存",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "rectangle",
			"version": 146,
			"versionNonce": 88750476,
			"isDeleted": false,
			"id": "bUMlh3q4R5IGtGrTxlj9x",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -240.29346622404728,
			"y": 291.1936866562342,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 96.79998779296875,
			"height": 194.4000244140625,
			"seed": 2103785868,
			"groupIds": [
				"VLNIQQmgGfXHq3xJjrX9W",
				"DWOkBI9BjiVhmj2Tcibzi"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [
				{
					"type": "text",
					"id": "ZHDFo9us"
				}
			],
			"updated": 1704551663325,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 97,
			"versionNonce": 761339011,
			"isDeleted": false,
			"id": "ZHDFo9us",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -206.5516754525629,
			"y": 376.39369886326546,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 29.31640625,
			"height": 24,
			"seed": 1630199860,
			"groupIds": [
				"VLNIQQmgGfXHq3xJjrX9W",
				"DWOkBI9BjiVhmj2Tcibzi"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705326387736,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "……",
			"rawText": "……",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "bUMlh3q4R5IGtGrTxlj9x",
			"originalText": "……",
			"lineHeight": 1.2,
			"baseline": 20
		},
		{
			"type": "text",
			"version": 122,
			"versionNonce": 485516293,
			"isDeleted": false,
			"id": "aRXPaxlT",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -229.09339298185978,
			"y": 300.7936622421717,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 40,
			"height": 24,
			"seed": 1423628684,
			"groupIds": [
				"VLNIQQmgGfXHq3xJjrX9W",
				"DWOkBI9BjiVhmj2Tcibzi"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823908,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "作业",
			"rawText": "作业",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "作业",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 165,
			"versionNonce": 869019316,
			"isDeleted": false,
			"id": "kcRBsZx9COg3l23aTkztu",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -165.89344180998478,
			"y": 388.7936622421717,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 60.79998779296875,
			"height": 24.800018310546875,
			"seed": 1316346380,
			"groupIds": [
				"VLNIQQmgGfXHq3xJjrX9W",
				"DWOkBI9BjiVhmj2Tcibzi"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1704551663325,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "cB0t9FWX",
				"focus": 0.6305442975158895,
				"gap": 4.750057220458984
			},
			"endBinding": {
				"elementId": "1MKM1Fy2",
				"focus": 0.7683716425294285,
				"gap": 4.540000915527344
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
					60.79998779296875,
					-24.800018310546875
				]
			]
		},
		{
			"type": "rectangle",
			"version": 168,
			"versionNonce": 1633306252,
			"isDeleted": false,
			"id": "WgdsDqyXzqgN8dpv0Cglc",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -105.89344180998478,
			"y": 287.99364393162483,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 70.4000244140625,
			"height": 119.20004272460938,
			"seed": 1856886156,
			"groupIds": [
				"VLNIQQmgGfXHq3xJjrX9W",
				"DWOkBI9BjiVhmj2Tcibzi"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [
				{
					"id": "z-FwEgYVz83LACG0dhaKg",
					"type": "arrow"
				}
			],
			"updated": 1704551663325,
			"link": null,
			"locked": false
		},
		{
			"type": "line",
			"version": 76,
			"versionNonce": 758921268,
			"isDeleted": false,
			"id": "njT4PF7Eddg2drpAFa9sQ",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -105.09345401701603,
			"y": 347.1936561386561,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 70.4000244140625,
			"height": 0.79998779296875,
			"seed": 711398540,
			"groupIds": [
				"VLNIQQmgGfXHq3xJjrX9W",
				"DWOkBI9BjiVhmj2Tcibzi"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1704551663326,
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
					70.4000244140625,
					0.79998779296875
				]
			]
		},
		{
			"type": "text",
			"version": 121,
			"versionNonce": 867928779,
			"isDeleted": false,
			"id": "D8wa35t0",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -99.69349063810978,
			"y": 293.3936378281092,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 44.91999816894531,
			"height": 24,
			"seed": 1964372236,
			"groupIds": [
				"VLNIQQmgGfXHq3xJjrX9W",
				"DWOkBI9BjiVhmj2Tcibzi"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823909,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "进程1",
			"rawText": "进程1",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "进程1",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "text",
			"version": 134,
			"versionNonce": 531602277,
			"isDeleted": false,
			"id": "1MKM1Fy2",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -100.55345310148869,
			"y": 356.99364393162483,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 50.13999938964844,
			"height": 24,
			"seed": 506083636,
			"groupIds": [
				"VLNIQQmgGfXHq3xJjrX9W",
				"DWOkBI9BjiVhmj2Tcibzi"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "kcRBsZx9COg3l23aTkztu",
					"type": "arrow"
				}
			],
			"updated": 1705369823909,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "进程2",
			"rawText": "进程2",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "进程2",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 94,
			"versionNonce": 411767692,
			"isDeleted": false,
			"id": "z-FwEgYVz83LACG0dhaKg",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -33.09345401701603,
			"y": 348.31618518926086,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 42.4000244140625,
			"height": 21.357125361405963,
			"seed": 911400756,
			"groupIds": [
				"DWOkBI9BjiVhmj2Tcibzi"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1704551663326,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "WgdsDqyXzqgN8dpv0Cglc",
				"focus": 0.25425730072447383,
				"gap": 2.39996337890625
			},
			"endBinding": {
				"elementId": "ovxI1QvFM8SI_UvBG9PwT",
				"focus": 0.3318844617472531,
				"gap": 6.39996337890625
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
					42.4000244140625,
					-21.357125361405963
				]
			]
		},
		{
			"type": "text",
			"version": 52,
			"versionNonce": 691403115,
			"isDeleted": false,
			"id": "wdKBh90W",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 23.70659481110897,
			"y": 262.1936561386561,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 36.77998352050781,
			"height": 24,
			"seed": 236852236,
			"groupIds": [
				"DWOkBI9BjiVhmj2Tcibzi"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823910,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "CPU",
			"rawText": "CPU",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "CPU",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "rectangle",
			"version": 61,
			"versionNonce": 259572236,
			"isDeleted": false,
			"id": "ovxI1QvFM8SI_UvBG9PwT",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 15.706533775952721,
			"y": 294.39366834568733,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 63.20001220703125,
			"height": 56,
			"seed": 175786508,
			"groupIds": [
				"DWOkBI9BjiVhmj2Tcibzi"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [
				{
					"id": "z-FwEgYVz83LACG0dhaKg",
					"type": "arrow"
				}
			],
			"updated": 1704551663326,
			"link": null,
			"locked": false
		},
		{
			"type": "image",
			"version": 15,
			"versionNonce": 1391801524,
			"isDeleted": false,
			"id": "LG0LVtMH",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -783.0816526900398,
			"y": 580.8866430433081,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 500.00000000000006,
			"height": 84.9264705882353,
			"seed": 81453,
			"groupIds": [
				"TAVIDZQqYhkMlFTAAaGCc"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1704551663326,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "85d4ccb0a76bd2fd92092b1cfdd67101f1d671f1",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "text",
			"version": 284,
			"versionNonce": 676390597,
			"isDeleted": false,
			"id": "UUWyKE73",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -777.0815916548836,
			"y": 676.1498050952383,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 296.2608337402344,
			"height": 79.12509714461878,
			"seed": 35736460,
			"groupIds": [
				"TAVIDZQqYhkMlFTAAaGCc"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823915,
			"link": null,
			"locked": false,
			"fontSize": 16.484395238462245,
			"fontFamily": 4,
			"text": "前提条件：\n- 互斥信号量mutex，初始值为1\n- empty为可使用的缓冲区数，初始值为n\n- full为缓冲区内的产品数，初始值为0",
			"rawText": "前提条件：\n- 互斥信号量mutex，初始值为1\n- empty为可使用的缓冲区数，初始值为n\n- full为缓冲区内的产品数，初始值为0",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "前提条件：\n- 互斥信号量mutex，初始值为1\n- empty为可使用的缓冲区数，初始值为n\n- full为缓冲区内的产品数，初始值为0",
			"lineHeight": 1.2,
			"baseline": 73
		},
		{
			"type": "rectangle",
			"version": 58,
			"versionNonce": 1297382964,
			"isDeleted": false,
			"id": "i1AZN7Umoi1EtlOgKdh_G",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -784.6816893111336,
			"y": 670.5498295093008,
			"strokeColor": "#2f9e44",
			"backgroundColor": "transparent",
			"width": 316.00006103515625,
			"height": 93.60000610351562,
			"seed": 1353319180,
			"groupIds": [
				"TAVIDZQqYhkMlFTAAaGCc"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [],
			"updated": 1704551663326,
			"link": null,
			"locked": false
		},
		{
			"type": "image",
			"version": 98,
			"versionNonce": 1054912268,
			"isDeleted": false,
			"id": "SH8nIZot",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -803.3482339074877,
			"y": 819.8496294021068,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 500,
			"height": 263.8004246284501,
			"seed": 58942,
			"groupIds": [
				"pJhYtQozk1mGvh9jWLyDR",
				"vUXmo-KAVbr87GIdP808J",
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "d3_ei2rLurAMR87tsfboQ",
					"type": "arrow"
				},
				{
					"id": "-FbZrOp4qzGLSH4YnrZkF",
					"type": "arrow"
				},
				{
					"id": "Xo3W8kyCHj4vCU-nLEUYz",
					"type": "arrow"
				},
				{
					"id": "osewX_0_WsUQ-OIerGzXX",
					"type": "arrow"
				},
				{
					"id": "dEgKcouQ9QLVgNg7F31-9",
					"type": "arrow"
				}
			],
			"updated": 1704551663326,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "a041a9e831914c2ddb555c4f0ebea45d6ce8d1a3",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "rectangle",
			"version": 75,
			"versionNonce": 537827252,
			"isDeleted": false,
			"id": "gDph_aKFLSjG5LeJEeNo_",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -406.9482705285815,
			"y": 871.74987223391,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 80.79998779296875,
			"height": 20.79998779296875,
			"seed": 377029004,
			"groupIds": [
				"pJhYtQozk1mGvh9jWLyDR",
				"vUXmo-KAVbr87GIdP808J",
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [],
			"updated": 1704551663326,
			"link": null,
			"locked": false
		},
		{
			"type": "arrow",
			"version": 328,
			"versionNonce": 529460620,
			"isDeleted": false,
			"id": "d3_ei2rLurAMR87tsfboQ",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -329.348294942644,
			"y": 890.1498661303943,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 40.800048828125,
			"height": 10.399993896484375,
			"seed": 448408204,
			"groupIds": [
				"pJhYtQozk1mGvh9jWLyDR",
				"vUXmo-KAVbr87GIdP808J",
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1704551663326,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "5hsUN1ul",
				"focus": -0.2537231413493035,
				"gap": 1.39996337890625
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
					40.800048828125,
					10.399993896484375
				]
			]
		},
		{
			"type": "text",
			"version": 146,
			"versionNonce": 1856607243,
			"isDeleted": false,
			"id": "5hsUN1ul",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -287.1482827356127,
			"y": 897.3498478198475,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 120.77998352050781,
			"height": 24,
			"seed": 1500752948,
			"groupIds": [
				"pJhYtQozk1mGvh9jWLyDR",
				"vUXmo-KAVbr87GIdP808J",
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "CfbD0S_UrMZDCR1z4O5en",
					"type": "arrow"
				},
				{
					"id": "d3_ei2rLurAMR87tsfboQ",
					"type": "arrow"
				}
			],
			"updated": 1705369823916,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "只能分配给P0",
			"rawText": "只能分配给P0",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "只能分配给P0",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 596,
			"versionNonce": 2096192524,
			"isDeleted": false,
			"id": "CfbD0S_UrMZDCR1z4O5en",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -222.14828273561272,
			"y": 927.74987223391,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 8.7999267578125,
			"height": 26.399993896484375,
			"seed": 350793780,
			"groupIds": [
				"pJhYtQozk1mGvh9jWLyDR",
				"vUXmo-KAVbr87GIdP808J",
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1704551663326,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "5hsUN1ul",
				"focus": -0.16684744302811927,
				"gap": 6.4000244140625
			},
			"endBinding": {
				"elementId": "g2EqVbJq",
				"focus": -0.5563200705200014,
				"gap": 6.399993896484375
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
					-8.7999267578125,
					26.399993896484375
				]
			]
		},
		{
			"type": "text",
			"version": 168,
			"versionNonce": 1500628517,
			"isDeleted": false,
			"id": "g2EqVbJq",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -307.7483803918627,
			"y": 960.5498600268787,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 320.5799560546875,
			"height": 48,
			"seed": 175640716,
			"groupIds": [
				"pJhYtQozk1mGvh9jWLyDR",
				"vUXmo-KAVbr87GIdP808J",
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "CfbD0S_UrMZDCR1z4O5en",
					"type": "arrow"
				},
				{
					"id": "-FbZrOp4qzGLSH4YnrZkF",
					"type": "arrow"
				}
			],
			"updated": 1705369823919,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "P0运行完后，需要归还已分配的资源\n0 0 1 0",
			"rawText": "P0运行完后，需要归还已分配的资源\n0 0 1 0",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "P0运行完后，需要归还已分配的资源\n0 0 1 0",
			"lineHeight": 1.2,
			"baseline": 42
		},
		{
			"type": "arrow",
			"version": 611,
			"versionNonce": 285342348,
			"isDeleted": false,
			"id": "-FbZrOp4qzGLSH4YnrZkF",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -269.348294942644,
			"y": 1014.1498966479724,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 20.79998779296875,
			"height": 36.79998779296875,
			"seed": 2136847924,
			"groupIds": [
				"pJhYtQozk1mGvh9jWLyDR",
				"vUXmo-KAVbr87GIdP808J",
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1704551663326,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "g2EqVbJq",
				"focus": 0.6048679949200132,
				"gap": 5.600036621093636
			},
			"endBinding": {
				"elementId": "VH8VYxsT",
				"focus": -0.6794531804262305,
				"gap": 6.5999755859375
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
					-20.79998779296875,
					36.79998779296875
				]
			]
		},
		{
			"type": "text",
			"version": 138,
			"versionNonce": 68213419,
			"isDeleted": false,
			"id": "VH8VYxsT",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -332.3483559778002,
			"y": 1057.5498600268786,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 226.4599609375,
			"height": 24,
			"seed": 64587188,
			"groupIds": [
				"pJhYtQozk1mGvh9jWLyDR",
				"vUXmo-KAVbr87GIdP808J",
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "Xo3W8kyCHj4vCU-nLEUYz",
					"type": "arrow"
				},
				{
					"id": "-FbZrOp4qzGLSH4YnrZkF",
					"type": "arrow"
				}
			],
			"updated": 1705369823920,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "所以可使用资源为2 4 4 1",
			"rawText": "所以可使用资源为2 4 4 1",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "所以可使用资源为2 4 4 1",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 613,
			"versionNonce": 1182451980,
			"isDeleted": false,
			"id": "Xo3W8kyCHj4vCU-nLEUYz",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -332.548246114519,
			"y": 1078.1498966479724,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 36.800048828125,
			"height": 17.5999755859375,
			"seed": 216923572,
			"groupIds": [
				"pJhYtQozk1mGvh9jWLyDR",
				"vUXmo-KAVbr87GIdP808J",
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1704551663326,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "VH8VYxsT",
				"focus": 0.6900467482729378,
				"gap": 1
			},
			"endBinding": {
				"elementId": "ia5FYkmt",
				"focus": 0.4940947944442269,
				"gap": 1
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
					-36.800048828125,
					17.5999755859375
				]
			]
		},
		{
			"type": "text",
			"version": 138,
			"versionNonce": 637516165,
			"isDeleted": false,
			"id": "ia5FYkmt",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -528.9482705285815,
			"y": 1096.5498600268786,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 161.21998596191406,
			"height": 24,
			"seed": 271081524,
			"groupIds": [
				"pJhYtQozk1mGvh9jWLyDR",
				"vUXmo-KAVbr87GIdP808J",
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "osewX_0_WsUQ-OIerGzXX",
					"type": "arrow"
				},
				{
					"id": "Xo3W8kyCHj4vCU-nLEUYz",
					"type": "arrow"
				}
			],
			"updated": 1705369823922,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "又只能够给P3提供",
			"rawText": "又只能够给P3提供",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "又只能够给P3提供",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 593,
			"versionNonce": 550881164,
			"isDeleted": false,
			"id": "osewX_0_WsUQ-OIerGzXX",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -538.9482705285815,
			"y": 1112.5498600268786,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 41.5999755859375,
			"height": 3.20001220703125,
			"seed": 1487842868,
			"groupIds": [
				"pJhYtQozk1mGvh9jWLyDR",
				"vUXmo-KAVbr87GIdP808J",
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1704551663326,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "ia5FYkmt",
				"focus": -0.6027225484370115,
				"gap": 10
			},
			"endBinding": {
				"elementId": "soKqDiJ4",
				"focus": -0.3693196226743891,
				"gap": 3.4000244140625
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
					-41.5999755859375,
					-3.20001220703125
				]
			]
		},
		{
			"type": "text",
			"version": 99,
			"versionNonce": 1606467851,
			"isDeleted": false,
			"id": "soKqDiJ4",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -623.9482705285815,
			"y": 1100.5498600268786,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 40,
			"height": 24,
			"seed": 2016248500,
			"groupIds": [
				"pJhYtQozk1mGvh9jWLyDR",
				"vUXmo-KAVbr87GIdP808J",
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "osewX_0_WsUQ-OIerGzXX",
					"type": "arrow"
				},
				{
					"id": "dEgKcouQ9QLVgNg7F31-9",
					"type": "arrow"
				}
			],
			"updated": 1705369826369,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "……",
			"rawText": "……",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "……",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 492,
			"versionNonce": 609023500,
			"isDeleted": false,
			"id": "dEgKcouQ9QLVgNg7F31-9",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -630.5483071496752,
			"y": 1110.9498234057849,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 40,
			"height": 4,
			"seed": 1456625804,
			"groupIds": [
				"vUXmo-KAVbr87GIdP808J",
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1704551663326,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "soKqDiJ4",
				"focus": 0.3042885916573661,
				"gap": 6.60003662109375
			},
			"endBinding": {
				"elementId": "e9dbQ5JL",
				"focus": 0.5567211391922918,
				"gap": 4.320098876953125
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
					4
				]
			]
		},
		{
			"type": "text",
			"version": 103,
			"versionNonce": 1194868965,
			"isDeleted": false,
			"id": "e9dbQ5JL",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -938.7483193567065,
			"y": 1102.5497989917224,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 263.8799133300781,
			"height": 24,
			"seed": 814684812,
			"groupIds": [
				"vUXmo-KAVbr87GIdP808J",
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "dEgKcouQ9QLVgNg7F31-9",
					"type": "arrow"
				}
			],
			"updated": 1705369823923,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "能找到序列为P0 P3 P4 P2 P1",
			"rawText": "能找到序列为P0 P3 P4 P2 P1",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "能找到序列为P0 P3 P4 P2 P1",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "line",
			"version": 52,
			"versionNonce": 1037718668,
			"isDeleted": false,
			"id": "YQGmLVGJvy4Gz9H9x76If",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -943.348294942644,
			"y": 1128.5498600268786,
			"strokeColor": "#2f9e44",
			"backgroundColor": "transparent",
			"width": 276,
			"height": 0.79998779296875,
			"seed": 817070772,
			"groupIds": [
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1704551663326,
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
					276,
					-0.79998779296875
				]
			]
		},
		{
			"type": "text",
			"version": 101,
			"versionNonce": 403991531,
			"isDeleted": false,
			"id": "jsleP9HS",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -812.348294942644,
			"y": 1137.3498478198474,
			"strokeColor": "#2f9e44",
			"backgroundColor": "transparent",
			"width": 300.0799865722656,
			"height": 24,
			"seed": 141657396,
			"groupIds": [
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823924,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "只要能找到一个序列那就是安全的",
			"rawText": "只要能找到一个序列那就是安全的",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "只要能找到一个序列那就是安全的",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "rectangle",
			"version": 60,
			"versionNonce": 725082892,
			"isDeleted": false,
			"id": "F6UPgqmSHc18k8p_WZsHk",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -816.1482827356127,
			"y": 1136.5498600268786,
			"strokeColor": "#2f9e44",
			"backgroundColor": "transparent",
			"width": 314.4000244140625,
			"height": 30.39996337890625,
			"seed": 584823180,
			"groupIds": [
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [],
			"updated": 1704551663326,
			"link": null,
			"locked": false
		},
		{
			"type": "line",
			"version": 53,
			"versionNonce": 787784628,
			"isDeleted": false,
			"id": "NUAdStGjHa2NDlMXkSjsj",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -624.5483071496752,
			"y": 1061.3498478198474,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 160,
			"height": 0.79998779296875,
			"seed": 1904624180,
			"groupIds": [
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1704551663326,
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
					160,
					0.79998779296875
				]
			]
		},
		{
			"type": "arrow",
			"version": 284,
			"versionNonce": 1658823052,
			"isDeleted": false,
			"id": "darq4BtekGAtnQ0qJw_Em",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -495.7482583215502,
			"y": 1061.3498478198474,
			"strokeColor": "#1971c2",
			"backgroundColor": "transparent",
			"width": 236.79998779296875,
			"height": 66.4000244140625,
			"seed": 470810164,
			"groupIds": [
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1704551663326,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "5U1QKuoi",
				"focus": 0.21459805987653058,
				"gap": 10.39996337890625
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
					236.79998779296875,
					66.4000244140625
				]
			]
		},
		{
			"type": "text",
			"version": 82,
			"versionNonce": 1923669061,
			"isDeleted": false,
			"id": "5U1QKuoi",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -317.7482583215502,
			"y": 1138.149835612816,
			"strokeColor": "#1971c2",
			"backgroundColor": "transparent",
			"width": 213.23992919921875,
			"height": 24,
			"seed": 1188364980,
			"groupIds": [
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "darq4BtekGAtnQ0qJw_Em",
					"type": "arrow"
				}
			],
			"updated": 1705369823926,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "说明尚需资源为0 10 7 2",
			"rawText": "说明尚需资源为0 10 7 2",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "说明尚需资源为0 10 7 2",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "text",
			"version": 185,
			"versionNonce": 236304011,
			"isDeleted": false,
			"id": "sjVGRUct",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -920.8816404830086,
			"y": 1496.442464698045,
			"strokeColor": "#1971c2",
			"backgroundColor": "transparent",
			"width": 50.04585266113281,
			"height": 28.373723517663908,
			"seed": 2081439924,
			"groupIds": [
				"LsZN0_FzGHu9F-bsN-quD",
				"LEBXYBDM5YD9b98nJPszW",
				"wvf61GcZxN3Gbz-73nrpH"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823927,
			"link": null,
			"locked": false,
			"fontSize": 23.64476959805326,
			"fontFamily": 4,
			"text": "OPT:",
			"rawText": "OPT:",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "OPT:",
			"lineHeight": 1.2,
			"baseline": 20
		},
		{
			"type": "image",
			"version": 192,
			"versionNonce": 1212040884,
			"isDeleted": false,
			"id": "anExIFJM",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -917.6500515375315,
			"y": 1254.732641757095,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 712.9681791507612,
			"height": 232.43035285890014,
			"seed": 44048,
			"groupIds": [
				"bXqV8oojYcv7wLQIQ1bJF",
				"LsZN0_FzGHu9F-bsN-quD",
				"LEBXYBDM5YD9b98nJPszW",
				"wvf61GcZxN3Gbz-73nrpH"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1704551663326,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "e1da97656258e1f8031b3dec765b6b218b788c4f",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "line",
			"version": 79,
			"versionNonce": 381005452,
			"isDeleted": false,
			"id": "rnirAR3jb8_36glS19B04",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -432.68162827597735,
			"y": 1330.583652203054,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 142.39996337890625,
			"height": 0,
			"seed": 1142688564,
			"groupIds": [
				"bXqV8oojYcv7wLQIQ1bJF",
				"LsZN0_FzGHu9F-bsN-quD",
				"LEBXYBDM5YD9b98nJPszW",
				"wvf61GcZxN3Gbz-73nrpH"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1704551663326,
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
					142.39996337890625,
					0
				]
			]
		},
		{
			"type": "text",
			"version": 147,
			"versionNonce": 1345260453,
			"isDeleted": false,
			"id": "u1FPTyIv",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -865.8816404830086,
			"y": 1495.7836338925072,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 175.2399444580078,
			"height": 24,
			"seed": 945731980,
			"groupIds": [
				"bXqV8oojYcv7wLQIQ1bJF",
				"LsZN0_FzGHu9F-bsN-quD",
				"LEBXYBDM5YD9b98nJPszW",
				"wvf61GcZxN3Gbz-73nrpH"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823928,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "首先是2 3 1 进来了",
			"rawText": "首先是2 3 1 进来了",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "首先是2 3 1 进来了",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "text",
			"version": 241,
			"versionNonce": 1456778539,
			"isDeleted": false,
			"id": "AS2Z5zlN",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -700.8816404830086,
			"y": 1495.7836338925072,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 434.8199157714844,
			"height": 48,
			"seed": 1587012620,
			"groupIds": [
				"bXqV8oojYcv7wLQIQ1bJF",
				"LsZN0_FzGHu9F-bsN-quD",
				"LEBXYBDM5YD9b98nJPszW",
				"wvf61GcZxN3Gbz-73nrpH"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823930,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "，2再进来了更新了原来的2，还是2 3 1，4进来，\n3在后面要使用，2也要使用，所以淘汰1",
			"rawText": "，2再进来了更新了原来的2，还是2 3 1，4进来，\n3在后面要使用，2也要使用，所以淘汰1",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "，2再进来了更新了原来的2，还是2 3 1，4进来，\n3在后面要使用，2也要使用，所以淘汰1",
			"lineHeight": 1.2,
			"baseline": 42
		},
		{
			"type": "text",
			"version": 114,
			"versionNonce": 804802309,
			"isDeleted": false,
			"id": "9ZF6Ahq9",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -922.081683207618,
			"y": 1554.9836155819603,
			"strokeColor": "#1971c2",
			"backgroundColor": "transparent",
			"width": 49.93995666503906,
			"height": 24,
			"seed": 1806981044,
			"groupIds": [
				"LsZN0_FzGHu9F-bsN-quD",
				"LEBXYBDM5YD9b98nJPszW",
				"wvf61GcZxN3Gbz-73nrpH"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823931,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "FIFO:",
			"rawText": "FIFO:",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "FIFO:",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "text",
			"version": 176,
			"versionNonce": 633065419,
			"isDeleted": false,
			"id": "DcJpZnSJ",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -862.6816893111336,
			"y": 1555.583652203054,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 260.27996826171875,
			"height": 24,
			"seed": 1932724236,
			"groupIds": [
				"LsZN0_FzGHu9F-bsN-quD",
				"LEBXYBDM5YD9b98nJPszW",
				"wvf61GcZxN3Gbz-73nrpH"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823932,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "4进来，那就淘汰最先进来的2",
			"rawText": "4进来，那就淘汰最先进来的2",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "4进来，那就淘汰最先进来的2",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "text",
			"version": 98,
			"versionNonce": 8529509,
			"isDeleted": false,
			"id": "ZbcQ1bPp",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -920.2816648970711,
			"y": 1592.9836766171165,
			"strokeColor": "#1971c2",
			"backgroundColor": "transparent",
			"width": 41.01995849609375,
			"height": 24,
			"seed": 1198040460,
			"groupIds": [
				"LsZN0_FzGHu9F-bsN-quD",
				"LEBXYBDM5YD9b98nJPszW",
				"wvf61GcZxN3Gbz-73nrpH"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823933,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "LRU:",
			"rawText": "LRU:",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "LRU:",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "text",
			"version": 209,
			"versionNonce": 1558552171,
			"isDeleted": false,
			"id": "UixQAajl",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -868.8816404830086,
			"y": 1591.5835911678978,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 548.679931640625,
			"height": 24,
			"seed": 201196852,
			"groupIds": [
				"LsZN0_FzGHu9F-bsN-quD",
				"LEBXYBDM5YD9b98nJPszW",
				"wvf61GcZxN3Gbz-73nrpH"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823934,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "2进来了，说明2使用了，4再进来，那就是3最久未使用，淘汰3",
			"rawText": "2进来了，说明2使用了，4再进来，那就是3最久未使用，淘汰3",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "2进来了，说明2使用了，4再进来，那就是3最久未使用，淘汰3",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "image",
			"version": 287,
			"versionNonce": 1906003124,
			"isDeleted": false,
			"id": "bPo3y7jy",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -812.0397834461982,
			"y": 1637.42041649822,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 603.2000732421876,
			"height": 393.84035910521044,
			"seed": 34958,
			"groupIds": [
				"v9lh0fVHlRQ8Qxuc0XcGv",
				"LEBXYBDM5YD9b98nJPszW",
				"wvf61GcZxN3Gbz-73nrpH"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "a0ZrK-AMhvfPc0S4KDmiH",
					"type": "arrow"
				}
			],
			"updated": 1704551663326,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "83dfcdad93975a5487f5d426f4d62ba754dc022b",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "rectangle",
			"version": 98,
			"versionNonce": 34867340,
			"isDeleted": false,
			"id": "3GeHHyAhs4x005SZlihiQ",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -748.5399099253694,
			"y": 1686.226344281865,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 21.75895595086797,
			"height": 23.69307430154572,
			"seed": 876547508,
			"groupIds": [
				"v9lh0fVHlRQ8Qxuc0XcGv",
				"LEBXYBDM5YD9b98nJPszW",
				"wvf61GcZxN3Gbz-73nrpH"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [],
			"updated": 1704551663326,
			"link": null,
			"locked": false
		},
		{
			"type": "arrow",
			"version": 214,
			"versionNonce": 1601672756,
			"isDeleted": false,
			"id": "a0ZrK-AMhvfPc0S4KDmiH",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -745.1439600026831,
			"y": 1687.7684225531943,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 80.46803280940048,
			"height": 34.9682805389491,
			"seed": 278575028,
			"groupIds": [
				"v9lh0fVHlRQ8Qxuc0XcGv",
				"LEBXYBDM5YD9b98nJPszW",
				"wvf61GcZxN3Gbz-73nrpH"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1704551663326,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "bPo3y7jy",
				"focus": 1.0228871817313465,
				"gap": 13.572209365885442
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
					-46.7064587894796,
					-10.008514156960018
				],
				[
					-80.06821506767938,
					-12.010227169551854
				],
				[
					-80.46803280940048,
					-34.9682805389491
				]
			]
		},
		{
			"type": "text",
			"version": 201,
			"versionNonce": 77205957,
			"isDeleted": false,
			"id": "0ECahKRF",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -922.9620802406874,
			"y": 1732.8067935287638,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 115.83895874023438,
			"height": 36.61588909483841,
			"seed": 567690292,
			"groupIds": [
				"v9lh0fVHlRQ8Qxuc0XcGv",
				"LEBXYBDM5YD9b98nJPszW",
				"wvf61GcZxN3Gbz-73nrpH"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823936,
			"link": null,
			"locked": false,
			"fontSize": 15.256620456182672,
			"fontFamily": 4,
			"text": "2进来,块里没有2,\n所以缺页",
			"rawText": "2进来,块里没有2,\n所以缺页",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "2进来,块里没有2,\n所以缺页",
			"lineHeight": 1.2,
			"baseline": 31
		},
		{
			"type": "arrow",
			"version": 242,
			"versionNonce": 772714420,
			"isDeleted": false,
			"id": "OuzQN8anImOeJMQR1pyea",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -847.8981286147381,
			"y": 1755.8263849983216,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 109.42651986769488,
			"height": 39.36690804247587,
			"seed": 993777588,
			"groupIds": [
				"v9lh0fVHlRQ8Qxuc0XcGv",
				"LEBXYBDM5YD9b98nJPszW",
				"wvf61GcZxN3Gbz-73nrpH"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1704551663326,
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
					88.74226660941122,
					26.02220553119605
				],
				[
					109.42651986769488,
					39.36690804247587
				]
			]
		},
		{
			"type": "rectangle",
			"version": 109,
			"versionNonce": 54285708,
			"isDeleted": false,
			"id": "9MI9ixmCLbw1BKmADf5Q2",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -665.4093319541855,
			"y": 1685.7667222671023,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 20.017053766919787,
			"height": 22.01875405301189,
			"seed": 64455348,
			"groupIds": [
				"v9lh0fVHlRQ8Qxuc0XcGv",
				"LEBXYBDM5YD9b98nJPszW",
				"wvf61GcZxN3Gbz-73nrpH"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [],
			"updated": 1704551663326,
			"link": null,
			"locked": false
		},
		{
			"type": "arrow",
			"version": 176,
			"versionNonce": 495360308,
			"isDeleted": false,
			"id": "vX3yCPjiM44t5td_KO2D6",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -654.7335801263617,
			"y": 1687.7684225531943,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 13.344702511279877,
			"height": 40.03409480733967,
			"seed": 2081785140,
			"groupIds": [
				"v9lh0fVHlRQ8Qxuc0XcGv",
				"LEBXYBDM5YD9b98nJPszW",
				"wvf61GcZxN3Gbz-73nrpH"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1704551663326,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "CUZ9gWMV",
				"focus": 0.8751195146419601,
				"gap": 6.005126311276058
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
					-10.008526883459865,
					-29.358342979515783
				],
				[
					3.336175627820012,
					-40.03409480733967
				]
			]
		},
		{
			"type": "text",
			"version": 222,
			"versionNonce": 924621067,
			"isDeleted": false,
			"id": "CUZ9gWMV",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -645.3922781872657,
			"y": 1633.8891683468016,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 154.63351440429688,
			"height": 21.088754767154168,
			"seed": 2045156364,
			"groupIds": [
				"v9lh0fVHlRQ8Qxuc0XcGv",
				"LEBXYBDM5YD9b98nJPszW",
				"wvf61GcZxN3Gbz-73nrpH"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "vX3yCPjiM44t5td_KO2D6",
					"type": "arrow"
				}
			],
			"updated": 1705369823938,
			"link": null,
			"locked": false,
			"fontSize": 17.573962305961807,
			"fontFamily": 4,
			"text": "块里有2,所以不缺页",
			"rawText": "块里有2,所以不缺页",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "块里有2,所以不缺页",
			"lineHeight": 1.2,
			"baseline": 15
		},
		{
			"type": "arrow",
			"version": 139,
			"versionNonce": 2034586292,
			"isDeleted": false,
			"id": "85jRGKCIHH8FdmoJtfb7R",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -264.2812333167399,
			"y": 1662.138622790852,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 61.91262437735497,
			"height": 140.7105966989709,
			"seed": 733811892,
			"groupIds": [
				"v9lh0fVHlRQ8Qxuc0XcGv",
				"LEBXYBDM5YD9b98nJPszW",
				"wvf61GcZxN3Gbz-73nrpH"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1704551663326,
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
					50.03043438185637,
					1.2507656308202968
				],
				[
					59.41114082845445,
					113.19384824640179
				],
				[
					-2.5014835489005236,
					140.7105966989709
				]
			]
		},
		{
			"type": "image",
			"version": 88,
			"versionNonce": 369942540,
			"isDeleted": false,
			"id": "SlcIdYBd",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -706.6114716462596,
			"y": 2155.5800320286844,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 672.8000488281251,
			"height": 354.05881834655924,
			"seed": 71273,
			"groupIds": [
				"MLFYLzv_yxz5DtiRkHsBP",
				"d4Hu4wFoFJaUHLcteaXAa"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1704552189094,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "d696d0f843efdf94f24b086030b9bfe87fc3a293",
			"scale": [
				1,
				1
			]
		},
		{
			"type": "text",
			"version": 163,
			"versionNonce": 1230868773,
			"isDeleted": false,
			"id": "kXjgrfO6",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -762.5190208177107,
			"y": 2341.419474049102,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 89.89598083496094,
			"height": 40.800018310546875,
			"seed": 26138636,
			"groupIds": [
				"MLFYLzv_yxz5DtiRkHsBP",
				"d4Hu4wFoFJaUHLcteaXAa"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823939,
			"link": null,
			"locked": false,
			"fontSize": 34.00001525878906,
			"fontFamily": 4,
			"text": "FCFS:",
			"rawText": "FCFS:",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "FCFS:",
			"lineHeight": 1.2,
			"baseline": 29
		},
		{
			"type": "text",
			"version": 228,
			"versionNonce": 836452267,
			"isDeleted": false,
			"id": "UmbkbDQU",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -763.7190025071639,
			"y": 2382.4195350842583,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 235.7799530029297,
			"height": 48,
			"seed": 294941836,
			"groupIds": [
				"MLFYLzv_yxz5DtiRkHsBP",
				"d4Hu4wFoFJaUHLcteaXAa"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823941,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "65到了就先从110移动到65，\n然后再从65移动到68",
			"rawText": "65到了就先从110移动到65，\n然后再从65移动到68",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "65到了就先从110移动到65，\n然后再从65移动到68",
			"lineHeight": 1.2,
			"baseline": 42
		},
		{
			"type": "rectangle",
			"version": 37,
			"versionNonce": 1311834164,
			"isDeleted": false,
			"id": "7Mbq8IdBgPirBtLyZuk9M",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -772.118935368492,
			"y": 2337.0194496350396,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 109.60003662109375,
			"height": 44.800018310546875,
			"seed": 1241711884,
			"groupIds": [
				"MLFYLzv_yxz5DtiRkHsBP",
				"d4Hu4wFoFJaUHLcteaXAa"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [],
			"updated": 1704552189094,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 112,
			"versionNonce": 1547314309,
			"isDeleted": false,
			"id": "Es8VMBLB",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -311.9189231614607,
			"y": 2215.8194679455864,
			"strokeColor": "#1971c2",
			"backgroundColor": "transparent",
			"width": 268,
			"height": 24,
			"seed": 1028604212,
			"groupIds": [
				"MLFYLzv_yxz5DtiRkHsBP",
				"d4Hu4wFoFJaUHLcteaXAa"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [
				{
					"id": "h9_qP3Qgt6IMByBL2dhH1",
					"type": "arrow"
				}
			],
			"updated": 1705369823943,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "把移动的距离相加/移动的次数",
			"rawText": "把移动的距离相加/移动的次数",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "把移动的距离相加/移动的次数",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 12,
			"versionNonce": 369809844,
			"isDeleted": false,
			"id": "h9_qP3Qgt6IMByBL2dhH1",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -366.7189109544295,
			"y": 2230.619455738555,
			"strokeColor": "#1971c2",
			"backgroundColor": "transparent",
			"width": 54.39996337890625,
			"height": 1.600006103515625,
			"seed": 1470140596,
			"groupIds": [
				"MLFYLzv_yxz5DtiRkHsBP",
				"d4Hu4wFoFJaUHLcteaXAa"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1704552189094,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "Es8VMBLB",
				"focus": 0.17269584186154438,
				"gap": 1
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
					54.39996337890625,
					-1.600006103515625
				]
			]
		},
		{
			"type": "text",
			"version": 128,
			"versionNonce": 927732299,
			"isDeleted": false,
			"id": "do8UtMr8",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -765.0389545945243,
			"y": 2453.5893685346036,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 76.06973266601562,
			"height": 34.79997253417969,
			"seed": 992652980,
			"groupIds": [
				"MLFYLzv_yxz5DtiRkHsBP",
				"d4Hu4wFoFJaUHLcteaXAa"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823945,
			"link": null,
			"locked": false,
			"fontSize": 28.999977111816406,
			"fontFamily": 4,
			"text": "SSTF:",
			"rawText": "SSTF:",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "SSTF:",
			"lineHeight": 1.2,
			"baseline": 25
		},
		{
			"type": "rectangle",
			"version": 125,
			"versionNonce": 1215136564,
			"isDeleted": false,
			"id": "GXCnw_7RvUJ0ntxcoAR_m",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -768.5188987473982,
			"y": 2449.81940691043,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 90.47987548832316,
			"height": 46.39996337890625,
			"seed": 1995645876,
			"groupIds": [
				"MLFYLzv_yxz5DtiRkHsBP",
				"d4Hu4wFoFJaUHLcteaXAa"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [],
			"updated": 1704552189094,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 87,
			"versionNonce": 1089293285,
			"isDeleted": false,
			"id": "n2626deA",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -762.3190086106795,
			"y": 2505.219492359649,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 222.63990783691406,
			"height": 24,
			"seed": 696278708,
			"groupIds": [
				"MLFYLzv_yxz5DtiRkHsBP",
				"d4Hu4wFoFJaUHLcteaXAa"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823945,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "110先到100，从100到68……",
			"rawText": "110先到100，从100到68……",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "110先到100，从100到68……",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "text",
			"version": 136,
			"versionNonce": 139038955,
			"isDeleted": false,
			"id": "7zMC1cGp",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -475.2098737159205,
			"y": 2532.083086572462,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 79.76988220214844,
			"height": 27.272723489551183,
			"seed": 960900236,
			"groupIds": [
				"MLFYLzv_yxz5DtiRkHsBP",
				"d4Hu4wFoFJaUHLcteaXAa"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823947,
			"link": null,
			"locked": false,
			"fontSize": 22.727269574625986,
			"fontFamily": 4,
			"text": "SCAN：",
			"rawText": "SCAN：",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "SCAN：",
			"lineHeight": 1.2,
			"baseline": 19
		},
		{
			"type": "rectangle",
			"version": 155,
			"versionNonce": 558061708,
			"isDeleted": false,
			"id": "oP4jn3jIIwdToZ8mk0zfK",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -486.118935368492,
			"y": 2528.219492359649,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 100.90906303971488,
			"height": 39.99993896484375,
			"seed": 842673548,
			"groupIds": [
				"MLFYLzv_yxz5DtiRkHsBP",
				"d4Hu4wFoFJaUHLcteaXAa"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [],
			"updated": 1704552189094,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 99,
			"versionNonce": 662996805,
			"isDeleted": false,
			"id": "avt4HuLj",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -379.318886540367,
			"y": 2522.619455738555,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 248.41990661621094,
			"height": 24,
			"seed": 553354252,
			"groupIds": [
				"MLFYLzv_yxz5DtiRkHsBP",
				"d4Hu4wFoFJaUHLcteaXAa"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823948,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "从110到160，再到170，再到194",
			"rawText": "从110到160，再到170，再到194",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "从110到160，再到170，再到194",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "text",
			"version": 86,
			"versionNonce": 1717451659,
			"isDeleted": false,
			"id": "z2VSILIa",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -377.5189597825545,
			"y": 2551.619394703399,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 162.7999725341797,
			"height": 24,
			"seed": 1589548084,
			"groupIds": [
				"MLFYLzv_yxz5DtiRkHsBP",
				"d4Hu4wFoFJaUHLcteaXAa"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823949,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "再回去扫描100……",
			"rawText": "再回去扫描100……",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "再回去扫描100……",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "text",
			"version": 282,
			"versionNonce": 1650284197,
			"isDeleted": false,
			"id": "LrxTWLfo",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -759.5189597825545,
			"y": 2556.0194191174614,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 110.21998596191406,
			"height": 24,
			"seed": 2094403724,
			"groupIds": [
				"d4Hu4wFoFJaUHLcteaXAa"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823950,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "循环SCAN：",
			"rawText": "循环SCAN：",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "循环SCAN：",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "rectangle",
			"version": 290,
			"versionNonce": 2060952972,
			"isDeleted": false,
			"id": "tePW2rRio--RRCRPU2TI9",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -770.7189719895857,
			"y": 2549.0194191174614,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 122.4000244140625,
			"height": 36.79998779296875,
			"seed": 411488908,
			"groupIds": [
				"d4Hu4wFoFJaUHLcteaXAa"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [],
			"updated": 1704552189094,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 121,
			"versionNonce": 2110034475,
			"isDeleted": false,
			"id": "LlrhoyQv",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -760.3288886765974,
			"y": 2592.619455738555,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 248.41990661621094,
			"height": 24,
			"seed": 1946561204,
			"groupIds": [
				"6t2LeCY1ICD9wEpWtXLT2",
				"d4Hu4wFoFJaUHLcteaXAa"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823950,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "从110到160，再到170，再到194",
			"rawText": "从110到160，再到170，再到194",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "从110到160，再到170，再到194",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "text",
			"version": 87,
			"versionNonce": 472201733,
			"isDeleted": false,
			"id": "a24n4JZR",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -763.9189231614607,
			"y": 2618.8194679455864,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 139.95997619628906,
			"height": 24,
			"seed": 2050043188,
			"groupIds": [
				"d4Hu4wFoFJaUHLcteaXAa"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823951,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "再到28，48……",
			"rawText": "再到28，48……",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "再到28，48……",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "rectangle",
			"version": 204,
			"versionNonce": 751779690,
			"isDeleted": false,
			"id": "9dieLlb4LEO1e47StW5UF",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -182.11310833041807,
			"y": -134.9370709210333,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 81.6000366210937,
			"height": 44.80001831054682,
			"seed": 200779190,
			"groupIds": [
				"jdACSrUm3Q5SUBm4Q7DZp",
				"kzZ7BpGqBa-KQohVoIMNp"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [
				{
					"type": "text",
					"id": "lUKjFdyx"
				},
				{
					"id": "Xfq2tzbZFQsoeOe4hPvpH",
					"type": "arrow"
				},
				{
					"id": "LAuzygNsl5cDwYhcWjhhc",
					"type": "arrow"
				}
			],
			"updated": 1704896496989,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 150,
			"versionNonce": 445367541,
			"isDeleted": false,
			"id": "lUKjFdyx",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -171.31309001987123,
			"y": -124.53706176575989,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 60,
			"height": 24,
			"seed": 1066595766,
			"groupIds": [
				"jdACSrUm3Q5SUBm4Q7DZp",
				"kzZ7BpGqBa-KQohVoIMNp"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705286752216,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "客户端",
			"rawText": "客户端",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "9dieLlb4LEO1e47StW5UF",
			"originalText": "客户端",
			"lineHeight": 1.2,
			"baseline": 20
		},
		{
			"type": "arrow",
			"version": 690,
			"versionNonce": 1080168549,
			"isDeleted": false,
			"id": "Xfq2tzbZFQsoeOe4hPvpH",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -94.11316936557432,
			"y": -125.33706481751767,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 175.20001220703125,
			"height": 1.6000061035156392,
			"seed": 666106230,
			"groupIds": [
				"jdACSrUm3Q5SUBm4Q7DZp",
				"kzZ7BpGqBa-KQohVoIMNp"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1705369823752,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "9dieLlb4LEO1e47StW5UF",
				"gap": 6.399902343750057,
				"focus": -0.5810072785172423
			},
			"endBinding": {
				"elementId": "E9go_c9fX7nkr7ocSUrYL",
				"gap": 12,
				"focus": 0.14178852524361027
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
					175.20001220703125,
					1.6000061035156392
				]
			]
		},
		{
			"type": "arrow",
			"version": 685,
			"versionNonce": 231406373,
			"isDeleted": false,
			"id": "LAuzygNsl5cDwYhcWjhhc",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 81.88683063442565,
			"y": -98.13708312806455,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 171.99999999999997,
			"height": 1.600006103515625,
			"seed": 1342450602,
			"groupIds": [
				"jdACSrUm3Q5SUBm4Q7DZp",
				"kzZ7BpGqBa-KQohVoIMNp"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1705369823753,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "E9go_c9fX7nkr7ocSUrYL",
				"gap": 11.20001220703125,
				"focus": -0.046483127696803614
			},
			"endBinding": {
				"elementId": "9dieLlb4LEO1e47StW5UF",
				"gap": 10.399902343750057,
				"focus": 0.7232920769240555
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
					-171.99999999999997,
					1.600006103515625
				]
			]
		},
		{
			"type": "text",
			"version": 100,
			"versionNonce": 258413771,
			"isDeleted": false,
			"id": "mzGIOjNQ",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -54.11316936557432,
			"y": -157.33709533509574,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 67.87995910644531,
			"height": 24,
			"seed": 1625997366,
			"groupIds": [
				"jdACSrUm3Q5SUBm4Q7DZp",
				"kzZ7BpGqBa-KQohVoIMNp"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823952,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "request",
			"rawText": "request",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "request",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "text",
			"version": 85,
			"versionNonce": 1306112357,
			"isDeleted": false,
			"id": "6ZhaS3ef",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -50.31312053744932,
			"y": -91.9370709210333,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 78.13995361328125,
			"height": 24,
			"seed": 982338090,
			"groupIds": [
				"jdACSrUm3Q5SUBm4Q7DZp",
				"kzZ7BpGqBa-KQohVoIMNp"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823953,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "response",
			"rawText": "response",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "response",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "rectangle",
			"version": 111,
			"versionNonce": 787005354,
			"isDeleted": false,
			"id": "E9go_c9fX7nkr7ocSUrYL",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 93.08684284145693,
			"y": -230.1370831280645,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 180.00006103515614,
			"height": 250.39999389648432,
			"seed": 1273024182,
			"groupIds": [
				"jdACSrUm3Q5SUBm4Q7DZp",
				"kzZ7BpGqBa-KQohVoIMNp"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [
				{
					"id": "Xfq2tzbZFQsoeOe4hPvpH",
					"type": "arrow"
				},
				{
					"id": "LAuzygNsl5cDwYhcWjhhc",
					"type": "arrow"
				}
			],
			"updated": 1704896496989,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 113,
			"versionNonce": 1524646763,
			"isDeleted": false,
			"id": "nw1fXlc6",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 105.48680622036318,
			"y": -221.737058714002,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 101.93995666503906,
			"height": 24,
			"seed": 1864160374,
			"groupIds": [
				"jdACSrUm3Q5SUBm4Q7DZp",
				"kzZ7BpGqBa-KQohVoIMNp"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705369823954,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "Servlet容器",
			"rawText": "Servlet容器",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "Servlet容器",
			"lineHeight": 1.2,
			"baseline": 18
		},
		{
			"type": "rectangle",
			"version": 43,
			"versionNonce": 734476906,
			"isDeleted": false,
			"id": "YKpS4wD9C6qcmjmwD-yvP",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 123.48686725551943,
			"y": -177.33706481751761,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 121.5999755859375,
			"height": 44.80001831054682,
			"seed": 126594986,
			"groupIds": [
				"kzZ7BpGqBa-KQohVoIMNp"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [
				{
					"type": "text",
					"id": "hNBugFyE"
				}
			],
			"updated": 1704896496989,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 17,
			"versionNonce": 251698755,
			"isDeleted": false,
			"id": "hNBugFyE",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 144.36009723598818,
			"y": -166.9370556622442,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 79.853515625,
			"height": 24,
			"seed": 1559066730,
			"groupIds": [
				"kzZ7BpGqBa-KQohVoIMNp"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705326387742,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "init()方法",
			"rawText": "init()方法",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "YKpS4wD9C6qcmjmwD-yvP",
			"originalText": "init()方法",
			"lineHeight": 1.2,
			"baseline": 20
		},
		{
			"type": "rectangle",
			"version": 29,
			"versionNonce": 1686658346,
			"isDeleted": false,
			"id": "4FNc3F8lqi2z-LJChA8xk",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 115.48686725551943,
			"y": -108.5370465069708,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 144.00006103515625,
			"height": 36.800018310546875,
			"seed": 436907050,
			"groupIds": [
				"kzZ7BpGqBa-KQohVoIMNp"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [
				{
					"type": "text",
					"id": "kYo8j9A8"
				}
			],
			"updated": 1704896496989,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 18,
			"versionNonce": 267004291,
			"isDeleted": false,
			"id": "kYo8j9A8",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 137.07674152309755,
			"y": -102.13703735169736,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 100.8203125,
			"height": 24,
			"seed": 1609090666,
			"groupIds": [
				"kzZ7BpGqBa-KQohVoIMNp"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705326387744,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "service方法",
			"rawText": "service方法",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "4FNc3F8lqi2z-LJChA8xk",
			"originalText": "service方法",
			"lineHeight": 1.2,
			"baseline": 20
		},
		{
			"type": "rectangle",
			"version": 42,
			"versionNonce": 379004906,
			"isDeleted": false,
			"id": "ptViGwh4W0UxYj04GMBSR",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 122.68681842739443,
			"y": -51.73708923158017,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 128,
			"height": 56,
			"seed": 1932193834,
			"groupIds": [
				"kzZ7BpGqBa-KQohVoIMNp"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [
				{
					"type": "text",
					"id": "ndwy8y1j"
				}
			],
			"updated": 1704896496989,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 43,
			"versionNonce": 567928003,
			"isDeleted": false,
			"id": "ndwy8y1j",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 133.89384967739443,
			"y": -35.73708923158017,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 105.5859375,
			"height": 24,
			"seed": 489979562,
			"groupIds": [
				"kzZ7BpGqBa-KQohVoIMNp"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1705326387747,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 4,
			"text": "destroy方法",
			"rawText": "destroy方法",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "ptViGwh4W0UxYj04GMBSR",
			"originalText": "destroy方法",
			"lineHeight": 1.2,
			"baseline": 20
		},
		{
			"type": "image",
			"version": 15,
			"versionNonce": 1298994437,
			"isDeleted": false,
			"id": "0tAkucai",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 384.5626027421573,
			"y": 411.13021105853363,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 395.86776859504135,
			"height": 500.00000000000006,
			"seed": 34211,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1704980475617,
			"link": null,
			"locked": false,
			"status": "pending",
			"fileId": "03680fe1d28f617aa1faf37271b950a2d32d434b",
			"scale": [
				1,
				1
			]
		}
	],
	"appState": {
		"theme": "light",
		"viewBackgroundColor": "#ffffff",
		"currentItemStrokeColor": "#1e1e1e",
		"currentItemBackgroundColor": "transparent",
		"currentItemFillStyle": "solid",
		"currentItemStrokeWidth": 1,
		"currentItemStrokeStyle": "solid",
		"currentItemRoughness": 1,
		"currentItemOpacity": 100,
		"currentItemFontFamily": 4,
		"currentItemFontSize": 20,
		"currentItemTextAlign": "left",
		"currentItemStartArrowhead": null,
		"currentItemEndArrowhead": "arrow",
		"scrollX": 3153.831779230029,
		"scrollY": 504.8698194590445,
		"zoom": {
			"value": 0.25
		},
		"currentItemRoundness": "round",
		"gridSize": null,
		"gridColor": {
			"Bold": "#C9C9C9FF",
			"Regular": "#EDEDEDFF"
		},
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