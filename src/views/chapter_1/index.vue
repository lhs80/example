<template>
    <aside class="nav-wrapper">
        <ul class="nav-header">
            <li class="nav-header-item normal" :class="curTab===1?'active':''" @mouseover="curTab=1">
                <span class="title">商品分类</span>
                <ul class="menu">
                    <li class="menu-item"
                        :class="curPanel===key?'active':''"
                        v-for="(item,key) in navData"
                        :key="item.id"
                        @mouseenter="curPanel=key"
                        @mouseleave="curPanel=-1"
                    >
                        <div class="menu-item-name" :class="'menu-item-name-'+key">
                            <i class="iconfont" :class="item.icon"/>
                            <span>{{item.name}}</span>
                        </div>
                        <div class="menu-content" :class="'menu-content-'+key">
                            <div class="menu-content-line"
                                 v-for="(subItem,index) in item.child"
                                 :key="index"
                            >
                                <label class="name">
                                    <i class="text">{{subItem.name}}</i>
                                    <i class="iconfont icon-jiantou"/>
                                </label>
                                <div class="panel">
                                    <a href="#" :class="childItem.flag?'highlight':''"
                                       v-for="childItem in subItem.child">
                                        {{childItem.name}}
                                    </a>
                                </div>
                            </div>
                        </div>
                    </li>
                </ul>
            </li>
            <li class="nav-header-item meeting-tab" :class="curTab===2?'active':''" @mouseover="curTab=2">
                <span class="title">38大促</span>
                <ul class="menu">
                    <li><span>大牌服饰</span></li>
                    <li><span>大牌美妆</span></li>
                    <li><span>手机数码</span></li>
                    <li><span>女王新家</span></li>
                    <li><span>食品生鲜</span></li>
                    <li><span>天猫国际</span></li>
                    <li><span>苏宁爆款</span></li>
                    <li><span>虚拟充值</span></li>
                    <li><span>新车补贴</span></li>
                </ul>
            </li>
        </ul>
        <div class="nav-content">
            <span class="nav-content-item">
                <a href="https://vip.tmall.com/">天猫超市</a>
            </span>
            <span class="nav-content-item">
                <a href="https://vip.tmall.com/">天猫国际</a>
            </span>
            <span class="nav-content-item">
                <a href="https://vip.tmall.com/">天猫会员</a>
            </span>
            <span class="nav-content-item">
                <a href="https://vip.tmall.com/">电器城</a>
            </span>
            <span class="nav-content-item">
                <a href="https://vip.tmall.com/">喵鲜生</a>
            </span>
            <span class="nav-content-item">
                <a href="https://vip.tmall.com/">医药馆</a>
            </span>
            <span class="nav-content-item">
                <a href="https://vip.tmall.com/">魅力惠</a>
            </span>
            <span class="nav-content-item">
                <a href="https://vip.tmall.com/">飞猪旅行</a>
            </span>
            <span class="nav-content-item">
                <a href="https://vip.tmall.com/">苏宁易购</a>
            </span>
        </div>
    </aside>
</template>

<script>
  export default {
    data() {
      return {
        curTab: 2,
        navData: [],
        curPanel: -1
      }
    },
    mounted() {
      this.navData = require('./nav.json')
    }
  }
</script>

