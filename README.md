# bugList

# FBReactNativeSpec, PhaseScriptExecution failed with a nonzero exit codeFBReactNativeSpec，PhaseScriptExecution
    find-node.sh 找到的路径有问题
    可能是我自己重新安装过路径的原因
    解决方案
    which node 找到node 本机路径
    在选择目标的 Xcode 中，点击 Build Phases 并打开 Bundle React Native code and image
    NODE_BINARY=node node 替换为路径
    FBReactNativeSpec 到 cp 脚本里把find-node 去掉直接复制node 路径
