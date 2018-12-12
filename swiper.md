# swiper

    我是使用vscode来开发的，所以在安装vue-awesome-swiper的时候，总是会报模块找不到的错误，网上找了很久也没找到解决的方法，感觉应该是和自己的vscode的配置有关吧，最后还是直接安装swiper来做滑动效果了；
    以下是swiper的安装和使用:

    安装：
        cnpm install swiper --save-dev

    组件中script引入swiper:
        <script>
            import Swiper from 'swiper';
            export default {
                name: 'HelloWorld',
                data () {
                    return {
                        
                    }
                },
                mounted(){
                    new Swiper ('.swiper-container', {
                        loop: true,
                        // 如果需要分页器
                        pagination: {
                            el: '.swiper-pagination'
                        },
                        // 如果需要前进后退按钮
                        navigation: {
                            nextEl: '.swiper-button-next',
                            prevEl: '.swiper-button-prev',
                        },
                        // 如果需要滚动条
                        scrollbar: {
                            el: '.swiper-scrollbar',
                        }
                    })         
                }
            }
        </script>

    组件中swiper的HTML结构:

        <div class="swiper-container">
            <div class="swiper-wrapper">
                <div class="swiper-slide">Slide 1</div>
                <div class="swiper-slide">Slide 2</div>
                <div class="swiper-slide">Slide 3</div>
            </div>
            <!-- 如果需要分页器 -->
            <div class="swiper-pagination"></div>
            
            <!-- 如果需要导航按钮 -->
            <div class="swiper-button-prev"></div>
            <div class="swiper-button-next"></div>
            
            <!-- 如果需要滚动条 -->
            <div class="swiper-scrollbar"></div>
        </div>

    main.js里引入css:

        import Vue from 'vue'
        import 'swiper/dist/css/swiper.css'

    swiper的组件里写点样式:

        <style scoped>
            .swiper-container {
                width: 500px;
                height: 300px;
                margin: 20px auto;
            }
        </style>