<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <title>卡诗官网</title>
    <script type="text/javascript" src="http://code.jquery.com/jquery-1.10.2.min.js"></script>
    <style>
        * {
            margin: 0px;
            padding: 0px;
        }

        ul, li {
            list-style: none;
        }

        .wrap {
            margin: 0 auto;
        }

        .lf {
            float: left;
        }

        .rt {
            float: right;
        }

        .w266 {
            width: 266px;
        }

        .w320 {
            width: 320px;
        }

        .clear {
            clear: both;
        }

        .topMenu {
            background: url("images/wap_topBg.jpg") repeat-x;
            width: 320px;
            background-size: 100%;
            display: inline-block;
        }

        .topMenu a {
            height: 24px;
            display: inline-block;
            font-size: 12px;
            color: #cccccc;
            text-decoration: none;
            line-height: 24px;
            width: 90px;
        }

        .mapLeft {
            position: relative;
            background: url("images/map_left.jpg");
            width: 320px;
            height: 260px;
            background-size: 100%;
            margin: 0px auto;
        }

        .citySelect {
            position: absolute;
            top: 34px;
            left: 117px;
        }

        .citySelect #Province, #City, #Area {
            float: left;
            margin-top: 14px;
            height: 24px;
            position: relative;
        }

        .writeBox span {
            float: left;
            width: 137px;
            height: 24px;
            line-height: 24px;
            font-size: 12px;
            padding: 0 5px;
            display: inline-block;
        }

        .writeBox a {
            float: left;
            display: inline-block;
            width: 24px;
            height: 25px;
            margin-left: 5px;
        }

        .btnStyle {
            position: absolute;
            top: 207px;
            left: 81px;
            height: 26px;
            padding: 0px 30px 15px;
            line-height: 26px;
            margin: 0px auto;
        }
        .listStyle{
            position: absolute;
            top: 24px;
            left: -6px;
            width: 183px;
            max-height: 150px;
            overflow: auto;
            overflow-x: hidden;
            border: 1px solid #909090;
            z-index: 55;
            background: #ffffff;
        }
        .listStyle li {
            height: 22px;
            line-height: 22px;
            padding: 0 5px;
            width: 163px;
            color: #7b7b7b;
            font-size: 12px;
        }
        .listStyle li:hover{
            background-color: #cccccc;
        }
        #storeList li {
            width: 300px;
            padding: 10px 10px 10px 15px;
            border-bottom: 1px solid #b2b2b2;
        }
    </style>
</head>
<body>
<div class="warp w320" style="position: relative;margin: 0px auto">
    <div class="topMenu">
        <a href="http://www.kerastase.com.cn/" class="rt">返回首页</a>
    </div>

    <div class="clear" style=" height:10px;"></div>
    <div class="mapLeft">
        <div class="citySelect">
            <div id="Province">
                <p class="writeBox">
                    <span>请选择</span>
                    <a></a>
                <ul class="listStyle" style="display: none"></ul>
                </p>
            </div>
            <div id="City">
                <p class="writeBox">
                    <span></span>
                    <a></a>
                <ul class="listStyle" style="display: none"></ul>
                </p>
            </div>
            <div id="Area">
                <p class="writeBox">
                    <span></span>
                    <a></a>
                <ul class="listStyle" style="display: none"></ul>
                </p>
            </div>
        </div>
    </div>
    <a class="btnStyle" id="soStore">
        <img src="images/searchBtn.jpg" alt="" width="82" height="25"/>
    </a>
    <div>
        <h1>
            <img src="images/result_title.jpg" alt="" width="320" height="66"/>
        </h1>
        <div id="storeList">
            <ul>

            </ul>
        </div>
    </div>
