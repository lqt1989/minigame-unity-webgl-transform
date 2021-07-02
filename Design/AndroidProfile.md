# 使用Android CPU Profiler性能调优
1. 在Android微信小游戏打开调试进行录制

   <image src='../image/androidprofile1.png' width="300"/>

2. 停止性能数据录制

    与步骤1相似，在相同的菜单中选择Stop CPU Profile

3. 传输录制文件到PC
   
    录制结束后，Android会生成一份xxx.cpuprofile，该文件格式可以使用chrome进行解析。
因此我们需要将录制后的文件传输到PC使用chrome进行分析。
文件路径通常为：Android/data/com.tencent.mm/MicroMsg/appbrand/trace
<image src='../image/androidprofile2.png' width="300"/>


4. 利用PC(Windows/Mac)的chrome加载数据

    <image src='../image/androidprofile3.png' width="500"/>

5. 使用JavaScriptProfile进行数据分析
   
    <image src='../image/androidprofile4.png' width="700"/> 

注意：仅当导出Develop版本时才能在函数堆栈中看到函数名称，否则为函数ID，此时有两种做法进行解读：
1. 通过webgl导出目录下的symbols文件对照映射
2. 通过[替换脚本](../tools/update_v8_wasm_profile.py)对cpuprofile进行自动映射到真实函数。使用方式：python update_v8_wasm_profile.py $cpuprofile $symbol

   