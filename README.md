# README

dependabotのわけのわからないbranchがたくさんできる

## Setup

サイト作成

    $ npx gatsby new gatsby-agency-portfolio https://github.com/cosmicjs/gatsby-agency-portfolio

CosmicJS(https://www.cosmicjs.com/)の管理画面(https://app.cosmicjs.com/buckets)から>Add New Bucket>Start with an App>Gatsby Agency Portfolioでバケット作成

Setting>Basic Settingsを参考に.envを設定

    $ cat .env
    COSMIC_READ_KEY=<Read Key>
    COSMIC_BUCKET_SLUG=<Bucket slug>

> Personal Planに変更しておいたほうがよい

ライブラリ更新

    $ npm install

サーバ起動

    $ cd gatsby-agency-portfolio
    $ gatsby develop

## Github pagesとの連携

gatsby-config.js(リンクのprefixを付加:githubのレポジトリ名に設定すること)

    ...
      pathPrefix: "/gatsby-agency-portfolio",
    }

gatsby-config.js(上記prefixを付加してbuildしpublicディレクトリをgh-pagesブランチにプッシュ)

    ...
    "scripts": {
      ...
      "develop": "gatsby develop",
      "deploy": "gatsby build --prefix-paths && gh-pages -d public",
      "clean": "gatsby clean",
      ...

gh-pagesのインストール

    $ npm install gh-pages --save-dev

GithubにRepository"gatsby-agency-portfolio"を作成後

    $ git remote add origin git@github.com:higebobo/gatsby-agency-portfolio.git
    $ git add -A
    $ git commit -m 'init'
    $ git push -u origin master

デプロイ

    $ npx run deploy

reactが無いというエラーが出た場合

    $ rm -fr package-lock.json node_modules
    $ npm i

## Link

* [https://github\.com/cosmicjs/gatsby\-agency\-portfolio](https://www.gatsbyjs.org/starters/cosmicjs/gatsby-agency-portfolio/)
* [cosmicjs/gatsby\-agency\-portfolio: Portfolio client designed with creative agencies in mind\.](https://github.com/cosmicjs/gatsby-agency-portfolio)
* [GatsbyとNetlifyで簡単にブログを作成 \- Qiita](https://qiita.com/k-penguin-sato/items/7554e5e7e90aa10ae225)
* [How Gatsby Works with GitHub Pages \| GatsbyJS](https://www.gatsbyjs.org/docs/how-gatsby-works-with-github-pages/)
* [Can I change build directory path from public to anything else? · Issue \#14703 · gatsbyjs/gatsby](https://github.com/gatsbyjs/gatsby/issues/14703)
