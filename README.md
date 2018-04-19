# media-app-api
新媒体接口调用方式，仿微信

```js
// 登陆
wx_navigateTo({
  path: "/login",
  back: `${window.location.origin}/sight-audio/${data.id}` // 登陆成功后需要继续跳转的页面，如果没有，则默认跳到首页
})

// 分享
wx_onShare({
  title: data.title, // 分享标题
  desc: data.introduce, // 分享描述
  link: window.location.href, // 分享链接
  imgUrl: "http://public.duduapp.net/new-media/app/static/avatar.png", // 分享图标
})

// 下载
wx_downloadFile({
  url: data.audio_url // 下载资源的 url，下载成功后原生那边最好给个页面提示
})

```