</div>
<script>
    var $Province;
    var $City;
    var $Area;
    var p = null;
    var c = null;
    var CITY_DATA  = [{
        "Value": "北京",
        "Children": [{"Value": "北京", "Children": [{"Value": "昌平区", "Children": []}, {"Value": "朝阳", "Children": []}, {"Value": "朝阳区", "Children": []
            }, {"Value": "崇文区", "Children": []}, {"Value": "东城区", "Children": []}, {"Value": "丰台", "Children": []
            }, {"Value": "丰台区", "Children": []}, {"Value": "海淀区", "Children": []}, {"Value": "市南区", "Children": []
            }, {"Value": "顺义区", "Children": []}, {"Value": "通州", "Children": []},   {"Value": "西城", "Children": []}, {"Value": "西城区", "Children": []}, {"Value": "宣武区", "Children": []}, {"Value": "亦庄开发区", "Children": []}]
        }]
        }, {"Value": "上海",
        "Children": [{"Value": "上海",
            "Children": [{"Value": "宝山区", "Children": []}, {"Value": "长宁区", "Children": []}, {"Value": "虹口区", "Children": []
            }, {"Value": "黄浦区", "Children": []}, {"Value": "静安区", "Children": []}, {"Value": "卢湾区", "Children": []
            }, {"Value": "闵行区", "Children": []}, {"Value": "浦东新区", "Children": []}, {"Value": "普陀区", "Children": []
            }, {"Value": "徐汇区", "Children": []}, {"Value": "杨浦区", "Children": []}, {"Value": "闸北区", "Children": []}]
        }]
         }, {"Value": "广东",
        "Children": [{"Value": "东莞", "Children": [{"Value": "全部", "Children": []}]}, {"Value": "佛山", "Children": [{"Value": "禅城区", "Children": []}, {"Value": "全部", "Children": []}]
        }, {"Value": "广州", "Children": [{"Value": "白云区", "Children": []}, {"Value": "东山区", "Children": []}, {"Value": "番禺区", "Children": []
            }, {"Value": "番禹区", "Children": []}, {"Value": "海珠区", "Children": []}, {"Value": "花都区", "Children": []
            }, {"Value": "天河区", "Children": []}, {"Value": "越秀", "Children": []}, {"Value": "越秀区", "Children": []
            }, {"Value": "增城区", "Children": []}]
        }, {"Value": "惠州", "Children": [{"Value": "全部", "Children": []}]}, {"Value": "江门", "Children": [{"Value": "全部", "Children": []}]
        }, {"Value": "深圳", "Children": [{"Value": "东城区", "Children": []}, {"Value": "福田", "Children": []}, {"Value": "福田区", "Children": []
        }, {"Value": "龙岗区", "Children": []}, {"Value": "罗湖区", "Children": []}, {"Value": "南山区", "Children": []
        }, {"Value": "中心区", "Children": []}]
        }, {"Value": "珠海", "Children": []}]
         }, {"Value": "安徽",
        "Children": [{"Value": "合肥", "Children": [{"Value": "全部", "Children": []}]}]},
        {"Value": "福建",
        "Children": [{"Value": "福清", "Children": [{"Value": "全部", "Children": []}]}, {"Value": "福州", "Children": [{"Value": "鼓楼区", "Children": []}, {"Value": "全部", "Children": []}]
        }, {"Value": "泉州", "Children": [{"Value": "全部", "Children": []}]}, {"Value": "石狮", "Children": [{"Value": "全部", "Children": []}]
        }, {"Value": "厦门", "Children": [{"Value": "全部", "Children": []}]}]
        },
        {"Value": "甘肃",
            "Children": [{"Value": "兰州", "Children": [{"Value": "全部", "Children": []}]}]},
        {"Value": "广西",
        "Children": [{"Value": "柳州", "Children": [{"Value": "全部", "Children": []}]}, {"Value": "南宁", "Children": [{"Value": "青秀区", "Children": []}, {"Value": "全部", "Children": []}]
        }]
         }, {"Value": "贵州",
        "Children": [{"Value": "贵阳", "Children": [{"Value": "南明区", "Children": []}, {"Value": "全部", "Children": []}]
        }, {"Value": "遵义", "Children": [{"Value": "全部", "Children": []}]}]
         },
        {"Value": "河北",
        "Children": [{"Value": "保定", "Children": [{"Value": "全部", "Children": []}]}, {"Value": "邯郸", "Children": [{"Value": "全部", "Children": []}]
        }, {"Value": "石家庄", "Children": []}, {"Value": "唐山", "Children": [{"Value": "全部", "Children": []}]}]
            },
        {"Value": "河南",
        "Children": [{"Value": "郑州", "Children": [{"Value": "金水", "Children": []}, {"Value": "全部", "Children": []}]}]
         },
        {"Value": "黑龙江",
        "Children": [{"Value": "哈尔滨", "Children": [{"Value": "道里区", "Children": []}, {"Value": "南岗", "Children": []}, {"Value": "南岗区", "Children": []
        }, {"Value": "全部", "Children": []}]
        }]
        },
        {"Value": "湖北",
        "Children": [{"Value": "武汉", "Children": [{"Value": "江岸区", "Children": []}, {"Value": "江汉区", "Children": []}, {"Value": "青山区", "Children": []
            }, {"Value": "全部", "Children": []}, {"Value": "伍家区", "Children": []}, {"Value": "西陵区", "Children": []}]
        }]
        },
        {"Value": "湖南",
        "Children": [{"Value": "长沙", "Children": [{"Value": "全部", "Children": []}]}, {"Value": "娄底", "Children": [{"Value": "全部", "Children": []}]
        }, {"Value": "湘潭", "Children": [{"Value": "全部", "Children": []}]}, {
            "Value": "株洲",
            "Children": [{"Value": "全部", "Children": []}]
        }]
        },
        {"Value": "吉林",
        "Children": [{"Value": "长春", "Children": [{"Value": "朝阳区", "Children": []}, {"Value": "全部", "Children": []}]}]
        },
        {"Value": "江苏",
        "Children": [{"Value": "常熟", "Children": [{"Value": "全部", "Children": []}]}, {"Value": "常州", "Children": [{"Value": "全部", "Children": []}]
        }, {"Value": "合肥", "Children": [{"Value": "全部", "Children": []}]}, {"Value": "江阴", "Children": [{"Value": "全部", "Children": []}]
        }, {"Value": "连云港", "Children": []}, {"Value": "南京", "Children": [{"Value": "白下区", "Children": []}, {"Value": "鼓楼区", "Children": []}, {"Value": "建邺区", "Children": []
            }, {"Value": "栖霞区", "Children": []}, {"Value": "秦淮区", "Children": []}, {"Value": "玄武区", "Children": []}]
        }, {"Value": "南通", "Children": [{"Value": "崇川区", "Children": []}]}, {"Value": "苏州", "Children": [{"Value": "全部", "Children": []}]
        }, {"Value": "泰州", "Children": [{"Value": "海陵区", "Children": []}]}, {"Value": "无锡", "Children": [{"Value": "全部", "Children": []}]
        }, {"Value": "吴江", "Children": [{"Value": "全部", "Children": []}]}, {"Value": "徐州", "Children": [{"Value": "全部", "Children": []}]
        }, {"Value": "盐城", "Children": []}, {"Value": "扬州", "Children": [{"Value": "全部", "Children": []}]
        }, {"Value": "宜兴", "Children": []}, {"Value": "镇江", "Children": [{"Value": "全部", "Children": []}]}]
            },
        {"Value": "江西",
        "Children": [{"Value": "九江", "Children": []}, {"Value": "南昌", "Children": [{"Value": "红谷滩区", "Children": []}, {"Value": "全部", "Children": []}]
        }, {"Value": "上饶", "Children": [{"Value": "全部", "Children": []}]}]
            },
        {"Value": "辽宁",
        "Children": [{"Value": "鞍山", "Children": [{"Value": "全部", "Children": []}]}, {"Value": "大连", "Children": [{"Value": "全部", "Children": []}, {"Value": "中山", "Children": []}, {"Value": "中山区", "Children": []
            }]
        }, {"Value": "锦州", "Children": [{"Value": "全部", "Children": []}]}, {"Value": "沈阳", "Children": [{"Value": "和平", "Children": []}, {"Value": "全部", "Children": []}]
        }]
            },
        {"Value": "内蒙古",
        "Children": [{"Value": "鄂尔多斯", "Children": [{"Value": "全部", "Children": []}]}, {"Value": "呼和浩特", "Children": []
        }]
            },
        {"Value": "山东",
        "Children": [{"Value": "东营", "Children": [{"Value": "全部", "Children": []}]}, {"Value": "济南", "Children": [{"Value": "全部", "Children": []}]
        }, {"Value": "青岛", "Children": [{"Value": "全部", "Children": []}, {"Value": "市南区", "Children": []}]
        }, {"Value": "威海", "Children": [{"Value": "环翠", "Children": []}, {"Value": "全部", "Children": []}]
        }, {"Value": "潍坊", "Children": [{"Value": "全部", "Children": []}]}, {"Value": "烟台", "Children": [{"Value": "全部", "Children": []}]
        }, {"Value": "淄博", "Children": []}]
            },
        {"Value": "山西",
        "Children": [{"Value": "太原", "Children": [{"Value": "全部", "Children": []}]}, {"Value": "运城", "Children": [{"Value": "盐湖区", "Children": []}]
        }]
            },
        {"Value": "陕西",
        "Children": [{"Value": "西安", "Children": [{"Value": "莲湖区", "Children": []}, {"Value": "全部", "Children": []}]}]
            },
        {"Value": "四川",
        "Children": [{"Value": "成都", "Children": [{"Value": "成华区", "Children": []}, {"Value": "都江堰", "Children": []}, {"Value": "高新区", "Children": []}, {"Value": "锦江区", "Children": []}, {"Value": "青羊区", "Children": []}, {"Value": "武侯区", "Children": []
            }, {"Value": "新都区", "Children": []}]
        }, {"Value": "乐山", "Children": [{"Value": "全部", "Children": []}]}, {"Value": "泸州", "Children": [{"Value": "江阳区", "Children": []}, {"Value": "全部", "Children": []}]
        }, {"Value": "眉山", "Children": [{"Value": "全部", "Children": []}]}, {"Value": "南充", "Children": [{"Value": "全部", "Children": []}]
        }, {"Value": "攀枝花", "Children": [{"Value": "全部", "Children": []}]}, {"Value": "宜宾", "Children": [{"Value": "翠屏区", "Children": []}]
        }]
        },
        {"Value": "天津",
            "Children": [{"Value": "天津", "Children": [{"Value": "全部", "Children": []}]}]},
        {"Value": "西藏",
        "Children": [{"Value": "拉萨", "Children": [{"Value": "全部", "Children": []}]}]
        },
        {"Value": "新疆",
        "Children": [{"Value": "阿克苏", "Children": [{"Value": "全部", "Children": []}]}, {"Value": "昌吉市", "Children": [{"Value": "全部", "Children": []}]
        }, {"Value": "乌鲁木齐", "Children": [{"Value": "全部", "Children": []}]}]
        },
        {"Value": "云南 ",
        "Children": [{"Value": "昆明", "Children": [{"Value": "盘龙区", "Children": []}, {"Value": "全部", "Children": []}, {"Value": "五华区", "Children": []
            }, {"Value": "西山区", "Children": []}]
        }]
        },
        {"Value": "浙江",
        "Children": [{"Value": "慈溪", "Children": [{"Value": "全部", "Children": []}]}, {"Value": "东阳", "Children": []
        }, {"Value": "海宁", "Children": [{"Value": "全部", "Children": []}]}, {"Value": "杭州", "Children": [{"Value": "拱墅区", "Children": []}, {"Value": "江干区", "Children": []}, {"Value": "上城区", "Children": []
            }, {"Value": "西湖区", "Children": []}, {"Value": "下城区", "Children": []}]
        }, {"Value": "嘉兴", "Children": [{"Value": "海宁", "Children": []}, {"Value": "全部", "Children": []}]
        }, {"Value": "椒江", "Children": [{"Value": "全部", "Children": []}]}, {"Value": "金华", "Children": [{"Value": "全部", "Children": []}]
        }, {"Value": "乐清", "Children": [{"Value": "全部", "Children": []}]}, {"Value": "临海", "Children": [{"Value": "全部", "Children": []}]
        }, {"Value": "宁波", "Children": [{"Value": "奉化市", "Children": []}, {"Value": "海曙区", "Children": []}, {
                "Value": "全部",
                "Children": []
            }, {"Value": "镇海", "Children": []}]
        }, {"Value": "瑞安", "Children": [{"Value": "全部", "Children": []}]}, {
            "Value": "绍兴",
            "Children": [{"Value": "全部", "Children": []}]
        }, {"Value": "绍兴市", "Children": [{"Value": "柯桥区", "Children": []}]}, {
            "Value": "台州",
            "Children": [{"Value": "椒江区", "Children": []}, {"Value": "全部", "Children": []}]
        }, {"Value": "温岭", "Children": [{"Value": "全部", "Children": []}]}, {
            "Value": "温州",
            "Children": [{"Value": "全部", "Children": []}]
        }, {"Value": "义乌", "Children": [{"Value": "全部", "Children": []}]}, {
            "Value": "余姚",
            "Children": [{"Value": "全部", "Children": []}]
        }, {"Value": "诸暨", "Children": [{"Value": "全部", "Children": []}]}]
        },
        {"Value": "重庆",
            "Children": [{"Value": "重庆", "Children": [{"Value": "全部","Children":[]}]}]}]


       $(function () {
           $Province = $("#Province");
           $City = $("#City");
           $Area = $("#Area");
           loadProvince();
       })
                    //加载省份
         function loadProvince() {
             var p_length = CITY_DATA.length;
             var p_list = '';
             for (var i = 0; i < p_length; i++) {
                 p_list+="<li>"+CITY_DATA[i].Value+"</li>";
             }
             $(".listStyle",$Province).append(p_list);
             selectValue($Province);
         }
        function selectValue(obj){
            $("a",obj).unbind().click(function(){
                $(".listStyle",obj).toggle();
            });
            $(".listStyle li",obj).unbind().click(function(){
                var spanvalue=$(this).text()
                $("span",obj).text(spanvalue);
                $(".listStyle",obj).hide();
                if(obj==$Province){
                    p=$(this).index();
                    c=null;
                    $("span",$City).text("请选择");
                    $("span",$Area).text("请选择");
                    $(".listStyle",$City).empty();
                    $(".listStyle",$Area).empty();
                    loadChildData(p);
                    selectValue($City);
                }
                if(obj==$City){
                    c=$(this).index();
                    loadChildData(p,c);
                    selectValue($Area)
                }
            });
            function loadChildData(m,n){
                var obj=null;
                var p_length=0;
                var p_list="";
                var children_obj=null;
                var parent_obj=null;
               if(m!=null && n!=null) {
                   obj=$Area;
                   parent_obj=CITY_DATA[m].Children[n];
                   children_obj=CITY_DATA[m].Children[n].Children;
                   p_length=children_obj.length;

               }else if(m!=null){
                   obj=$City;
                   parent_obj=CITY_DATA[m];
                   children_obj=CITY_DATA[m].Children;
                   p_length=children_obj.length;

               }else{return;}
                for(var i=0;i<p_length;i++){
                    p_list+="<li>"+children_obj[i].Value+"</li>"
                }
                $(".listStyle",obj).append(p_list);
            };
            $("#soStore").click(function(){
                var province=$("span",$Province).text();
                var city=$("span",$City).text();
                var area=$("span",$Area).text();
                if(city=="请选择"||city==""){
                    alert("请选择你要搜索的城市");
                    return false;
                }
                searchSalon();
            });
            //搜索沙龙
            function searchSalon(){
                var	province = $("span",$Province).text();
                var	city = $("span",$City).text();
                var	area = $("span",$Area).text();
                DoAjax({
                    url: '/common/GetMapAddress.ashx',
                    data: {
                        province: province,
                        city: city,
                        area: area
                    },
                    success: function (msg) {
                        document.location.href = "searchResult.html?province=" + province + "&city=" + city + "&area=" + area;
                    }
                });
            }


        }


