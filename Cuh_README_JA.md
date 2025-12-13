
# Cuh
CuhはHelicalにMIDI出力・Scale/WavetableのCVコントロール機能を追加するエクスパンダーです。

## ⚠️ Warning
Cuhを使用せずにHelicalをMIDI機器などに接続すると、過電流が発生し本体が故障する可能性があります。
この場合、本製品の保証対象外となります。

以下の機能が追加されます。
1. USB-MIDI/TRS<b>(TypeA)</b>-MIDI経由での、Helicalのノート情報及び、全てのノブのCC信号の出力。
2. Scale/WavetableのCVコントロール用のインプット。

<span style="color: red">
CuhはMIDI Deviceとしてのみ動作します。MIDIHostとして使用したい場合は別途他メーカーから販売されている変換等を購入してください。
</span>  

---
# Controls and Outputs

### MIDI Output(USB-C/TRS-MIDI)
Helicalのノート情報及び、ノブのCC信号を出力します。 
- Orbitにジャックが接続されていない場合：
  - 全てのノート情報は、[`midiChArc`で設定](#notecc-output)したチャンネルから出力されます。
- Orbitにジャックが接続されている場合：
  - 各出力に対応したノート情報が、それぞれ[設定されたチャンネル](#notecc-output)から出力されます。
。

<pre>
Helicalは非常に高速なMIDI送信に対応しており、最大で1秒間に999のMIDIメッセージを出力可能です。ノート情報はCCより優先的に送信されます。
</pre>

### Scale CV IN
Scaleのプリセットに対するCV入力です。現在選択されているスケールとは関係なく、0-5VがScaleの1-16番に対応しています。

### Wavetable CV IN
Wavetableのプリセットに対するCV入力です。現在選択されているWavetableとは関係なく、0-5VがWavetableの1-8番に対応しています。

---
# Velocity Setting
Cuhから出力されるノート情報のベロシティは、HelicalのDynamicSettingで設定された値により決定されます。   
### 設定方法
1. ScaleKnobをダブルクリックして、DynamicSettingModeに入ります。  
(LEDが高速で点滅します)
1. reloAd(左下のボタン)を押しながらScaleノブを回転させることで、音量の範囲の中心を設定します。
2. relOad(右下のボタン)を押しながらScaleノブを回転させることで、音量の幅を設定します。
3. Scaleノブをクリックすることで通常のModeに戻ります。
- 大まかな範囲はHelical本体のLEDに表示されます。もし正確な値に調整したい場合はSDカード内のsetting.txtファイルをPC等で開き、volCenterとvolWidthに0-100の値を記入してください。単位は%です。  
  SDカードのedit可能パラメーターについてはこちら。
- MIDI出力のベロシティは0-127にリマップした値が反映されます。
---
# Note/CC Output
全てのNote/CCMessageは、CuhのUSB OutおよびTRS MIDI Outから出力されます。  
SDCardのmidiSetting.txtのmidiChArc・midiChOrbit・midiCCChの数値を変更することで、それぞれの出力Chを変更する事ができます。  
Orbitにジャックが接続されていない場合、全てのノート情報はmidiChArcから出力されます。
### `midiSetting.txt` Parameters

| midiSettingName  | detail |  Range
| ---- | ---- | ---- |
| midiChArc |Set Arc MIDI Ch| 1 ~ 16 |
| midiChOrbit | Set Orbit MIDI Ch | 1 ~ 16 |
| ccEnable |Set Enable CC| 0 or 1 (Off/On)|
| midiCCCh | Set CC Ch | 1 ~ 16 |
| ccPoly | Set Poly CC number | 1 ~ 127 |
| ccRoot | Set Root CC number | 1 ~ 127 |
| ccGlide | Set Glide CC number | 1 ~ 127 |
| ccSpread | Set Spread CC number | 1 ~ 127 |
| ccHelicity | Set Helicity CC number | 1 ~ 127 |
| ccWave | Set Wave CC number | 1 ~ 127 |
| ccEnv | Set Env CC number | 1 ~ 127 |
| ccLock | Set Lock CC number | 1 ~ 127 |
| ccCutoff | Set Cutoff CC number | 1 ~ 127 |
| ccQ | Set Q CC number | 1 ~ 127 |
| ccIndex | Set Index CC number | 1 ~ 127 |
| ccFilterType | Set Lp-Hp CC number | 1 ~ 127 |
| ccLength | Set Length CC number | 1 ~ 127 |


### sample
```setting.txt
midiChArc 1
midiChOrbit 2
midiCCCh 1
ccPoly 20
ccRoot 21
ccGlide 22
ccSpread 23
ccHelicity 24
ccWave 25
ccEnv 26
ccLock 27
ccCutoff 28
ccQ 29
ccIndex 30
ccFilterType 31
ccLength 32
ccEnable 0
```

---
# How to Install
図の様にCuh付属のUSBCableを接続してください。  
<pre>
認識しない(CuhのLEDが光らない)場合は、電源を切り、もう一度接続し直してください。  
*多少の硬さがあるので、折らない様慎重に接続してください。
</pre>
---
# Update firmware

v2.08以降対応しています。Helicalのシリアルが367番以降であればアップデートの必要はありません。


HelicalのGitHubのページからファームウェア（binファイル）をダウンロードしてください。  
<a href = "https://electro-smith.github.io/Programmer/">Daisy Web Programmer</a> のページに移動し、記載されている手順に従ってファームウェアをアップロードしてください。  
DaisySeedからUSBケーブルを抜いた後、ユーロラックケースの電源を入れて、ファームウェアのアップデートが正常に行われているか確認してください。 

---
# Specification
Width : 4HP  
Max Depth: 30mm  
Maximum current draw:
* 20mA @12V
* 5mA @-12V

CV input range: 0-5V (depends on the knob position)

---
# Warranty

Sdkc Instrumentsは、本製品の購入日から1年間、材料および製造上の欠陥がないことを保証します（購入証明書や領収書が必要です）。

不適切な電源電圧、Eurorackバスボードケーブルの逆接続、製品の誤使用、ノブの取り外し、フェイスプレートの交換、非公式のファームウェア更新を含む許可されていない改造、その他Sdkc Instrumentsがユーザーの責任と判断した原因による不具合は保証対象外となり、その場合は通常の修理料金が適用されます。

また、過度な高温や湿気などの極端な環境条件による損傷も保証対象外となります。

保証サービスが必要な場合は、購入された販売店にお問い合わせください。保証対象となる不具合が確認された場合、Sdkc Instrumentsは製品の修理または交換を行います。

本製品の使用や誤使用によって生じた人身事故や物的損害について、Sdkc Instrumentsは一切の責任を負いません。ご不明点がある場合は、sdkc.store[a]gmail.com またはお近くの販売店までお問い合わせください。

# Contact
下記のアドレスにご連絡ください。[a]を@に置き換えてください。

sdkc.store[a]gmail.com