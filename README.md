# Hanzi Writer Wechat Miniprogram Plugin (小程序定义组件)

This component can be used in a Wechat miniprogram to add Hanzi Writer for character stroke animations and quizzing.

## Installation

```
npm install hanzi-writer-miniprogram
```

## Usage

In your `page.json`, first add the following to enable the `hanzi-writer-view` component:

```json
{
  "usingComponents": {
    "hanzi-writer-view": "hanzi-writer-miniprogram/hanzi-writer-view"
  }
}
```

Then, add a `hanzi-writer-view` component to your page. You must add an `id`, `width`, and `height`, like below:
```
<hanzi-writer-view id="hz-writer" width="300" height="300" />
```

Then in your page, you can control the view via `createHanziWriterContext(<id>)`, like below:

```javascript
import createHanziWriterContext from 'hanzi-writer-miniprogram';

Page({
  onLoad: function() {
    this.writerCtx = createHanziWriterContext({
      id: 'hz-writer',
      character: '你',
      page: this,
      charDataLoader: (char) => { /* char data loading logic here */ },
    });

    // You can call any normal HanziWriter method here
    this.writerCtx.loopCharacterAnimation();
  }
});
```

This method requires the `id` from the `hanzi-writer-view` component in wxml, the current page, and a `charDataLoader`. Unfortunately, network access is restricted inside of miniprograms, so you'll need to handle loading character data yourself. You can [read more about loading character data here](https://chanind.github.io/hanzi-writer/docs.html#loading-character-data-link).

You can also pass any other normal Hanzi Writer options to `createHanziWriterContext`, except for `width` and `height` which are set in the `hanzi-writer-view` component. You can see a [full list of options here](https://chanind.github.io/hanzi-writer/docs.html#api-link).

## Further Documentations

For more info and docs on Hanzi Writer check out https://chanind.github.io/hanzi-writer

## Data source

The chinese character svg and stroke order data used by Hanzi Writer is derived from the [Make me a Hanzi](https://github.com/skishore/makemeahanzi) project with some slight tweaks. The data can be found in the [Hanzi Writer Data](https://github.com/chanind/hanzi-writer-data) repo. There's a visualizer for this data [here](https://chanind.github.io/hanzi-writer-data).

## Contributing

Pull requests are welcome! If you would like to contribute code, you'll need to be able to build the project locally. After cloning the Hanzi Writer repo, you can get it set up by running:

```
yarn install
```

## LICENSE

Hanzi Writer is released under an [MIT](https://raw.githubusercontent.com/chanind/hanzi-writer/master/LICENSE) license.

The Hanzi Writer data comes from the [Make Me A Hanzi](https://github.com/skishore/makemeahanzi) project, which extracted the data from fonts by [Arphic Technology](http://www.arphic.com/), a Taiwanese font forge that released their work under a permissive license in 1999. You can redistribute and/or modify this data under the terms of the Arphic Public License as published by Arphic Technology Co., Ltd. A copy of this license can be found in [ARPHICPL.TXT](https://raw.githubusercontent.com/chanind/hanzi-writer-data/master/ARPHICPL.TXT).
