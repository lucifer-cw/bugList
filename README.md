# bugList

# FBReactNativeSpec, PhaseScriptExecution failed with a nonzero exit codeFBReactNativeSpec，PhaseScriptExecution
    find-node.sh 找到的路径有问题
    可能是我自己重新安装过路径的原因
    解决方案
    which node 找到node 本机路径
    在选择目标的 Xcode 中，点击 Build Phases 并打开 Bundle React Native code and image
    NODE_BINARY=node node 替换为路径
    FBReactNativeSpec 到 cp 脚本里把find-node 去掉直接复制node 路径


# brew install node link 的时候不能把路径添加到path 不然也会导致node路径不对
    **If you need to have this software first in your PATH run: echo 'export PATH="/usr/local/opt/openssl/bin:$PATH"' >> ~/.bash_profile**
 
    $ echo 'export PATH="/usr/local/opt/node@16/bin:$PATH"' >> ~/.bash_profile
    $ source ~/.bash_profile
    
    默认的node 路径 which node       /usr/local/bin/node 路径不太一样

# DeprecatedColorPropType.js this package itself specifies a `main` module field that could not be resolved
for me none of the above worked but this did: go to : node_modules\deprecated-react-native-prop-types\DeprecatedColorPropType.js
find this line :    const normalizeColor = require('@react-native/normalize-color'); 
and change it to this:      const normalizeColor = require('@react-native/normalize-color/base');

# find DSO to load: libhermes-executor-release.so
    ```
    dependencies {
    // ...

    if (enableHermes) {
+       implementation("com.facebook.react:hermes-engine:+") {
+           exclude group:'com.facebook.fbjni'
+       }
-       def hermesPath = "../../node_modules/hermes-engine/android/";
-       debugImplementation files(hermesPath + "hermes-debug.aar")
-       releaseImplementation files(hermesPath + "hermes-release.aar")
    } else {
        implementation jscFlavor
    }
    }
```
