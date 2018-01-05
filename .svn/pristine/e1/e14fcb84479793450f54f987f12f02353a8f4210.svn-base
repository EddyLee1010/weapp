//index.js
//获取应用实例
var app = getApp()

Page({
     data: {
        imgUrls: [
        'http://img02.tooopen.com/images/20150928/tooopen_sy_143912755726.jpg',
        'http://img06.tooopen.com/images/20160818/tooopen_sy_175866434296.jpg',
        'http://img06.tooopen.com/images/20160818/tooopen_sy_175833047715.jpg'
        ]
        },
     onLoad: function (options) {
       var that = this;
      //  页面加载时，通过接口获得文章的分类
        wx.request({
            url: 'https://www.liziqiang.net/index.php/api/index/getColumn', //仅为示例，并非真实的接口地址
          header: {
            'content-type': 'application/json'
          },
          success: function (res) {
            that.setData({
              "columnList" : res.data
            })
          }
        })
     },

     dload:function(){

         const downloadTask = wx.downloadFile({
             url: 'https://www.liziqiang.net/static/admin/images/metro.png', //仅为示例，并非真实的资源
             success: function (obj) {
                 console.log(obj)
                 var tempFilePaths = obj.tempFilePath
                 wx.saveFile({
                     tempFilePath: tempFilePaths,
                     success: function (res) {
                         console.log(res)
                     }
                 })
             }
         })

         downloadTask.onProgressUpdate((res) => {
             console.log('下载进度', res.progress)
             console.log('已经下载的数据长度', res.totalBytesWritten)
             console.log('预期需要下载的数据总长度', res.totalBytesExpectedToWrite)
         })

     },
     
     onShareAppMessage: function (res) {
       if (res.from === 'button') {
         // 来自页面内转发按钮
         console.log(res.target)
       }
       return {
         title: '自定义转发标题',
         path: '/page/user?id=123',
         success: function (res) {
           // 转发成功
         },
         fail: function (res) {
           // 转发失败
         }
       }
     }
})