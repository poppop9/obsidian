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


# Embedded files
5da0c3aa0de4c7df4efcca15e0985a71085136f0: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240102163106.png
994562a6fef2ce98da3aeb82cfeba8d3501ca650: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240104224727.png
85d4ccb0a76bd2fd92092b1cfdd67101f1d671f1: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240104235700.png
a041a9e831914c2ddb555c4f0ebea45d6ce8d1a3: https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240105105116.png

%%
# Drawing
```json
{
	"type": "excalidraw",
	"version": 2,
	"source": "https://github.com/zsviczian/obsidian-excalidraw-plugin/releases/tag/2.0.13",
	"elements": [
		{
			"type": "rectangle",
			"version": 144,
			"versionNonce": 2104478388,
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
			"updated": 1704379809245,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 134,
			"versionNonce": 709782156,
			"isDeleted": false,
			"id": "RkkZ35Xu",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -581.9778921725497,
			"y": -319.7982053810095,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 60.03999328613281,
			"height": 24,
			"seed": 1432515481,
			"groupIds": [
				"qx4T7IaayHInFrYxXCYYg"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1704379809245,
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
			"baseline": 18
		},
		{
			"type": "rectangle",
			"version": 77,
			"versionNonce": 940332084,
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
			"updated": 1704379809245,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 59,
			"versionNonce": 1555642636,
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
			"updated": 1704379809245,
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
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 245,
			"versionNonce": 910073652,
			"isDeleted": false,
			"id": "05OXV3LLHobliFHQeLH2x",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -414.26114361157136,
			"y": -324.40145169800843,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 138.13916312326455,
			"height": 0.6676203026530061,
			"seed": 709204375,
			"groupIds": [
				"qx4T7IaayHInFrYxXCYYg"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1704384084261,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "gIHYhFdL",
				"gap": 9.599975585937443,
				"focus": 1.6353118837606766
			},
			"endBinding": {
				"elementId": "PTPIghP7Guh-OSA3kilGE",
				"gap": 7.199951171875,
				"focus": 0.47508592569508035
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
					138.13916312326455,
					0.6676203026530061
				]
			]
		},
		{
			"type": "text",
			"version": 98,
			"versionNonce": 1170618252,
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
			"updated": 1704379809245,
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
			"version": 126,
			"versionNonce": 176412468,
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
			"updated": 1704379809245,
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
			"version": 240,
			"versionNonce": 316629556,
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
			"updated": 1704384084261,
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
			"version": 74,
			"versionNonce": 267047092,
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
			"updated": 1704379809245,
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
			"version": 46,
			"versionNonce": 1433322636,
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
			"updated": 1704379809245,
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
			"version": 296,
			"versionNonce": 1412363788,
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
			"updated": 1704379849035,
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
			"version": 266,
			"versionNonce": 49037492,
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
			"updated": 1704379849035,
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
			"version": 318,
			"versionNonce": 561796236,
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
			"updated": 1704379849035,
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
			"version": 93,
			"versionNonce": 42601012,
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
			"updated": 1704379849035,
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
			"version": 95,
			"versionNonce": 1251599116,
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
			"updated": 1704379849035,
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
			"version": 144,
			"versionNonce": 783459252,
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
			"updated": 1704379849035,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 82,
			"versionNonce": 1174512012,
			"isDeleted": false,
			"id": "ZHDFo9us",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -211.8934723275629,
			"y": 376.39369886326546,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"width": 40,
			"height": 24,
			"seed": 1630199860,
			"groupIds": [
				"VLNIQQmgGfXHq3xJjrX9W",
				"DWOkBI9BjiVhmj2Tcibzi"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1704379849035,
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
			"baseline": 18
		},
		{
			"type": "text",
			"version": 110,
			"versionNonce": 1301024052,
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
			"updated": 1704379849035,
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
			"version": 163,
			"versionNonce": 840245812,
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
			"updated": 1704379882095,
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
			"version": 166,
			"versionNonce": 1887192756,
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
			"updated": 1704379849035,
			"link": null,
			"locked": false
		},
		{
			"type": "line",
			"version": 74,
			"versionNonce": 425176716,
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
			"updated": 1704379849035,
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
			"version": 109,
			"versionNonce": 204034100,
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
			"updated": 1704379849035,
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
			"version": 122,
			"versionNonce": 570031372,
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
			"updated": 1704379849035,
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
			"version": 92,
			"versionNonce": 925967668,
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
			"updated": 1704379882095,
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
			"version": 40,
			"versionNonce": 776895372,
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
			"updated": 1704379849035,
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
			"version": 59,
			"versionNonce": 9556788,
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
			"updated": 1704379849035,
			"link": null,
			"locked": false
		},
		{
			"type": "image",
			"version": 13,
			"versionNonce": 1848347828,
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
			"updated": 1704384076092,
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
			"version": 272,
			"versionNonce": 94881932,
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
			"updated": 1704384076092,
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
			"version": 56,
			"versionNonce": 1610602036,
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
			"updated": 1704384076092,
			"link": null,
			"locked": false
		},
		{
			"type": "image",
			"version": 96,
			"versionNonce": 661732876,
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
			"updated": 1704423424117,
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
			"id": "gDph_aKFLSjG5LeJEeNo_",
			"type": "rectangle",
			"x": -406.9482705285815,
			"y": 871.74987223391,
			"width": 80.79998779296875,
			"height": 20.79998779296875,
			"angle": 0,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [
				"pJhYtQozk1mGvh9jWLyDR",
				"vUXmo-KAVbr87GIdP808J",
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"seed": 377029004,
			"version": 73,
			"versionNonce": 1698012300,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1704423424117,
			"link": null,
			"locked": false
		},
		{
			"id": "d3_ei2rLurAMR87tsfboQ",
			"type": "arrow",
			"x": -329.348294942644,
			"y": 890.1498661303943,
			"width": 40.800048828125,
			"height": 10.399993896484375,
			"angle": 0,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [
				"pJhYtQozk1mGvh9jWLyDR",
				"vUXmo-KAVbr87GIdP808J",
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 448408204,
			"version": 153,
			"versionNonce": 415589300,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1704471548584,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					40.800048828125,
					10.399993896484375
				]
			],
			"lastCommittedPoint": null,
			"startBinding": null,
			"endBinding": {
				"elementId": "5hsUN1ul",
				"focus": -0.2537231413493035,
				"gap": 1.39996337890625
			},
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "5hsUN1ul",
			"type": "text",
			"x": -287.1482827356127,
			"y": 897.3498478198475,
			"width": 120.77998352050781,
			"height": 24,
			"angle": 0,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [
				"pJhYtQozk1mGvh9jWLyDR",
				"vUXmo-KAVbr87GIdP808J",
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": null,
			"seed": 1500752948,
			"version": 134,
			"versionNonce": 1376315788,
			"isDeleted": false,
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
			"updated": 1704423424117,
			"link": null,
			"locked": false,
			"text": "只能分配给P0",
			"rawText": "只能分配给P0",
			"fontSize": 20,
			"fontFamily": 4,
			"textAlign": "left",
			"verticalAlign": "top",
			"baseline": 18,
			"containerId": null,
			"originalText": "只能分配给P0",
			"lineHeight": 1.2
		},
		{
			"id": "CfbD0S_UrMZDCR1z4O5en",
			"type": "arrow",
			"x": -222.14828273561272,
			"y": 927.74987223391,
			"width": 8.7999267578125,
			"height": 26.399993896484375,
			"angle": 0,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [
				"pJhYtQozk1mGvh9jWLyDR",
				"vUXmo-KAVbr87GIdP808J",
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 350793780,
			"version": 248,
			"versionNonce": 81725108,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1704471548585,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					-8.7999267578125,
					26.399993896484375
				]
			],
			"lastCommittedPoint": null,
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
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "g2EqVbJq",
			"type": "text",
			"x": -307.7483803918627,
			"y": 960.5498600268787,
			"width": 320.5799560546875,
			"height": 48,
			"angle": 0,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [
				"pJhYtQozk1mGvh9jWLyDR",
				"vUXmo-KAVbr87GIdP808J",
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": null,
			"seed": 175640716,
			"version": 156,
			"versionNonce": 2020721548,
			"isDeleted": false,
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
			"updated": 1704423424117,
			"link": null,
			"locked": false,
			"text": "P0运行完后，需要归还已分配的资源\n0 0 1 0",
			"rawText": "P0运行完后，需要归还已分配的资源\n0 0 1 0",
			"fontSize": 20,
			"fontFamily": 4,
			"textAlign": "left",
			"verticalAlign": "top",
			"baseline": 42,
			"containerId": null,
			"originalText": "P0运行完后，需要归还已分配的资源\n0 0 1 0",
			"lineHeight": 1.2
		},
		{
			"id": "-FbZrOp4qzGLSH4YnrZkF",
			"type": "arrow",
			"x": -269.348294942644,
			"y": 1014.1498966479724,
			"width": 20.79998779296875,
			"height": 36.79998779296875,
			"angle": 0,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [
				"pJhYtQozk1mGvh9jWLyDR",
				"vUXmo-KAVbr87GIdP808J",
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 2136847924,
			"version": 263,
			"versionNonce": 2066475444,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1704471548585,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					-20.79998779296875,
					36.79998779296875
				]
			],
			"lastCommittedPoint": [
				-20.79998779296875,
				36.79998779296875
			],
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
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "VH8VYxsT",
			"type": "text",
			"x": -332.3483559778002,
			"y": 1057.5498600268786,
			"width": 226.4599609375,
			"height": 24,
			"angle": 0,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [
				"pJhYtQozk1mGvh9jWLyDR",
				"vUXmo-KAVbr87GIdP808J",
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": null,
			"seed": 64587188,
			"version": 126,
			"versionNonce": 1050516876,
			"isDeleted": false,
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
			"updated": 1704423424117,
			"link": null,
			"locked": false,
			"text": "所以可使用资源为2 4 4 1",
			"rawText": "所以可使用资源为2 4 4 1",
			"fontSize": 20,
			"fontFamily": 4,
			"textAlign": "left",
			"verticalAlign": "top",
			"baseline": 18,
			"containerId": null,
			"originalText": "所以可使用资源为2 4 4 1",
			"lineHeight": 1.2
		},
		{
			"id": "Xo3W8kyCHj4vCU-nLEUYz",
			"type": "arrow",
			"x": -332.548246114519,
			"y": 1078.1498966479724,
			"width": 36.800048828125,
			"height": 17.5999755859375,
			"angle": 0,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [
				"pJhYtQozk1mGvh9jWLyDR",
				"vUXmo-KAVbr87GIdP808J",
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 216923572,
			"version": 265,
			"versionNonce": 2010909876,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1704471548585,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					-36.800048828125,
					17.5999755859375
				]
			],
			"lastCommittedPoint": [
				-36.800048828125,
				17.5999755859375
			],
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
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "ia5FYkmt",
			"type": "text",
			"x": -528.9482705285815,
			"y": 1096.5498600268786,
			"width": 161.21998596191406,
			"height": 24,
			"angle": 0,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [
				"pJhYtQozk1mGvh9jWLyDR",
				"vUXmo-KAVbr87GIdP808J",
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": null,
			"seed": 271081524,
			"version": 126,
			"versionNonce": 722237324,
			"isDeleted": false,
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
			"updated": 1704423424117,
			"link": null,
			"locked": false,
			"text": "又只能够给P3提供",
			"rawText": "又只能够给P3提供",
			"fontSize": 20,
			"fontFamily": 4,
			"textAlign": "left",
			"verticalAlign": "top",
			"baseline": 18,
			"containerId": null,
			"originalText": "又只能够给P3提供",
			"lineHeight": 1.2
		},
		{
			"id": "osewX_0_WsUQ-OIerGzXX",
			"type": "arrow",
			"x": -538.9482705285815,
			"y": 1112.5498600268786,
			"width": 41.5999755859375,
			"height": 3.20001220703125,
			"angle": 0,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [
				"pJhYtQozk1mGvh9jWLyDR",
				"vUXmo-KAVbr87GIdP808J",
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 1487842868,
			"version": 245,
			"versionNonce": 723480500,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1704471548586,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					-41.5999755859375,
					-3.20001220703125
				]
			],
			"lastCommittedPoint": [
				-41.5999755859375,
				-3.20001220703125
			],
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
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "soKqDiJ4",
			"type": "text",
			"x": -623.9482705285815,
			"y": 1100.5498600268786,
			"width": 40,
			"height": 24,
			"angle": 0,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [
				"pJhYtQozk1mGvh9jWLyDR",
				"vUXmo-KAVbr87GIdP808J",
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": null,
			"seed": 2016248500,
			"version": 83,
			"versionNonce": 71192972,
			"isDeleted": false,
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
			"updated": 1704423424117,
			"link": null,
			"locked": false,
			"text": "……",
			"rawText": "……",
			"fontSize": 20,
			"fontFamily": 4,
			"textAlign": "left",
			"verticalAlign": "top",
			"baseline": 18,
			"containerId": null,
			"originalText": "……",
			"lineHeight": 1.2
		},
		{
			"id": "dEgKcouQ9QLVgNg7F31-9",
			"type": "arrow",
			"x": -630.5483071496752,
			"y": 1110.9498234057849,
			"width": 40,
			"height": 4,
			"angle": 0,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [
				"vUXmo-KAVbr87GIdP808J",
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 1456625804,
			"version": 144,
			"versionNonce": 2032538292,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1704471548586,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					-40,
					4
				]
			],
			"lastCommittedPoint": [
				-40,
				4
			],
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
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "e9dbQ5JL",
			"type": "text",
			"x": -938.7483193567065,
			"y": 1102.5497989917224,
			"width": 263.8799133300781,
			"height": 24,
			"angle": 0,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [
				"vUXmo-KAVbr87GIdP808J",
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": null,
			"seed": 814684812,
			"version": 91,
			"versionNonce": 1353919372,
			"isDeleted": false,
			"boundElements": [
				{
					"id": "dEgKcouQ9QLVgNg7F31-9",
					"type": "arrow"
				}
			],
			"updated": 1704423424117,
			"link": null,
			"locked": false,
			"text": "能找到序列为P0 P3 P4 P2 P1",
			"rawText": "能找到序列为P0 P3 P4 P2 P1",
			"fontSize": 20,
			"fontFamily": 4,
			"textAlign": "left",
			"verticalAlign": "top",
			"baseline": 18,
			"containerId": null,
			"originalText": "能找到序列为P0 P3 P4 P2 P1",
			"lineHeight": 1.2
		},
		{
			"id": "YQGmLVGJvy4Gz9H9x76If",
			"type": "line",
			"x": -943.348294942644,
			"y": 1128.5498600268786,
			"width": 276,
			"height": 0.79998779296875,
			"angle": 0,
			"strokeColor": "#2f9e44",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 817070772,
			"version": 50,
			"versionNonce": 414103692,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1704423424117,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					276,
					-0.79998779296875
				]
			],
			"lastCommittedPoint": [
				276,
				-0.79998779296875
			],
			"startBinding": null,
			"endBinding": null,
			"startArrowhead": null,
			"endArrowhead": null
		},
		{
			"id": "jsleP9HS",
			"type": "text",
			"x": -812.348294942644,
			"y": 1137.3498478198474,
			"width": 300.0799865722656,
			"height": 24,
			"angle": 0,
			"strokeColor": "#2f9e44",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": null,
			"seed": 141657396,
			"version": 89,
			"versionNonce": 1977599756,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1704423424117,
			"link": null,
			"locked": false,
			"text": "只要能找到一个序列那就是安全的",
			"rawText": "只要能找到一个序列那就是安全的",
			"fontSize": 20,
			"fontFamily": 4,
			"textAlign": "left",
			"verticalAlign": "top",
			"baseline": 18,
			"containerId": null,
			"originalText": "只要能找到一个序列那就是安全的",
			"lineHeight": 1.2
		},
		{
			"id": "F6UPgqmSHc18k8p_WZsHk",
			"type": "rectangle",
			"x": -816.1482827356127,
			"y": 1136.5498600268786,
			"width": 314.4000244140625,
			"height": 30.39996337890625,
			"angle": 0,
			"strokeColor": "#2f9e44",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"seed": 584823180,
			"version": 58,
			"versionNonce": 1458242956,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1704423424117,
			"link": null,
			"locked": false
		},
		{
			"id": "NUAdStGjHa2NDlMXkSjsj",
			"type": "line",
			"x": -624.5483071496752,
			"y": 1061.3498478198474,
			"width": 160,
			"height": 0.79998779296875,
			"angle": 0,
			"strokeColor": "#e03131",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 1904624180,
			"version": 51,
			"versionNonce": 554333196,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1704423424117,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					160,
					0.79998779296875
				]
			],
			"lastCommittedPoint": [
				160,
				0.79998779296875
			],
			"startBinding": null,
			"endBinding": null,
			"startArrowhead": null,
			"endArrowhead": null
		},
		{
			"id": "darq4BtekGAtnQ0qJw_Em",
			"type": "arrow",
			"x": -495.7482583215502,
			"y": 1061.3498478198474,
			"width": 236.79998779296875,
			"height": 66.4000244140625,
			"angle": 0,
			"strokeColor": "#1971c2",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 470810164,
			"version": 109,
			"versionNonce": 1975098420,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1704471548586,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					236.79998779296875,
					66.4000244140625
				]
			],
			"lastCommittedPoint": [
				236.79998779296875,
				66.4000244140625
			],
			"startBinding": null,
			"endBinding": {
				"elementId": "5U1QKuoi",
				"focus": 0.21459805987653058,
				"gap": 10.39996337890625
			},
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "5U1QKuoi",
			"type": "text",
			"x": -317.7482583215502,
			"y": 1138.149835612816,
			"width": 213.23992919921875,
			"height": 24,
			"angle": 0,
			"strokeColor": "#1971c2",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [
				"vLxHgxg_US29unF-W7KeY"
			],
			"frameId": null,
			"roundness": null,
			"seed": 1188364980,
			"version": 70,
			"versionNonce": 1496178956,
			"isDeleted": false,
			"boundElements": [
				{
					"id": "darq4BtekGAtnQ0qJw_Em",
					"type": "arrow"
				}
			],
			"updated": 1704423424117,
			"link": null,
			"locked": false,
			"text": "说明尚需资源为0 10 7 2",
			"rawText": "说明尚需资源为0 10 7 2",
			"fontSize": 20,
			"fontFamily": 4,
			"textAlign": "left",
			"verticalAlign": "top",
			"baseline": 18,
			"containerId": null,
			"originalText": "说明尚需资源为0 10 7 2",
			"lineHeight": 1.2
		}
	],
	"appState": {
		"theme": "light",
		"viewBackgroundColor": "#ffffff",
		"currentItemStrokeColor": "#1971c2",
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
		"scrollX": 1008.8150104374357,
		"scrollY": -471.41650838299876,
		"zoom": {
			"value": 0.7499999999999998
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