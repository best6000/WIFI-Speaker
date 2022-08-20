## WIFI—Speaker
项目简介：一个基于ESP8266的、使用MQTT协议的、采用NodeRed实现播放控制的WIFI播放器。
### 特别鸣谢
- 感谢instructables这个网站，以后闲着没事可以瞎逛，等我成为英语大神就往上传项目。
- 感谢万能的Arduino库，果然想做什么都有先人写好了库给我用🤓
- 感谢MrDIY先生已经实现了我所有想要的功能
　　项目原地址:https://www.instructables.com/MQTT-Audio-Notifier-for-ESP8266-Play-MP3-TTS-RTTL/
　　视频地址:https://www.youtube.com/watch?v=SPa9SMyPU58
- 感谢aspork42先生做了一个圆圆的火箭🚀外壳，但是我懒得打印直接用以前的收音机壳子了！值得一提的是aspork42先生做出了改进允许多个设备订阅不同的主题，实现不同设备的单独控制。也可以选择订阅相同主题，实现不同房间的同步播放。
　　项目原地址:https://github.com/aspork42/speaker
- 感谢一盏电灯up主提供的随机获取网易云热歌榜歌曲以及NodeRed结合HomeAssistant实现播放控制的思路。
### 基本功能
- 推送mp3文件播放
- 音量控制
- 接入百度tts实现文本转语音功能(MrDiy先生的tts太难用了)
### 目前使用场景
- 改造老旧的有源音箱，放在院子里当广播用（给草坪浇水的时候必须要听歌！）
- 厕所里接一个3w的喇叭就可以实现非常响的音量（让我颇为震惊）不听歌能洗澡？
### 硬件连接
　　硬件上的连接比较简单，ESP8266 mini D1 的RX脚输出音频信号，直接输出大概可以驱动0.5w的喇叭，大概就是蚊子叫吧。可以使用软件模拟DAC接一个三极管放大后输出，但是我没有测试过。为了得到较好的音质，推荐使用硬件DAC方案，MAX98357支持I2S，同时还集成了一个功率放大模块，可以驱动3w的喇叭（4欧姆的比较响）。
| ESP8266 | MAX98357 |
| ------- | -------- |
| D4      | LRC      |
| D8      | BCLK     |
| RX      | DIN      |
| 5V      | VIN      |
| GND     | GND      |

<img src="/Users/best/Library/Application Support/typora-user-images/image-20220820232218612.png" alt="image-20220820232218612" style="zoom:25%;" />

### 软件部分

