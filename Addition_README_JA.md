
# Addition
AdditionはHelicalを拡張するエクスパンダーです。

以下の機能が追加されます。

1. 16個全てのオシレーターへ個別のSVF Filterの追加。
2. 音量のエンベロープの長さの調整。

<div style="text-align: center">

[![helical demo](http://img.youtube.com/vi/6yBOZIw-G4k/0.jpg)](https://youtu.be/6yBOZIw-G4k](https://youtu.be/6yBOZIw-G4k))
</div>

<div style="page-break-before:always"></div>

# Controls and Outputs

<div style="text-align: center">
    <img src="ManualData/Addition_panel_Image.png" width="10%">
</div>

### Cutoff
* SVF FilterのCutoff Frequencyを調整します。
  
  Cutoff FrequencyはKeyTrackingされており、つまみが10時の時に、自身のオシレーターの周波数と一致します。

### Q 
* SVF FilterのQを調整します。

### Index
* 自身の音量のエンベロープをCutoff Frequencyでモジュレーションする量を調整します。
  
  つまみの位置が12時で、モジュレーション無し、CCWで負の方向へのモジュレーション、CWで正の方向へモジュレーションがかかります。

### LP-HP
* SVF FilterのLowpass,Bandpass,Highpassの出力ミックスのバランスを調整します。
  CCWでLP、12時でBandPass、CWでHPとなります。


### Length
* 音量エンベロープの長さを調整します。
  
  このつまみで設定された音の長さは、AutoregressiveSynthesisで決定された音の長さには影響を与えず、CWで元々の音の長さ、CCWで非常に短いパルスの様な音になります。元々の音の長さに影響は与えないので、Helicalには存在しなかった無音を挿入することが可能になります。
  
# Connection
付属のExpanderCableを使用し、Helicalに12pin端子、Addition側に10pinの端子を接続してください。

<b>Additionは電源を必要としません。必ずAddition付属のケーブル(電源ケーブルでの接続はできません)を必ず使用してください。電源ケーブルなどを繋いで接続した場合の故障は保証対象外になります。</b>


# Update firmware

v1.2以降対応しています。Helicalのシリアルが99番以降であればアップデートの必要はありません。

v1.1でも動作いたしますが、フィルターの動作に関するアップデートが含まれている為、アップデートを強くお勧め致します。

HelicalのGitHubのページからファームウェア（binファイル）をダウンロードしてください。  
<a href = "https://electro-smith.github.io/Programmer/">Daisy Web Programmer</a> のページに移動し、記載されている手順に従ってファームウェアをアップロードしてください。  
DaisySeedからUSBケーブルを抜いた後、ユーロラックケースの電源を入れて、ファームウェアのアップデートが正常に行われているか確認してください。  
Helicalの背面にあるシリアル番号が6から98の場合、出荷時のファームウェアはv1.11です。

# Specification
Width : 4HP  
Max Depth: 30mm  
Maximum current draw:
* 0mA @12V
* 0mA @-12V

CV input range: +/- 5V (depends on the knob position)