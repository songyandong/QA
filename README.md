# QA
primeng
组件p-spinner并没有[style]属性,如果指定并不存在的属性,老版本的谷歌浏览器会包Cannot set property style of [object Object] which has only a getter

js
Json.stringif方法转换Date对象是的UTC时间问题
谷歌格式2017/4/20,IE格式2017年4月20日(不能重新转成日期对象),各种浏览器各种不同格式......,自己拼或直接使用第三方moment.js.
Date.prototype.toJSON = function () {
    var result = this.getFullYear() + '-' + (this.getMonth() * 1 + 1) + '-' + this.getDate();
    return result;
}

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
