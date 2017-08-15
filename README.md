# Cocos Creator Engine API

This repo is for hosting Cocos Creator Engine API website with [Gitbook](https://gitbook.com).

## Markdown Source

The markdown files we use in this repo is generated from [Cocos Creator Engine](https://github.com/cocos-creator/engine) repo, with the help of [Firedoc](https://github.com/cocos-creator/firedoc).

The markdown sources should be put into `en` and `zh` folders according to the language. A list of all sources with link should be generated as `index.md` in each folder.

## Preview Book

```bash
npm install gitbook-cli -g
gitbook install
gitbook serve
```

## Customize Style and Template

To customize styles, modify [zh/styles/website.css](zh/styles/website.css) and [en/styles/website.css](en/styles/website.css).

To change HTML templates, change the content in [zh/_layouts](zh/_layouts) and [en/_layouts](en/_layouts). Check out [Templating Guide](https://toolchain.gitbook.com/templating/) for gitbook.

## Contribution

If you found any error or problem for document contents, or you'd like to submit your modification to the source. Please go to [Cocos Creator engine repo](https://github.com/cocos-creator/engine) and submit a pull request.

You can also just post inline comment when browsering the doc website. We'll update accordingly.