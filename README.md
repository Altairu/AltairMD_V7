# [**AltairMD_V7**](https://github.com/Altairu/AltairMD_V7)
![](image/MD_kairozu_all.png)
![](image/MD_PCB_all.png)
![](image/MD.png)

https://github.com/Altairu/AltairMD_V7
---
### **仕様**
* 30V~10V(フォトカプラを変更すると10V以下も可)
* 最大40A 

|SDs|Ps1|Ps2|出力|
|:----:|:----:|:----:|:----:|
|HIGH|LOW	|LOW	|停止|
|HIGH|LOW	|HIGH	|逆転|
|HIGH|HIGH	|LOW	|正転|
|HIGH|HIGH	|HIGH	|`ブレーキ`（非推奨）|
|LOW|X	|X	|0|
### **降圧**
![](image/三端子.png)
![](image/三端子PCB.png) 
### **三端子レギュレーター** 
### **[NJM7812SDL1]()**
* **12Vに降圧**
* **端子が3つ(入力・グラウンド・出力）**
* **三端子レギュレータは落とした分の電圧をすべて`熱`として消費**
* **ダイオード**
レギュレータに逆電流が流れるのを防止
* **コンデンサ**
コンデンサは入力側と出力側に0.1～10[uF]程度入れるのが一般的


---
## **フォトカプラ**
![](image/フォトカプラ.png)

### [TLP152](https://akizukidenshi.com/catalog/g/g110824/)
* 取り付け様式:	SMD/SMT	
* パッケージ/ケース:SOIC-6
* 電源電圧min.：10V
* 電源電圧max.：30V
* 出力電流：2A
* 入力電流max.：20mA
* 上昇応答時間：95ns
* 下降応答時間：110ns


---
## **MOSFET**
[**RSJ400N10**](https://www.rohm.co.jp/products/mosfets/small-signal/single-nch/rsj400n10-product)
Nch 100V 40A Power MOSFET

![](image/fet.png)

* 4V駆動タイプ
* Nチャンネル　パワーMOSFET
* 高速スイッチング
* 駆動回路が簡単
* 並列使用が容易

ゲート抵抗は10[Ω]で設定している

---
### **ハーフブリッジゲートドライバ**
### [**IR2302STRPBF**](https://akizukidenshi.com/catalog/g/g115656/)
![](image/ir2302PCB.png) 
![](image/ir2302_2.png) 
* IN端子
ハイサイドMOSFETをONにするか、ローサイドMOSFETをONにするかの切り替えを行う
Hが入力されるとハイサイド、Lが入力されるとローサイドがONとなる
**ハイサイドにNchMOSFETを使うためにブーストラップ回路を使用**
* ブートストラップコンデンサの容量は[10uF]
* ブートストラップダイオード
(ファストリカバリダイオード)
* `100％出力は不可`
ブートストラップ回路の制約で
コンデンサのチャージ時間が必要.

# Ｈブリッジ回路
![width:1000px](image/HブリッジPCB.png) 

---
<br>
<br>

| Ps1 | Ps2 | Q1  | Q2  | Q3  | Q4  | 1    | 2    | 
| :----: | :----: | :----: | :----: | :----: | :----: | :----: | :----: | 
| L   | L   | H   | L   | H   | L   | open | open | 
| L   | H   | H   | H   | L   | L   | L    | H    | 
| H   | L   | L   | L   | H   | H   | H    | L    | 
| H   | H   | H   | H   | H   | H   | L    | L    | 

# 正回転

![bg right:60% width:500px](image/1_files/4f8aed0cbb3d233e4912fb6e8aac236a.png)

[Hatena Electronics](https://practicalelectronicsblog.com/hbridge/)

# 逆回転
![bg right:60% width:500px](image/1_files/165cf2e3f7085f0288b2cf0e68efcce5.png)

[Hatena Electronics](https://practicalelectronicsblog.com/hbridge/)

# ブレーキ
![bg right:60% width:500px](image/1_files/498ec3ddbcb9075836d5a820f88e3163.png)

[Hatena Electronics](https://practicalelectronicsblog.com/hbridge/)

https://practicalelectronicsblog.com/hbridge/  より
