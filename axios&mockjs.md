mockjs
    安装：

        cnpm install mockjs --save

    建立目录结构： src/mock.js

    mock.js

        /* start */
        import Mock from 'mockjs' // 引入mockjs
        
        const Random = Mock.Random // Mock.Random 是一个工具类，用于生成各种随机数据
        
        let data = [] // 用于接受生成数据的数组
        let size = [
            '300x250', '250x250', '240x400', '336x280', 
            '180x150', '720x300', '468x60', '234x60', 
            '88x31', '120x90', '120x60', '120x240', 
            '125x125', '728x90', '160x600', '120x600', 
            '300x600'
        ] // 定义随机值
        for(let i = 0; i < 10; i ++) { // 可自定义生成的个数
            let template = {
                'Boolean': Random.boolean, // 可以生成基本数据类型
                'Natural': Random.natural(1, 10), // 生成1到100之间自然数
                'Integer': Random.integer(1, 100), // 生成1到100之间的整数
                'Float': Random.float(0, 100, 0, 5), // 生成0到100之间的浮点数,小数点后尾数为0到5位
                'Character': Random.character(), // 生成随机字符串,可加参数定义规则
                'String': Random.string(2, 10), // 生成2到10个字符之间的字符串
                'Range': Random.range(0, 10, 2), // 生成一个随机数组
                'Date': Random.date(), // 生成一个随机日期,可加参数定义日期格式
                'Image': Random.image(Random.size, '#02adea', 'Hello'), // Random.size表示将从size数据中任选一个数据
                'Color': Random.color(), // 生成一个颜色随机值
                'Paragraph':Random.paragraph(2, 5), //生成2至5个句子的文本
                'Name': Random.name(), // 生成姓名
                'Url': Random.url(), // 生成web地址
                'Address': Random.province() // 生成地址
            }
            data.push(template)
        }
        
        Mock.mock('/data/index', 'post', data) // 根据数据模板生成模拟数据
        /* end */

    main.js引入：

        require('./mock.js');

    解决跨域问题：
        config/index.js

            proxyTable: {
                '/api': {  
                    target: 'http://api.douban.com',//设置你调用的接口域名和端口号  			
                    changeOrigin: true, //跨域  			
                    pathRewrite: {  
                    '^/api': '/' 			
                    }  
                }
            },
            host: 'xjw.pconline.com.cn', // 使用自己host文件下配置的域名s



axios
    安装：

        cnpm install axios qs --save-dev

    新建目录结构 

        src/axios/http.js

    http.js

        /* start */
        import axios from 'axios'
        import qs from 'qs'
 
        axios.defaults.headers.post['Content-Type'] = 'application/x-www-form-urlencoded'
        
        // 请求拦截器
        axios.interceptors.request.use(function(config) {
            if (config.method === 'post') {
                config.data = qs.stringify(config.data)
            }
            return config;
        }, function(error) {
            return Promise.reject(error);
        })

        // 响应拦截器
        axios.interceptors.response.use(function(response) {
            return response;
        }, function(error) {
            return Promise.reject(error);
        })
        
        // 封装axios的get/post请求
        export default {
            post(url, params){
                return new Promise((resolve, reject) => {
                    axios.post(url, params)
                    .then(response => {
                        resolve(response.data);
                    })
                    .catch((error) => {
                        reject(error);
                    })
                })
            },
            get(url, params){
                return new Promise((resolve, reject) => {
                    axios.get(url, params)
                    .then(response => {
                        resolve(response.data);
                    })
                    .catch((error) => {
                        reject(error);
                    })
                }) 
            }
        }
        /* end */

    组件中使用：

        http.mockdata('/data/index')
		.then(res => {
			console.log(res);
		})
