# API迭代 {#ApiUpgrade .reference}

## 产品迭代 {#Upgrade .section}

max\{20, 当前系统盘容量\}

\[max\{20, 参数ImageId对应的镜像大小\}, 500\]

长度为\[2, 128\]个大小写英文或中文字符，必须以大小字母或中文开头，可包含数字、点号（.）、半角冒号（:）、下划线（\_）或连字符（-）。

-   cloud：普通云盘
-   cloud\_efficiency：高效云盘
-   cloud\_ssd：SSD云盘
-   ephemeral\_ssd：本地SSD盘

-   cloud：\[5, 2000\]
-   cloud\_efficiency：\[20, 32768\]
-   cloud\_ssd：\[20, 32768\]
-   ephemeral\_ssd：\[5, 800\]

