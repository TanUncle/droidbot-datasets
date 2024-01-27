# droidbot-datasets

## Folder Description

- `data explore` 文件夹下存放各种 APP 的 explore results；其其文件夹，如 `voicerecorder explore` 存放对单个 APP 的explore result。
- `data explore/voicerecorder explore` 文件夹包含如下内容：
  - `1706273204448.mp4` ：以开始时间戳命名的录屏。11分钟的录屏文件为370M，超出了git上传最大100M的限制，故没有上传。
  - `action_i.png` ：执行动作 *i* 之前，用户看到的界面。
  - json file
    - `UI Task Raw.json` ：Android 端标注出的原始数据（trace log）。
    - `UI Task.json` ：使用 OCR 提取点击坐标，处理 windowStateChanged action 和 提取不到 click 的组件的情况。 
    - `UI Task Combined.json` ：对 input 动作和 scroll 动作进行合并。
    - `UI Task Combined Plus.json`： merge 系统自动产生的多余动作
    - `UI Task Combined Plus Check.json` ：**Final Result！** 剔除 pageInfo 为空的 action 。

## Included Actions

1. click
2. longClick
3. input（delete）：合并为一个 textChange
4. scroll
5. back：返回键
6. home：返回主界面
7. end：任务结束，默认的最后一个 action

## Runtime test

- APPs: Voice Recorder(simple mobile tools)、Clock(simple mobile tools)
- json lines: 319696 + 417438 = 737134
- actions: 351 + 428 = 779
- To get UI Task Combined Plus Check.json and utg.js, the total running time is about an hour and a half.