# droidbot-datasets

[Click here to see the UTG demo!](https://tanuncle.github.io/droidbot-datasets/)

## Folder Description

- `data explore` 文件夹下存放各种 APP 的 explore results；其子文件夹，如 `voicerecorder explore` 存放对单个 APP 的explore result。
- `data explore/voicerecorder explore` 文件夹包含如下内容：
  - `1706273204448.mp4` ：以开始时间戳命名的录屏。11分钟的录屏文件为370M，超出了git上传最大100M的限制，故没有上传。
  - `action_i.png` ：执行动作 *i* 之前，用户看到的界面。
  - json file
    - `UI Task Raw.json` ：Android 端标注出的原始数据（trace log）。
    - `UI Task.json` ：使用 OCR 提取点击坐标，处理 windowStateChanged action 和 提取不到 click 的组件的情况。 
    - `UI Task Combined.json` ：对 input 动作和 scroll 动作进行合并。
    - `UI Task Combined Plus.json`： merge 系统自动产生的多余动作。
    - `UI Task Combined Plus Check.json` ：**Final Result！** 剔除 pageInfo 为空的 action。
- `utg.js`：Voice Recorder 的 utg。
- `index.html` ：Voice Recorde 的 utg 可视化界面。 
- `droidbot.apk` ：标注数据集的 Android APP 安装包。

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
- Json Lines: 319696 + 417438 = 737134
- Actions: 351 + 428 = 779
- Screen Recording Duration: 10min 45s + 14min 18s = 25min 3s
- To get the two apps' `UI Task Combined Plus Check.json` and `utg.js`, the total running time is about **1.5h**.

## Notes on dataset annotation

### 中文

1. 打开设置，搜索 `指针位置`，将该功能打开，屏幕上方会出现一个坐标条。
2. 第一次打开 DroidBot 时，会请求存储权限，请选择允许。
3. 打开 DroidBot 之后，会自动跳转到设置中的无障碍功能界面，你需要找到 DroidBot，并为其打开无障碍功能。
4. 在下拉框中选择标注的 APP，在 `请输入你的任务` 输入框中输入 `标注的 app 名字 explore`。（对同一个 APP 的多次标注，取不同的名称，如加上序号，否则只能记录最新的一个）
5. 点击 `开始任务`，会有“是否允许录屏”的提示框，点击允许。（如果 `开始任务` 按钮为不可点击状态，请完全关闭该 APP，然后重新启动，并重新为 DroidBot 打开无障碍功能。如果系统显示已经打开无障碍功能，那就关闭并重新打开）
   - **注意**：每次点击、输入之后，等待 1s~2s 的时间，每次滑动界面之后，等待 3s 左右的时间。输入的值如果能够直接在输入框中显示，输入得不要太快。

6. 任务完成时，将通知栏滑下，会有 DroidBot 正在录制屏幕的通知，点击该通知，任务结束。
   - **注意**：如果通知栏没有显示正在录制屏幕的通知，说明此次任务没有正确启动，请回到 DroidBot，重新开始任务。

7. 在你手机的文件管理 APP 的内部存储中，会出现一个名为 DroidBot 的文件夹，长按该文件夹，选择压缩，将压缩包发给我即可。

### English

1. Open Settings, search for `pointer location` and turn the feature on. After that, a coordinate bar will appear at the top of the screen. 
2. When you open DroidBot for the first time, storage permissions are requested, select Allow.
3. Open DroidBot. It will first automatically jump to the Accessibility screen in Settings, where you need to find DroidBot and turn on accessibility for it.
4. Select the labeled APP in the drop-down box and enter `labeled app name + explore` in the  `请输入你的任务`  input box. (For multiple annotations of the same APP, take different names, e.g. add serial number, otherwise only the latest one will be recorded)
5. Click `开始任务`, there will be a pop-up box "Allow screen recording", click allow. (If the `开始任务` button is not clickable, close the app completely, then restart it and turn on accessibility for DroidBot again. If the system shows that accessibility has been turned on, then close and turn it back on)
   - **Caution**: Wait for 1s~2s after each click and input, and wait for about 3s after each scroll. If the input value can be displayed directly in the input box, don't input it too fast.
6. When the task is finished, slide down the notification bar, there will be a notification that DroidBot is recording the screen, click on the notification, the task is finished.
   - **Caution**: If the notification bar does not show a notification that the screen is being recorded, this task was not started correctly, so go back to DroidBot and restart the task.
7. In the internal storage of your phone's file management app, a folder named DroidBot will appear, long press the folder, select Compress, and send the compressed package to me.