<style lang="less" scoped>
    .nav-wrapper {
        width: 1030px;
        margin: 0 auto;
        height: 36px;
        position: relative;

        .nav-header {
            position: absolute;
            left: 0;
            top: 0;
            padding: 0;
            margin: 0;
            width: 200px;
            height: 36px;

            .nav-header-item {
                display: inline-block;
                width: 100px;
                height: 36px;
                line-height: 36px;
                text-align: center;
                font-size: 14px;
                background: #c60a0a;
                cursor: pointer;

                .menu {
                    display: none;
                    position: absolute;
                    top: 100%;
                    left: 0;
                    width: 200px;
                    margin: 0;
                    padding: 0;
                    background: rgba(0, 0, 0, 1);
                }

                &.active {
                    .menu {
                        display: block;
                    }
                }

                &.normal {
                    color: white;

                    .menu-item {
                        list-style-type: none;
                        text-align: left;

                        .menu-item-name {
                            color: white;
                            padding: 0 0 0 10px;
                            height: 31px;
                            line-height: 31px;

                            .iconfont {
                                margin-right: 5px;
                                vertical-align: middle
                            }

                            &:hover {
                                background: white;
                                font-weight: bold;
                            }

                            &-0:hover, &-3:hover {
                                color: #e54077;
                            }

                            &-2:hover, &-4:hover {
                                color: #6347ed;
                            }

                            &-1:hover, &-5:hover, &-9:hover, &-11:hover {
                                color: #427def
                            }

                            &-6:hover {
                                color: #fa5c5c
                            }

                            &-7:hover, &-8:hover, &-12:hover {
                                color: #f7a831
                            }

                            &-10:hover, &-14:hover {
                                color: #dd2727
                            }

                            &-13:hover, &-15:hover {
                                color: #3bc7b0
                            }
                        }

                        .menu-content {
                            width: 583px;
                            height: 500px;
                            position: absolute;
                            left: 200px;
                            top: 0;
                            background: white;
                            padding: 19px 30px;
                            display: none;

                            .menu-content-line {
                                position: relative;
                                overflow: hidden;

                                .name {
                                    margin-right: 30px;
                                    float: left;
                                    width: 70px;
                                    height: 16px;
                                    line-height: 16px;
                                    color: black;

                                    .text {

                                        font-style: normal;
                                        font-weight: 700;
                                        text-align: justify;
                                        text-justify: distribute-all-lines;
                                        text-align-last: justify;
                                        -moz-text-align-last: justify;
                                        -webkit-text-align-last: justify;
                                    }

                                    .iconfont {
                                        font-size: 12px
                                    }
                                }

                                .panel {
                                    overflow: hidden;
                                    float: left;
                                    width: 480px;
                                    padding-bottom: 5px;

                                    a {
                                        font-style: normal;
                                        float: left;
                                        margin-right: 13px;
                                        color: #666;
                                        text-decoration: none;
                                        height: 25px !important;
                                        line-height: 1 !important;
                                    }
                                }

                                &:not(:last-child)::after {
                                    content: "";
                                    display: block;
                                    position: absolute;
                                    bottom: 0;
                                    left: 90px;
                                    width: 450px;
                                    height: 1px;
                                    border-bottom: dashed 1px #eee;
                                }

                                &:not(:first-child) {
                                    margin-top: 15px;
                                }
                            }

                            &-0, &-3 {
                                a:hover {
                                    color: #e54077 !important;
                                }

                                .highlight {
                                    color: #e54077 !important;
                                }
                            }

                            &-1, &-5, &-9, &-11 {
                                a:hover {
                                    color: #427def !important;
                                }

                                .highlight {
                                    color: #427def !important;
                                }
                            }

                            &-2, &-4 {
                                a:hover {
                                    color: #6347ed !important;
                                }

                                .highlight {
                                    color: #6347ed !important;
                                }
                            }

                            &-6 {
                                a:hover {
                                    color: #fa5c5c !important;
                                }

                                .highlight {
                                    color: #fa5c5c !important;
                                }
                            }

                            &-7, &-8, &-12 {
                                a:hover {
                                    color: #f7a831 !important;
                                }

                                .highlight {
                                    color: #f7a831 !important;
                                }
                            }

                            &-10, &-14 {
                                a:hover {
                                    color: #dd2727 !important;
                                }

                                .highlight {
                                    color: #dd2727 !important;
                                }
                            }

                            &-13, &-15 {
                                a:hover {
                                    color: #3bc7b0 !important;
                                }

                                .highlight {
                                    color: #3bc7b0 !important;
                                }
                            }
                        }

                        &.active {
                            .menu-content {
                                display: block;
                            }
                        }
                    }

                    &.active {
                        color: #c60a0a !important;
                        background: #eee;
                    }
                }

                &.meeting-tab {
                    color: #ffe013;

                    .menu {
                        padding: 29px 0 14px 0;

                        li {
                            padding: 0 24px;
                            margin-bottom: 15px;

                            span {
                                display: block;
                                width: 100%;
                                border: solid 1px #c60a0a;
                                border-radius: 10px;
                                text-align: center;

                                &:hover {
                                    background: #c60a0a;
                                }
                            }
                        }
                    }

                    &.active {
                        color: white;
                        background: #333;
                    }
                }
            }
        }

        .nav-content {
            display: inline-block;
            margin-left: 200px;
            border-bottom: solid 1px red;

            .nav-content-item {
                padding: 0 8px;
                height: 35px;
                line-height: 35px;
                font-size: 16px;

                a:link,
                a:active,
                a:visited {
                    color: #333;
                    text-decoration: none
                }

                a:hover {
                    color: #e54077;
                }
            }
        }
    }
</style>
