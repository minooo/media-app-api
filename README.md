# media-app-api
新媒体接口调用方式，仿微信

```js
// 登陆
wx.navigateTo({
  path: "/login",
  back: `${window.location.origin}/sight-audio/${data.id}` // 登陆成功后需要继续跳转的页面，如果没有，则默认跳到首页
})

// 分享
wx.onShare({
  title: data.title, // 分享标题
  desc: data.introduce, // 分享描述
  link: window.location.href, // 分享链接
  imgUrl: "http://public.duduapp.net/new-media/app/static/avatar.png", // 分享图标
})

```
