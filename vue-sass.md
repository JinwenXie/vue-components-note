### sass
    安装：
        cnpm install --save-dev sass-loader
        //sass-loader依赖于node-sass
        cnpm install --save-dev node-sass

    在build文件夹下的webpack.base.conf.js的rules里面添加配置
        {
            test: /\.sass$/,
            loaders: ['style', 'css', 'sass']
        }

    在修改style标签
        <style lang="scss">