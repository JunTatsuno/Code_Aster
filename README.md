# SALOME-Mecaの使用法解説

* [Code_Aster](https://www.code-aster.org/)とは熱・構造解析ソルバーです。
* [Salome](https://www.salome-platform.org/)とは物理シミュレーションの汎用プラットフォームです。

  [Salome-Meca](https://www.code-aster.org/)=Salome+Code_Aster（ソフト的統合）


[OpenCAE Users Wiki](http://opencae.gifu-nct.ac.jp/pukiwiki/index.php?OpenCAE%20Users%20Wiki)にあるFS氏ご提供の「[SALOME-Mecaの使用法解説](http://opencae.gifu-nct.ac.jp/pukiwiki/index.php?SALOME-Meca%A4%CE%BB%C8%CD%D1%CB%A1%B2%F2%C0%E2)」をSalome-Meca2019（Code_Aster14.4）用いて設定を行いました。

各フォルダには、メッシュファイル(.med)とCode_Asterコマンドファイル(.comm)が含まれています。

## 1.0 基本 Salomeの使い方
荷重の負荷方法として圧力荷重（面に垂直方向の圧力）の設定を行います。
Wizard（Add Stage with Assistant）＞Isotropic liner elasticity（等方性線形弾性）による手順です。
* [単純な片持ち梁](https://github.com/JunTatsuno/Code_Aster/tree/master/basic)：basic-bar.comm basic-bar.med

## 2.0 境界条件の設定
Wizard（Add Stage with Assistant）では圧力荷重しか設定ができません。
面、線、点に各方向の荷重を付加する、あるいは変位を設定して解析を行います。
* [面に働く荷重で指定](https://github.com/JunTatsuno/Code_Aster/tree/master/bar-2)：FORCE_FACE.comm bar-2.med
* [線に働く荷重で説明](https://github.com/JunTatsuno/Code_Aster/tree/master/bar-2)：FORCE_ARETE bar-2.med
* [点に働く荷重で説明](https://github.com/JunTatsuno/Code_Aster/tree/master/bar-2)：FORCE_NODALE.comm bar-2.med
* [変位の設定](https://github.com/JunTatsuno/Code_Aster/tree/master/bar-2)：DDL_IMPO.comm bar-2.med

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
材料の応力と歪の関係が弾性域では比例しているため、構造解析（線形）の解は容易に求めることができますが、塑性域に入りますと、応力と歪の関係が線形ではなく、非線形となるため、解を求めることが難しくなります。
* [単純な片持ち梁](https://github.com/JunTatsuno/Code_Aster/tree/master/plastic)：bar.comm bar.med
* [円柱の圧縮](https://github.com/JunTatsuno/Code_Aster/tree/master/plastic-pole)：plastic-pole.comm pole.med

## 7.1 塑性（負荷を変化）
弾塑性変形はモデルに負荷をかけて変形（弾性変形＋塑性変形）させた後、負荷を取り除いても塑性変形が残り、元の形状には戻りません。
このような解析を行うには塑性変形させた後に負荷を取り除くことになりますので、負荷の大きさを時間的に変化させ解析する必要があります。
* [変位拘束](https://github.com/JunTatsuno/Code_Aster/tree/master/plastic-pole-reloded)
* [荷重拘束](https://github.com/JunTatsuno/Code_Aster/tree/master/plastic-pole-reloded)

## 7.2 塑性（結果の検証）

## 8.0 塑性と接触
塑性問題を扱う中で、加工（かしめ加工やプレス加工）を考えると、接触と塑性の解析が必要になってきます。
例えば、プレス加工を考えたとき、パンチが材料を押し潰し、塑性変形させて加工します。
パンチと材料は接触して、パンチが材料を塑性変形させますので、塑性変形と接触を同時に扱う非線形解析を行う必要があります。

* [単純モデルの場合](https://github.com/JunTatsuno/Code_Aster/tree/master/plastic-contact-ASTK)：mutli-bar-pl.comm mutli-bar-pl.med
* [かしめのモデルの場合](https://github.com/JunTatsuno/Code_Aster/tree/master/plastic-contact-ASTK)：pole-ring-pl.comm pole-ring-pl.med
* [治具による かしめのモデルの場合](https://github.com/JunTatsuno/Code_Aster/tree/master/plastic-contact-ASTK)：pole-ring-jig-pl.comm pole-ring-jig-pl.med

## 9.0 熱応力と弾塑性（基本）
P板製品のように素子がはんだ付けされている製品で、部品の熱応力によって、はんだに歪みが発生してクラックに至るケースがあります。
このような場合のはんだ歪（塑性歪）の解析います。
* [単純な片持ち梁](https://github.com/JunTatsuno/Code_Aster/tree/master/thermo-bar)：bar.comm bar.med

## 9.1 熱応力と弾塑性（はんだ）
9.0 熱応力と弾塑性（基本）では、単純な四角柱モデルを使いましたが、チップレジスタのはんだ歪を解析します。
* [線形熱応力解析](https://github.com/JunTatsuno/Code_Aster/tree/master/solder-chipR)：chip-sol.comm chip-sol.med
* [非線形熱応力解析](https://github.com/JunTatsuno/Code_Aster/tree/master/solder-chipR)：chip-sol.comm chip-sol-pl.med

## 10.0 モーダル解析
構造解析を行う場合、構造物の固有振動数が、どこにあるのか、また、その周波数で共振した場合、どのような形状で共振しているかが問題になることがあります。
共振して構造物が破壊する場合、これらのことがわかれば対策がとれます。
ここでは固有振動数と変形形状を解析（モーダル解析）します。
Wizard（Add Stage with Assistant）＞Modal analysys（モーダル解析）による手順です。
* [単純モデルの解析](https://github.com/JunTatsuno/Code_Aster/tree/master/modal)：bar100.comm bar100.med
* [L字モデルの解析](https://github.com/JunTatsuno/Code_Aster/tree/master/modal)：modal-bar.comm modal-bar.med

## 11.0 周波数応答（減衰無）

## 11.1 周波数応答（減衰有）

## 12.0 動解析（過渡応答）

## 13.0 熱流解析
モデルの1部に発熱部がある場合のモデル各部の温度分布を求めます。
Wizard（Add Stage with Assistant）＞Liner thermal analysis（線形熱解析）による手順です。
* [L字モデルの解析](https://github.com/JunTatsuno/Code_Aster/tree/master/thermo)：bar2.comm bar2.med

## 14.0 温度構造錬成解析（１）

## 14.1 温度構造錬成解析（２）

## 15.0 温度構造解析連携

## 16.0 シェル解析（基本）
シェルは2Dの平面であり、板厚が無いので、メッシュを切ったとき、メッシュ数が少なくてすみます。
簡単なシェルモデルを使って解析を行います。
* [1次メッシュの場合](https://github.com/JunTatsuno/Code_Aster/tree/master/shell-1P)：DKTshel-1P.comm DKTshel-1P.med
* [高次メッシュの場合](https://github.com/JunTatsuno/Code_Aster/tree/master/shell-1P)：COQUEshell-1P.comm COQUEshell-1P.med

## 16.1 シェル解析（複数シェル）

## 16.2 シェル解析（シェルとソリッド）

## License
All content is licensed under an open-source, 'copyleft' license:
[Attribution 4.0 International (CC BY 4.0) ](https://creativecommons.org/licenses/by/4.0/)
![Attribution 4.0 International (CC BY 4.0) ](http://i.creativecommons.org/l/by/3.0/88x31.png)
