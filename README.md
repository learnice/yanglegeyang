# yanglegeyang

羊了个羊 降低第二关难度

本方法主要是通过使用抓包 map 数据，修改第二关的“地图”，打包降低难度的目的，所有的操作都是你自己来安全可靠

## 抓包
[Charles 使用教程](https://www.jianshu.com/p/ff85b3dac157)

## 修改数据（截止 20220917）
使用 Charles 抓 cat-match.easygame2021.com 这个域名，获取到两关数据，然后将第一关的数据保存到文件中，map 到第二关的接口上

0. **首先确保你的抓包配置完成！**
是否配置成功的标志是，你进入到游戏中 cat-match.easygame2021.com 这个域名下的接口数据是否能看到，如图就是成功的
<img width="893" alt="截屏2022-09-17 23 04 01" src="https://user-images.githubusercontent.com/18441883/190864394-fcc0eb99-084e-4269-864e-841f6178b6cb.png">

1. 进入游戏后会看到，先后调用了cat-match.easygame2021.com/sheep/v1/game/map_info_new?map_id=xxx 接口两次，第一次 map_id=80001，第二次是 map_id=90017，它们分别返回了对应关卡数据的 md5。这个接口更新的很频繁，昨天它返回的还是当前关卡的所有数据（现在关卡数据 https://cat-match-static.easygame2021.com/maps/ 由这个接口下发）

2. 猜测当游戏运行的时候，会通过这个 md5 找到对应的游戏数据，然后运行。所以我们把 map_id=90017（第二关） 的返回内容的 md5，修改为 map_id=80001（第一关）返回的 md5 就可以了

3. 将 map_id=80001 返回的内容保存到本地，比如在桌面创建个文件 map.txt，然后将 map_id=80001 返回的内容保存到这个文件中，保存文件

4. 在 Charles 找到 map_id=90017 右键选择 Map Loccal，然后将 Map To 设置为你上一步保存的 map.txt 文件，下一次再调用 map_id=90017 接口时，你在 Charles 中看到 map_id=90017 返回的内容，就是你刚才保存文件中的内容了
<img width="427" alt="截屏2022-09-17 23 19 03" src="https://user-images.githubusercontent.com/18441883/190864426-295f0b1a-4bca-4ee1-97c4-ded55c0c23b2.png">

5. 重启游戏，到了第二关你会发现和第一关一样了，我相信你很容易就能过关！

0xff. 基本操作就是这样，办法有很多，你甚至可以改它关卡的数据，你可以使用自己喜欢的方法

## 进羊群
https://user-images.githubusercontent.com/18441883/190634528-62896dd8-1cdc-44db-b374-3780fa730391.mp4

## 声明
本项目仅供学习交流，严禁用作商业行为！
因他人私自不正当使用造成的违法违规行为与本人无关！
如有任何问题可联系本人删除！


## Buy yourself a cup of coffee
如果您玩的开心的话，可以给自己买杯咖啡，放下手机好好学习、生活！
