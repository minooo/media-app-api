# media-app-api
新媒体接口调用方式，仿微信

```js
// 登陆
wx.navigateTo(JSON.stringify({
  path: "/login", // 必选
  back: `${window.location.origin}/sight-audio/${data.id}` // 登陆成功后需要继续跳转的页面，如果没有，则默认跳到首页
}))

// 课程
wx.courseTo(JSON.stringify({
  path: `${window.location.origin}/course/${item.id}`, // 必选
  mediaType: `${item.chapter_type === 1 ? item.chapter_media_type : 3}`, // 1音频， 2视频 3图文，如果是图文，原生应该自动隐去视频/音频模块,
  mediaUrl: `${item.chapter_type === 1 ? item.chapter_media_url : ""}`, // 免费的多媒体的url 
  img: item.image
}))

// 视角
wx.sightTo(JSON.stringify({
  path: `${window.location.origin}/sight-audio/${item.id}`, // 必选
}))

// 设置
wx.setTo(JSON.stringify({
  path: "", // 必选
}))

// 无返回参数的登陆
wx.loginTo(JSON.stringify({
  path: "", // 必选
}))

// 分享
wx.onShare(JSON.stringify({
  title: data.title, // 分享标题
  desc: data.introduce, // 分享描述
  link: window.location.href, // 分享链接
  imgUrl: "http://public.duduapp.net/new-media/app/static/avatar.png", // 分享图标
}))

// 下载
wx.downloadFile(JSON.stringify({
  url: data.audio_url // 下载资源的 url，下载成功后原生那边最好给个页面提示,
  title: data.title, // 标题
  created: data.chapters[focus].created_at, // 创建日期
  img: (data.author && data.author.avatar) || "http://public.duduapp.net/new-media/app/static/avatar.png", // 占位图
}))

// 提供页面需要的音频等字段
wx.audioSourse(JSON.stringify({
  url: data.audio_url, // 音频链接
  text: data.audio_text, // 音频文字
  img: (data.author && data.author.avatar) || "http://public.duduapp.net/new-media/app/static/avatar.png",
  title: data.chapters[focus].title,
  mediaType: "1", // 1音频， 2视频 3图文，如果是图文，原生应该自动隐去视频/音频模块
  prev: `${window.location.origin}/sight-audio/${data.prev && data.prev.id}`, // 上一个音频的页面链接，注意这不是音频链接
  next: `${window.location.origin}/sight-audio/${data.next && data.next.id}`, // 下一个音频的页面链接，注意这不是音频链接
}))

// 初始化提供页面需要的音频等字段
wx.audioInitSourse(JSON.stringify({
   url: data.chapters[focus].media_url,
   img: data.chapters[focus].image,
   title: data.chapters[focus].title,
   text: data.chapters[focus].media_url === 1 && data.chapters[focus].content,
   mediaType: `${data.chapters[focus].chapter_type === 1 ? data.chapters[focus].media_type : 3}`,
 }))
 
 // 支付
 wx.pay(JSON.stringify({
    return_code: "SUCCESS",
    return_msg: "OK",
    appid: "wx01754ee3c11b2f17",
    mch_id: "1483129732",
    nonce_str: "dBfGibahLFadbVlr",
    sign: "66A9E13BADBB5C86222FF673A518C9B8",
    result_code: "SUCCESS",
    prepay_id: "wx271056069612794e07eed3fb4126190544",
    trade_type: "APP"
 }))
```
