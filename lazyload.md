## Vue-Lazyload
    安装：
        cnpm i vue-lazyload -S

    main.js
        import VueLazyload from 'vue-lazyload'
        Vue.use(VueLazyload, {
            preLoad: 1.3,
            error: require('./assets/error.jpg'),
            loading: require('./assets/loading.gif'),
            attempt: 1
        })

    组件中:
        <template>
            <div class="hello">
                <div v-for="(img,index) in src" :key="index">			
                    <img v-lazy="img" />
                </div>
            </div>
        </template>

        <script>
        export default {
            name: 'HelloWorld',
            data () {
                return {
                    src: [
                        "https://img3.doubanio.com/view/photo/s_ratio_poster/public/p2539661066.jpg",
                        "https://img1.doubanio.com/view/photo/s_ratio_poster/public/p2541280047.jpg",
                        "https://img3.doubanio.com/view/photo/s_ratio_poster/public/p253766730.jpg"
                    ]
                }
            }
        }
        </script>