</script>
<script>
    var addr=[
        {"SalonName":"iWo Fashion Style","SalonTel":"021-63321973","SalonAddress":"长宁区黃金城道528号"},
        {"SalonName":"明英(古北)","SalonTel":"021-62952108","SalonAddress":"长宁区荣华东道128号102A室"},
        {"SalonName":"明英(黄金城道)","SalonTel":"021-32095216","SalonAddress":"上海市长宁区黄金城道660号"},
        {"SalonName":"意莎(黄金城店)","SalonTel":"021-32303011","SalonAddress":"上海市长宁区黄金城道568号"},
        {"SalonName":"意莎古北","SalonTel":"021-62700813","SalonAddress":"古北新区荣华东道128号101"},
        {"SalonName":"尚舞台","SalonTel":"021-62120992","SalonAddress":"上海市长宁区定西路1316号"},
        {"SalonName":"金匠","SalonTel":"52420063","SalonAddress":"上海市长宁区娄山关路1016号"},
        {"SalonName":"发意美发","SalonTel":"021-33729337","SalonAddress":"上海市长宁区水城南路55号6月汇广场401A"},
        {"SalonName":"上海型秀造型","SalonTel":"021-33530082","SalonAddress":"上海市长宁区紫云西路20号（近遵义路）"},
        {"SalonName":"上海时尚传奇","SalonTel":"021-62210388","SalonAddress":"上海市长宁区黄金城道781号"},
        {"SalonName":"Airplus高岛屋","SalonTel":"52830287","SalonAddress":"上海市长宁区虹桥路1438号古北国际财富中心2期6楼01（近红宝石路）"},
        {"SalonName":"BV造型","SalonTel":"52081238","SalonAddress":"上海市长宁区仙霞路86号万都商城2F"},
        {"SalonName":"上海舒豪造型","SalonTel":"021-62839529","SalonAddress":"上海市长宁区定西路465号"},
        {"SalonName":"古北巴黎   ","SalonTel":"021-62702270","SalonAddress":"古北新区水城南路17号万科广场底层 "},
        {"SalonName":"时尚造型","SalonTel":"021-62823651","SalonAddress":"上海市长宁区法华镇路65号"},
        {"SalonName":"曼都仙霞店","SalonTel":"52832080","SalonAddress":"上海市长宁区仙霞西路88号西郊百联商场B111室（近剑河路）"},
        {"SalonName":"曼都缤谷店","SalonTel":"?021-62280267","SalonAddress":"上海市长宁区天山路341号缤谷广场214号商铺（近威宁路）"},
        {"SalonName":"阿玛尼护肤造型威宁店","SalonTel":"尚未提供","SalonAddress":"上海市长宁区威宁路280号"},
        {"SalonName":"阿玛尼护肤造型古北店","SalonTel":"尚未提供","SalonAddress":"上海市长宁区古北路497号"},
        {"SalonName":"上海梳香","SalonTel":"尚未提供","SalonAddress":"上海市长宁区武夷路207弄9号"},
        {"SalonName":"阿玛尼星空广场店","SalonTel":"13041683964","SalonAddress":"上海市虹桥路1665号星空广场B315"},
        {"SalonName":"上海杰作美发","SalonTel":"021-64499358","SalonAddress":"上海市长宁区红松路127号"}]
    var salonadd=$("ul","#storeList");
    var addrList=""
    for(var i=0;i<addr.length;i++){
        addrList+="<li><p><b>"+addr[i].SalonName+"</b><br>电话："+addr[i].SalonTel+"<br>地址："+addr[i].SalonAddress+"</p></li>"
    }
    salonadd.append(addrList);
</script>

</body>
</html>
