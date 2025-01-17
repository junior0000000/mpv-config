# mpv-config
- [mpv-config](#mpv-config)
- [mpv-gif.js](#mpv-gifjs)
  - [运行环境需求](#运行环境需求)
  - [feature](#feature)
  - [配置说明](#配置说明)
  - [快捷键说明](#快捷键说明)
- [switch-audio-channel.js](#switch-audio-channeljs)
  - [feature](#feature-1)
  - [快捷键说明](#快捷键说明-1)

# mpv-gif.js

给你的mpv添加制作gif，webp动图的功能，除此之外，还能裁剪音频和视频。

使用`g`指定开始时间，`G`指定结束时间。

然后就可以用快捷键生成这段时间的gif，视频或是音频。

个人更推荐使用webp动图，如果你上传的平台支持的话，webp动图体积更小画质也更好

## 运行环境需求

需要ffmepg的命令行工具，并且要放在环境变量里。

## feature

* 截取gif或者webp动图，支持带字幕截取，支持外挂字幕。（注意可能有些字幕格式是不支持的。默认会截取第一个字幕或第一个外挂字幕，外挂字幕需要和文件名相同才会引入）
* 无损截取音频
* 无损截取视频

## 配置说明

你可以在js文件内进行配置。

dir目前是没用的，本来是用来指定存放动图的目录，但是个人没有这个需求，就懒得做了。

frameSize你也可以用`1280*720`这样来指定,我这里的默认设置是原视频的三分之一的长和宽，8帧

其他选项下面有注释

```javascript
// 用户可配置的选项
const userOptions = {
  dir: mp.get_property('working-directory'),
  //帧大小
  frameSize: 'iw/3:ih/3',
  //帧率 fps: 15,
  fps: 8,
  // 设置动图循环播放次数,0是无限循环播放
  loop: 0,
  // 是否带声音
  audio: false,
}
```

## 快捷键说明

| 键位   | 作用                 |
| ------ | -------------------- |
| g      | 设置起始时间         |
| G      | 设置结束时间         |
| Ctrl+g | 生成gif动图          |
| Ctrl+G | 生成带字幕的gif动图  |
| Ctrl+w | 生成webp动图         |
| Ctrl+W | 生成带字幕的webp动图 |
| Ctrl+a | 截取音频             |
| Ctrl+v | 截取视频             |





# switch-audio-channel.js

这个插件主要是个人在听一些asmr音频时萌发的需求。

因为很多情景下都是对你单边耳朵进行操作的，有时候就一直只攻击你的一只耳朵，这时候你可能就会想把左耳朵和右耳朵切换一下就好了，最简单的方法就是把耳机左右耳换一下。但是有了这个插件，你就节省了这个操作。

还有一个神奇的双耳mix模式，就是两个耳朵都分别混音了左声道和右声道。但是注意，这个模式并没有立体声的效果。两边耳朵都是左声道和右声道的mix，但是结果是失去了立体声的效果。（左右都是100%的音量mix，因此看左右声道一样的视频，比如一般的动漫你会感觉声音变大了。）

个人也不是很清楚其中的原理。

所以如果你想体验两只耳朵被攻击的感觉，建议开两个mpv，一个切换左右声道，同时播放就是立体声了。

## feature

* 切换左声道和右声道
* 将左声道和右声道都设置为左声道，或者都设置为右声道
* 将左右声道，变成原来左右声道的mix

## 快捷键说明

快捷键很方便记忆，

* t toggle
* l left
* r right
* I init

| 键位        | 作用                   |
| ----------- | ---------------------- |
| alt+t       | 左右声道互换           |
| alt+l       | 左右声道都播放左声道   |
| alt+r       | 左右声道都播放右声道   |
| alt+shift+l | 单左声道（右边静音）   |
| alt+shift+r | 单右声道  （左边静音） |
| alt+a       | 左右声道mix模式        |
| shift+alt+i | 重置成立体声双声道     |
