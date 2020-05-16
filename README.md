# SALOME-Mecaの使用法解説

* [Code_Aster](https://www.code-aster.org/)とは熱・構造問題ソルバーです。
* [Salome](https://www.salome-platform.org/)とは物理シミュレーションの汎用プラットフォームす。

  [Salome-Meca](https://www.code-aster.org/)=Salome+Code_Aster（ソフト的統合）


[OpenCAE Users Wiki](http://opencae.gifu-nct.ac.jp/pukiwiki/index.php?OpenCAE%20Users%20Wiki)にあるFS氏ご提供の「[SALOME-Mecaの使用法解説](http://opencae.gifu-nct.ac.jp/pukiwiki/index.php?SALOME-Meca%A4%CE%BB%C8%CD%D1%CB%A1%B2%F2%C0%E2)」をSalome-Meca2019（Code_Aster14.4）用いて設定を行いました。

各フォルダには、メッシュファイル(.med)とCode_Asterコマンドファイル(.comm)が含まれています。

## 1.0 基本 Salomeの使い方
Wizard（Add Stage with Assistant）＞Isotropic liner elasticity（等方性線形弾性）による手順
* [単純な片持ち梁](https://github.com/JunTatsuno/Code_Aster/tree/master/basic)：basic-bar.comm basic-bar.med

## 2.0 境界条件の設定

## 3.0 複合材料の設定
複合材とは材質の異なる形状のものが組み合わさって構成されるモデルです。
その材質が異なる境界面ではモデルの節点が共有されており、全体としてのモデルはSolidが1個になるという考え方です。
* [2種類の材料で構成されるモデル](https://github.com/JunTatsuno/Code_Aster/tree/master/multiP)：multi-bar-1.comm multi-bar-1.med

## 4.0 部品の連結
複数のSolidを境界面ではモデルの節点を共有せずに連結（結合）してAssyを作り、Assyの線形解析を行います。
* [部品間の隙間が無いモデルの場合](https://github.com/JunTatsuno/Code_Aster/tree/master/Assy)：multi-bar-1.comm multi-bar-1.med
* [部品間に隙間があるモデルの場合](https://github.com/JunTatsuno/Code_Aster/tree/master/Assy)：multi-bar-1-1.comm multi-bar-1-1.med
* [連結（結合）の定義方法の確認](https://github.com/JunTatsuno/Code_Aster/tree/master/Assy)

## 5.0 線形熱応力
静的に熱応力を計算します。
温度は均一に分布しているものとして線形の弾性解析を行います。
* [単純モデルの場合](https://github.com/JunTatsuno/Code_Aster/tree/master/thermal-bar)：bar-100.comm bar-100.med
* [Bi-Metalのモデルの場合](https://github.com/JunTatsuno/Code_Aster/tree/master/thermal-circle)：circle2.comm circle2.med

## 6.0 接触解析の基本
2個のSolidが接触した状態で、荷重や変位を相手に伝えて変形していく問題です。
接触面ですべりが生じたり、変形とともに接触位置が変わっていく問題をとくために、負荷（荷重や位置）を少しずつかけていき、その都度、解を求めて最終的な解を求める非線形解析を行います。
* 単純モデルの場合
* 接触面積が増加するモデルの場合
* 接触面積が減少するモデルの場合

## 6.1 接触解析（摩擦あり）
接触問題を解くにあたって、通常は、その接触面に摩擦力が働きます。
そのため、ここで接触面にすべりが発生し、摩擦力が働くものとして、接触問題を解きます。
* 変位拘束の接触解析（摩擦あり）
* 荷重拘束の接触解析（摩擦あり）

## 7.0 塑性変形の基本
* [単純な片持ち梁](https://github.com/JunTatsuno/Code_Aster/tree/master/plastic)：bar.comm bar.med
* [円柱の圧縮](https://github.com/JunTatsuno/Code_Aster/tree/master/plastic-pole)：plastic-pole.comm pole.med

## 7.1 塑性（負荷を変化）
* 変位拘束
* 荷重拘束

## 7.2 塑性（結果の検証）

## 8.0 塑性と接触
* 単純モデルの場合
* かしめのモデルの場合
* 治具による かしめのモデルの場合

## 9.0 熱応力と弾塑性（基本）

## 9.1 熱応力と弾塑性（はんだ）
* 線形熱応力解析
* 非線形熱応力解析

## 10.0 モーダル解析
Wizard（Add Stage with Assistant）＞Modal analysys（モーダル解析）による手順
* [単純モデルの解析](https://github.com/JunTatsuno/Code_Aster/tree/master/modal)：bar100.comm bar100.med
* [L字モデルの解析](https://github.com/JunTatsuno/Code_Aster/tree/master/modal)：modal-bar.comm modal-bar.med

## 11.0 周波数応答（減衰無）

## 11.1 周波数応答（減衰有）

## 12.0 動解析（過渡応答）

## 13.0 熱流解析
Wizard（Add Stage with Assistant）＞Liner thermal analysis（線形熱解析）による手順

## 14.0 温度構造錬成解析（１）

## 14.1 温度構造錬成解析（２）

## 15.0 温度構造解析連携

## 16.0 シェル解析（基本）
* [1次メッシュの場合](https://github.com/JunTatsuno/Code_Aster/tree/master/shell-1P)：DKTshel-1P.comm DKTshel-1P.med
* [高次メッシュの場合](https://github.com/JunTatsuno/Code_Aster/tree/master/shell-1P)：COQUEshell-1P.comm COQUEshell-1P.med

## 16.1 シェル解析（複数シェル）

## 16.2 シェル解析（シェルとソリッド）

## License
All content is licensed under an open-source, 'copyleft' license:
[Attribution 4.0 International (CC BY 4.0) ](https://creativecommons.org/licenses/by/4.0/)
![Attribution 4.0 International (CC BY 4.0) ](http://i.creativecommons.org/l/by/3.0/88x31.png)
