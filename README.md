## 依赖

-   Angular >=6.0.0

## 下载使用

```bat
npm install @dllcn/ngx-clipboard --save
```

在你module文件,例如 `app.module.ts`导入:

```ts
import { ClipboardModule } from '@dllcn/ngx-clipboard';
...
imports: [
...
    ClipboardModule,
...
]
```



如果您使用systemjs加载文件，则可能需要更新配置：

```js
System.config({
    map: {
        'ngx-clipboard': 'node_modules/@dllcn/ngx-clipboard'
    }
});
```

### 复制

-   设置 `cbContent` 属性

```html
<button ngxClipboard [cbContent]="'target string'">Copy</button>
```

您可以指定父**容器**以避免焦点问题.

```html
<div #container>
    <button ngxClipboard [cbContent]="'target string'" [container]="container">Copy</button>
</div>
```

-   设置输入目标

```html
....

<input type="text" #inputTarget />

<button [ngxClipboard]="inputTarget">Copy</button>
```

-   使用`ClipboardService`中的`copyFromContent`来复制动态创建的文本。

```ts
import { ClipboardService } from 'ngx-clipboard'

...

constructor(private _clipboardService: ClipboardService){
...
}

copy(text: string){
  this._clipboardService.copyFromContent(text)
}
```

### 回调

-   使用`$ event：{isSuccess：true，content：string}复制成功后触发`cbOnSuccess`回调属性

```html
<button (cbOnSuccess)="copied($event)" [cbContent]="'example string'">Copied</button>
```

或者直接更新参数

```html
<button (cbOnSuccess)="isCopied = true" [cbContent]="'example string'">Copied</button>
```

-   使用`$ event：{isSuccess：false}复制失败时会触发`cbOnError`回调属性

### Conditionally render host

您还可以使用结构指令\*ngxClipboardIfSupported来有条件地呈现主机元素

```html
<button ngxClipboard *ngxClipboardIfSupported [cbContent]="'target string'" (cbOnSuccess)="isCopied = true">Copy</button>
```


[参考]: <> (https://github.com/maxisam/ngx-clipboard)
