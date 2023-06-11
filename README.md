<div align="center">
<img src="https://raw.githubusercontent.com/Yidadaa/ChatGPT-Next-Web/main/docs/images/icon.svg" alt="icon"/>

<h1 align="center">luci-app-openai</h1>

<h3 align="center">ChatGPT - Build your own AI assistant.</h3>

</div>

-----------

它来自 [Yidadaa/ChatGPT-Next-Web](https://github.com/Yidadaa/ChatGPT-Next-Web)，使用 [node-pkg](https://github.com/vercel/pkg) 工具封装而成，它适用于官方 [OpenWrt](https://github.com/openwrt)  aarch64 & x86_64 架构的固件使用。



-----------


## How to build

- Enter in your openwrt dir

- Openwrt official SnapShots

  ```shell
  git clone https://github.com/sbwml/luci-app-openai package/openai
  make menuconfig # choose LUCI -> Applications -> luci-app-openai
  make V=s
  ```

------------

![1](https://github-production-user-asset-6210df.s3.amazonaws.com/16485166/244598987-fd01152e-86b9-45fd-93da-3418098b5b23.png)

![2](https://github-production-user-asset-6210df.s3.amazonaws.com/16485166/244598997-e1a88ca4-0682-41e1-a5d5-3658e2bc8220.png)

![3](https://github-production-user-asset-6210df.s3.amazonaws.com/16485166/244599003-8040b42c-6ac2-4dea-b555-d33e76885a5b.png)
