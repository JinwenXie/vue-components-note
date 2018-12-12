1、豆瓣热映
    接口：https://api.douban.com/v2/movie/in_theaters

    参数：
        start : 数据的开始项
        count：单页条数
        city：城市

        如：获取“北京”热映电影“第二页”每页“25条”数据：
            https://api.douban.com/v2/movie/in_theaters?city=北京&start=25&count=25

 

2、电影top250
    接口：http://api.douban.com/v2/movie/top250

    参数：
        start : 数据的开始项
        count：单页条数
        如：获取电影Top250 第二页 25条数据：
            http://api.douban.com/v2/movie/top250?start=25&count=25

 

3、电影条目检索
    接口：http://api.douban.com/v2/movie/search
        
    访问参数：
        start : 数据的开始项
        count：单页条数
        q：要搜索的电影关键字
        tag：要搜索的电影的标签
        如：第二页每页25条
            搜索电影《战狼》：
            https://api.douban.com/v2/movie/search?q=战狼&start=25&count=25

            搜索喜剧类型的电影：
            https://api.douban.com/v2/movie/search?tag=喜剧&start=25&count=25

 
4、条目详情
    接口：http://api.douban.com/v2/movie/subject

    参数：
        电影id
        如：电影《神秘巨星》的电影id为：26942674，搜索此电影的详细信息
        http://api.douban.com/v2/movie/subject/26942674