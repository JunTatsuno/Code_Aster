# SALOME-Mecaの使用法解説

* Code_Asterとは熱・構造問題ソルバーです。
* Salomeとは物理シミュレーションの汎用プラットフォームす。

Salome-Meca=Salome+Code_Aster（ソフト的統合）


[OpenCAE Users Wiki](http://opencae.gifu-nct.ac.jp/pukiwiki/index.php?OpenCAE%20Users%20Wiki)にあるFS氏ご提供の「[SALOME-Mecaの使用法解説](http://opencae.gifu-nct.ac.jp/pukiwiki/index.php?SALOME-Meca%A4%CE%BB%C8%CD%D1%CB%A1%B2%F2%C0%E2)」をSalome-Meca2019（Code_Aster14.4）用いて設定を行いました。

各フォルダには、メッシュファイル(.med)とCode_Asterコマンドファイル(.comm)が含まれています。

## 1.0 基本 Salomeの使い方
Wizard（Add Stage with Assistant）＞Isotropic liner elasticity（等方性線形弾性）による手順
* [単純な片持ち梁](https://github.com/JunTatsuno/Code_Aster/tree/master/basic)：basic-bar.comm basic-bar.med

## 2.0 境界条件の設定

## 3.0 [複合材料の設定](https://github.com/JunTatsuno/Code_Aster/tree/master/multiP)
複合材とは材質の異なる形状のものが組み合わさって構成されるモデルです。
その材質が異なる境界面ではモデルの節点が共有されており、全体としてのモデルはSolidが1個になるという考え方です。

## 4.0 [部品の連結](https://github.com/JunTatsuno/Code_Aster/tree/master/Assy)

## 6.0 接触解析の基本

## 6.1 接触解析（摩擦あり）

## 5.0 線形熱応力
静的に熱応力を計算します。
温度は均一に分布しているものとして線形の弾性解析を行います。
* [単純モデルの場合](https://github.com/JunTatsuno/Code_Aster/tree/master/thermal-bar)
* [Bi-Metalのモデルの場合](https://github.com/JunTatsuno/Code_Aster/tree/master/thermal-circle)

## 7.0 塑性変形の基本
* [単純な片持ち梁](https://github.com/JunTatsuno/Code_Aster/tree/master/plastic)
* [円柱の圧縮](https://github.com/JunTatsuno/Code_Aster/tree/master/plastic-pole)

## 7.1 塑性（負荷を変化）

## 7.2 塑性（結果の検証）

## 8.0 塑性と接触

## 9.0 熱応力と弾塑性（基本）

## 9.1 熱応力と弾塑性（はんだ）

## 10.0 [モーダル解析](https://github.com/JunTatsuno/Code_Aster/tree/master/modal)
Wizard（Add Stage with Assistant）＞Modal analysys（モーダル解析）による手順
* 単純モデルの解析：bar100.comm bar100.med
* L字モデルの解析：modal-bar.comm modal-bar.med

## 11.0 周波数応答（減衰無）

## 11.1 周波数応答（減衰有）

## 12.0 動解析（過渡応答）

## 13.0 熱流解析
Wizard（Add Stage with Assistant）＞Liner thermal analysis（線形熱解析）による手順

## 14.0 温度構造錬成解析（１）

## 14.1 温度構造錬成解析（２）

## 15.0 温度構造解析連携

## 16.0 シェル解析（基本）
* 1次メッシュの場合
* 高次メッシュの場合

## 16.1 シェル解析（複数シェル）

## 16.2 シェル解析（シェルとソリッド）
