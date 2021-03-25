### Charles 安装证书后依旧抓取不到https请求

手机端安装了Charles证书依然不能抓取https请求，我们可以从一下几点进行排查：

- 查看手机系统：Android 27及以上版本不在信任用户证书。

 1. 配置信任用户证书

     android:networkSecurityConfig="@xml/network_security_config"，在配置文件中加入：
   
     ```
     <network-security-config>
         <base-config >
            <trust-anchors>
                ...
                <certificates src="user" />
            </trust-anchors>
         </base-config>
     </network-security-config>
     ```
- 手机端安装抓包工具证书

- mac安装charles根证书，并且在钥匙串 -> 登陆 -> 找到Charles证书，选择始终信任。
- 检查Charles SSL设置是否正确，Proxy -> SSL Proxying Settings ->  SSL Proxying -> Enable SSL Proxying，然后add，Host，port都输入 *，当然也可以根据自己需求设置。