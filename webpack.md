```javascript
const path = require('path');
const webpack = require('webpack');
const HtmlWebpackPlugin = require('html-webpack-plugin');
const CleanWebpackPlugin = require('clean-webpack-plugin');
const MiniCssExtractPlugin = require("mini-css-extract-plugin");

const config = {
    target: "web",
    devtool: "#source-map",
    entry: {
        index: "./src/js/index.js",
        common: "./src/js/common.js"
    },
    output: {
        filename: './js/[name].[hash].js',
        chunkFilename: './js/[name].[hash].js',
        path: path.resolve(__dirname, 'dist')
    },
    module: {
        rules: [{
            test: /\.html$/,
            loader: 'html-loader'
        }, {
            test: /\.js$/,
            exclude: /node_modules/,
            use: [
                {
                    loader: "babel-loader",
                    options: {
                        presets: [
                            ["env", {
                                "targets": {
                                    "browsers": ["last 15 versions", "safari >= 4", "not ie < 9", "iOS >= 7"]
                                }
                            }],
                        ],
                    }
                }
            ]
        }, {// loader sass and css
            test: /\.(scss|css)$/,
            use: [
                MiniCssExtractPlugin.loader,
                {
                    loader: 'css-loader?modules=false',
                    options: {
                        importLoaders: 1,
                        minimize: true
                    }
                },
                {
                    loader: 'postcss-loader',
                    options: {
                        config: {
                            path: path.resolve(__dirname, './postcss.config.js')
                        }
                    },
                },
                "sass-loader"
            ]
        }, {
            test: /\.(jpg|png|ico|jpeg|gif)$/,
            use: [{
                loader: "file-loader",
                options: {
                    name: "[name].[ext]",
                    publicPath: "./images/",
                    outputPath: "images/"
                }
            }]
        }, {
            test: /\.(eot|svg|ttf|woff)$/,
            use: [{
                loader: "file-loader",
                options: {
                    name: "[name].[ext]",
                    publicPath: "./fonts/",
                    outputPath: "fonts/"
                }
            }]
        }]
    },
    devServer: {
        port: 8088,
        overlay: {
            error: true
        },
        hot: true,
        clientLogLevel: "none",
        open: true
    },
    plugins: [
        new CleanWebpackPlugin(['dist']),
        new MiniCssExtractPlugin({
            filename: "[name].css",
            chunkFilename: "[id].css"
        }),
        new HtmlWebpackPlugin({
            template: 'index.html',
            inject: true
        }),
        new webpack.HotModuleReplacementPlugin(),
        new webpack.NoEmitOnErrorsPlugin(),
    ]
};

module.exports = config;
```
```js
{
  "name": "easy-webpack-4",
  "version": "4.0.0",
  "description": "easy webpack four",
  "main": "src/js/index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "dev": "webpack-dev-server --mode development --config webpack.config.js --progress --watch",
    "build": "webpack --mode production --config webpack.config.js --progress"
  },
  "author": "darlang",
  "license": "MIT",
  "devDependencies": {
    "autoprefixer": "^8.5.0",
    "babel-core": "^6.26.3",
    "babel-loader": "^7.1.4",
    "babel-preset-env": "^1.7.0",
    "babel-preset-stage-3": "^6.24.1",
    "clean-webpack-plugin": "^0.1.19",
    "css-loader": "^0.28.11",
    "file-loader": "^1.1.11",
    "html-loader": "^0.5.5",
    "html-webpack-plugin": "^3.2.0",
    "mini-css-extract-plugin": "^0.4.1",
    "node-sass": "^4.9.0",
    "postcss-loader": "^2.1.5",
    "sass-loader": "^7.0.1",
    "style-loader": "^0.21.0",
    "webpack": "^4.8.3",
    "webpack-cli": "^2.1.3",
    "webpack-dev-server": "^3.1.4"
  },
  "dependencies": {},
  "browserslist": [
    "defaults",
    "not ie < 9",
    "last 15 versions",
    "> 10%",
    "iOS 7",
    "last 10 iOS versions"
  ]
}



class LeftMenuCtrl {
    constructor(isLeftShow, leftMenuData) {
        this.isLeftShow = isLeftShow;
        this.leftMenuData = leftMenuData;
    }

    getPosition() {
        if (this.isLeftShow === false) {
            document.querySelector('.main-sidebar').style.transform = "translateX(0px)";
            document.querySelector('body').style.overflow = 'hidden';
        } else {
            document.querySelector('.main-sidebar').style.transform = "translateX(-230px)";
            document.querySelector('body').style.overflow = 'visible';
        }
        this.isLeftShow = !this.isLeftShow;
    }

    isShow() {
        document.getElementById('showLeft').onclick = () => {
            this.getPosition();
        }
    }

    showLeftData() {
        const ul = document.createElement('ul');
        for (let i = 0; i < this.leftMenuData.length; i++) {
            let li = document.createElement('li');
            li.innerHTML = this.leftMenuData[i].value;
            ul.appendChild(li);
        }
        document.querySelector('.aside-bottom').appendChild(ul);
    }

    init() {
        this.getPosition();
        this.isShow();
        this.showLeftData();
    }
}

export default LeftMenuCtrl;




import './common.js';
import "../css/style.css";
import "../css/common.css";
import "../css/fonts.css";
import "../css/media.css";
import LeftMenuCtrl from './leftMenuCtrl.js';
import ContentDataCtrl from './ContentDataCtrl.js';

(function (window) {
    const leftMenuData = [
        {id: 1, value: 'bjstdmmgbg01/Acceptance_test/Acceptance_test'},
        {id: 2, value: 'bjstdmmgbg02/Acceptance_test'},
        {id: 3, value: 'bjstdmmgbg03/Acceptance_test'},
        {id: 4, value: 'bjstdmmgbg04/Acceptance_test'},
        {id: 5, value: 'bjstdmmgbg05/Acceptance_test'},
        {id: 6, value: 'bjstdmmgbg06/Acceptance_test/Acceptance_test'},
        {id: 7, value: 'bjstdmmgbg07/Acceptance_test'},
        {id: 8, value: 'bjstdmmgbg08/Acceptance_test'},
        {id: 9, value: 'bjstdmmgbg09/Acceptance_test'},
        {id: 10, value: 'bjstdmmgbg10/Acceptance_test'},
        {id: 11, value: 'bjstdmmgbg11/Acceptance_test/Acceptance_test'}
    ];
    const contentData = [
        {
            id: 1,
            name: 'bjstdmngbgr01.thoughtworks.com',
            imgUrl: '../images/windows.png',
            status: 'orange',
            ip: '192.168.1.102',
            path: '/var/lib/cruise-agent',
            iconList: [
                {iconId: 1, iconName: 'Firefox'},
                {iconId: 2, iconName: 'Safari'},
                {iconId: 3, iconName: 'Ubuntu'},
                {iconId: 4, iconName: 'Chrome'}
            ]
        }, {
            id: 2,
            name: 'bjstdmngbgr01.thoughtworks.com',
            imgUrl: '../images/windows.png',
            status: 'orange',
            ip: '192.168.1.102',
            path: '/var/lib/cruise-agent',
            iconList: [
                {iconId: 1, iconName: 'Firefox'},
                {iconId: 2, iconName: 'Safari'},
                {iconId: 3, iconName: 'Ubuntu'},
                {iconId: 4, iconName: 'Chrome'}
            ]
        }, {
            id: 3,
            name: 'bjstdmngbgr01.thoughtworks.com',
            imgUrl: '../images/windows.png',
            status: 'orange',
            ip: '192.168.1.102',
            path: '/var/lib/cruise-agent',
            iconList: [
                {iconId: 1, iconName: 'Firefox'},
                {iconId: 2, iconName: 'Safari'},
                {iconId: 3, iconName: 'Ubuntu'},
                {iconId: 4, iconName: 'Chrome'}
            ]
        }, {
            id: 4,
            name: 'bjstdmngbgr01.thoughtworks.com',
            imgUrl: '../images/windows.png',
            status: 'orange',
            ip: '192.168.1.102',
            path: '/var/lib/cruise-agent',
            iconList: [
                {iconId: 1, iconName: 'Firefox'},
                {iconId: 2, iconName: 'Safari'},
                {iconId: 3, iconName: 'Ubuntu'},
                {iconId: 4, iconName: 'Chrome'}
            ]
        }, {
            id: 5,
            name: 'bjstdmngbgr01.thoughtworks.com',
            imgUrl: '../images/windows.png',
            status: 'orange',
            ip: '192.168.1.102',
            path: '/var/lib/cruise-agent',
            iconList: [
                {iconId: 1, iconName: 'Firefox'},
                {iconId: 2, iconName: 'Safari'},
                {iconId: 3, iconName: 'Ubuntu'},
                {iconId: 4, iconName: 'Chrome'}
            ]
        }
    ];
    let leftMenuCtrl = new LeftMenuCtrl(true, leftMenuData);
    let ContentDataCtrl = new ContentDataCtrl(contentData);
    leftMenuCtrl.init();
})(window);






class ContentDataCtrl {
    constructor(contentData) {
        this.contentData = contentData;
    }

    getData() {
        let content = document.createElement('div');
        content.classList.add('row');
        for (let item of this.contentData) {
            let str = `<div class="item-list col-xs-12 mb20">
                    <div class="item-left-img col-xs-2">
                        <img src="${item.imgUrl}">
                    </div>
                    <div class="item-info-top col-lg-10 col-xs-12">
                        <ul>
                            <li><i class="icon-desktop"></i><span>${item.name}</span></li>
                            <li class="item-status"><span class="bg-green">${item.status}</span></li>
                            <li><i class="icon-info"></i><span>${item.ip}</span></li>
                            <li><i class="icon-folder"></i><span>${item.path}</span></li>
                        </ul>
                    </div>
                    <div class="item-info-bottom col-lg-10 col-xs-12">
                        <i class="add-browser icon-plus"></i>
                        <ul class="browserList"></ul>
                    </div>
                </div>`;
            content.innerHTML += str;
        }
        document.querySelector('.content-list').appendChild(content);
    }
}

export default ContentDataCtrl;
```
