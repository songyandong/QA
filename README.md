# QA
npm install 疯狂失败的问题。
结果是node版本和npm版本不一致的问题。另外主要注意node最新版支持的npm不是最新版。
https://github.com/npm/npm/issues/19989
https://nodejs.org/en/download/

%1.降低npm版本,将npm版本降到4.x  npm -g i npm@4
%2.删除C:/用户/user/.npmrc文件
3.清除npm缓存 npm cache clean --force
4.设置资源淘宝镜像 执行以下命令
npm config set registry https://registry.npm.taobao.org
npm --registry https://registry.npm.taobao.org info underscore
5.安装vue 脚手架 npm install -g vue-cli
6.搭建项目 vue init webpack projectName


primeng
组件p-spinner并没有[style]属性,如果指定并不存在的属性,老版本的谷歌浏览器会包Cannot set property style of [object Object] which has only a getter


js
Json.stringif方法转换Date对象是的UTC时间问题
谷歌格式2017/4/20,IE格式2017年4月20日(不能重新转成日期对象),各种浏览器各种不同格式......,自己拼或直接使用第三方moment.js.
Date.prototype.toJSON = function () {
    var result = this.getFullYear() + '-' + (this.getMonth() * 1 + 1) + '-' + this.getDate();
    return result;
}
jquery.printarea.js 应用到有body{height:100%}样式的页面上,将会导致打印时出现一个空白页.
需要在生成html的时候再body上加上height:auto.


ng2
IE浏览器Get方法缓存问题
重写HTTP模块的get方法,添加一个随机时间戳参数.
@Injectable()
class NewHttp extends Http {
    constructor(_backend: ConnectionBackend, _defaultOptions: RequestOptions) {
        super(_backend, _defaultOptions);
    }

    get(url: string, options?: RequestOptionsArgs): Observable<Response> {
        在url上添加timestamp
    }

    /* post(...)
     ...*/
}


css
数字的折行样式:word-wrap: break-word;
超长显示...时,可以指定百分比长度.


ionic2 微信浏览器安全支持
sanitizer: DomSanitizer:安卓机可以,苹果机器不行.
