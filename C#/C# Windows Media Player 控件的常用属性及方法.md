# C# Windows Media Player 控件的常用属性及方法
| 属性/方法名： | 说明： |
|--|--|
| URL:String; |指定媒体位置，本机或网络地址  |
| uiMode:String; |播放器界面模式，可为Full, Mini, None, Invisible  |
|  playState:integer;|播放状态，1=停止，2=暂停，3=播放，6=正在缓冲，9=正在连接，10=准备就绪  |
| enableContextMenu:Boolean; | 启用/禁用右键菜单 |
|fullScreen:boolean;|是否全屏显示|
|controls.play;|播放|
|controls.pause;|暂停|
|controls.stop;|停止|
|controls.currentPosition:double;|当前进度|
|controls.currentPositionString:string;|当前进度，字符串格式。如“00:23”|
|controls.fastForward;|快进|
|controls.fastReverse;|快退|
|controls.next;|下一曲|
|controls.previous;|上一曲|
|settings.volume:integer;|音量大小（范围从0到100）|
|settings.autoStart:Boolean;|设置是否自动播放|
|settings.mute:Boolean;|设置是否静音|
|settings.playCount:integer;|播放次数|
|currentMedia.duration:double;|播放文件的总播放长度|
|currentMedia.durationString:string;|播放文件的总播放长度（返回字符串形式）|
|currentMedia.getItemInfo(const string);|获取当前媒体信息"Title"=媒体标题，"Author"=艺术家，"Copyright"=版权信息，"Description"=媒体内容描述，"Duration"=持续时间（秒），"FileSize"=文件大小，"FileType"=文件类型，"sourceURL"=原始地址|
|currentMedia.setItemInfo(const string);|通过属性名设置媒体信息|
|currentMedia.name:string;|同 currentMedia.getItemInfo("Title")|
|currentPlaylist.count:integer;|当前播放列表所包含媒体数|
|currentPlaylist.Item[integer];|获取或设置指定项目媒体信息，其子属性同wmp.currentMedia|


Player1.URL = ""; //播放地址
Player1.enableContextMenu = false; //显示右键菜单
Player1.uiMode = "none/full"; //界面模式
Player1.Ctlcontrols.play(); //播放
Player1.Ctlcontrols.pause(); //暂停
Player1.Ctlcontrols.stop(); //停止
Player1.Ctlcontrols.previous(); //上一首
Player1.Ctlcontrols.next(); //下一首
Player1.settings.volume = 100; //音量
Player1.settings.mute = true; //静音
Player1.settings.rate = 2; //播放速度
Player1.settings.autoStart = true; //自动播放
Player1.settings.playCount = 1; //播放次数

