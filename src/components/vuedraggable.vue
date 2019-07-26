<template>
    <div style="display: flex;min-width: 1490px;">
        <draggable v-model="items" v-bind="options1" tag="el-menu" class="container"
                   :component-data="getComponentData()">
            <!--            <transition-group type="transition" name="flip-list" tag="div">-->
            <template v-for="item in items">
                <el-submenu v-if="item.list.length>0" :index="item.index" :key="item.index">
                    <template slot="title">
                        <i :class="item.icon"></i>
                        <span>{{item.table}}</span>
                    </template>
                    <el-menu-item v-for="list in item.list" :index="list.index" :key="list.index">{{list.table}}
                    </el-menu-item>
                </el-submenu>
                <el-menu-item v-else :key="item.index" :index="item.index">
                    <i :class="item.icon"></i>
                    <span>{{item.table}}</span>
                </el-menu-item>
            </template>
            <!--            </transition-group>-->
        </draggable>

        <draggable v-model="data" v-bind="options3" @update="update" @remove="onRemove" @add="onAdd">
            <transition-group type="transition" name="flip-list" tag="ul" class="container">
                <li v-for="item in data" :key="item.index" class="li-list">
                    {{item.table}}
                </li>
            </transition-group>
        </draggable>

        <draggable v-model="lists" v-bind="options2">
            <transition-group type="transition" name="flip-list" tag="el-menu" class="container">
                <template v-for="item in lists">
                    <el-submenu v-if="item.list.length>0" :index="item.index" :key="item.index">
                        <template slot="title">
                            <i :class="item.icon"></i>
                            <span>{{item.table}}</span>
                        </template>
                        <el-menu-item v-for="list in item.list" :index="list.index" :key="list.index">{{list.table}}
                        </el-menu-item>
                    </el-submenu>
                    <el-menu-item v-else :key="item.index" :index="item.index">
                        <i :class="item.icon"></i>
                        <span>{{item.table}}</span>
                    </el-menu-item>
                </template>
            </transition-group>
        </draggable>

        <el-menu default-active="2" background-color="#545c64" text-color="#fff" active-text-color="#ffd04b"
                 class="container">
            <template v-for="item in lists">
                <el-submenu v-if="item.list.length>0" :index="item.index" :key="item.index">
                    <template slot="title">
                        <i :class="item.icon"></i>
                        <span>{{item.table}}</span>
                    </template>
                    <el-menu-item v-for="list in item.list" :index="list.index" :key="list.index">{{list.table}}
                    </el-menu-item>
                </el-submenu>
                <el-menu-item v-else :key="item.index" :index="item.index">
                    <i :class="item.icon"></i>
                    <span>{{item.table}}</span>
                </el-menu-item>
            </template>
        </el-menu>

        <draggable v-model="lists" v-bind="options4" style="width:650px;height: 100vh;overflow-y: auto;">
            <transition-group type="transition" name="flip-list">
                <el-card class="box-card" v-for="list in lists" :key="list.index">
                    <div slot="header">
                        <span>{{list.table}}</span>
                        <el-button style="float: right; padding: 3px 0" type="text">操作按钮</el-button>
                    </div>
                    <div v-for="o in 3" :key="o" class="text item">
                        {{'列表内容 ' + o }}
                    </div>
                </el-card>
            </transition-group>
        </draggable>
    </div>
</template>

<script>
    import draggable from 'vuedraggable'

    export default {
        components: {
            draggable
        },
        data: function () {
            return {
                items: [{
                    index: "1",
                    table: "导航一",
                    icon: "el-icon-location",
                    list: [{index: "1-1", table: "选项1"}, {index: "1-2", table: "选项2"}, {
                        index: "1-3",
                        table: "选项3"
                    }, {index: "1-4", table: "选项4"}]
                }, {
                    index: "2",
                    table: "导航二",
                    icon: "el-icon-menu",
                    list: [{index: "2-1", table: "选项1"}, {index: "2-2", table: "选项2"}, {
                        index: "2-3",
                        table: "选项3"
                    }, {index: "2-4", table: "选项4"}]
                },
                    {index: "3", table: "导航三", icon: "el-icon-setting", list: []},
                    {
                        index: "4",
                        table: "导航四",
                        icon: "el-icon-menu",
                        list: [{index: "4-1", table: "选项1"}, {index: "4-2", table: "选项2"}]
                    }, {
                        index: "5",
                        table: "导航五",
                        icon: "el-icon-menu",
                        list: [{index: "5-1", table: "选项1"}, {index: "5-2", table: "选项2"}, {
                            index: "5-3",
                            table: "选项3"
                        }, {index: "5-4", table: "选项4"}]
                    }, {
                        index: "6",
                        table: "导航五",
                        icon: "el-icon-menu",
                        list: [{index: "5-1", table: "选项1"}, {index: "5-2", table: "选项2"}, {
                            index: "5-3",
                            table: "选项3"
                        }, {index: "5-4", table: "选项4"}]
                    }, {
                        index: "7",
                        table: "导航五",
                        icon: "el-icon-menu",
                        list: [{index: "5-1", table: "选项1"}, {index: "5-2", table: "选项2"}, {
                            index: "5-3",
                            table: "选项3"
                        }, {index: "5-4", table: "选项4"}]
                    }, {
                        index: "8",
                        table: "导航五",
                        icon: "el-icon-menu",
                        list: [{index: "5-1", table: "选项1"}, {index: "5-2", table: "选项2"}, {
                            index: "5-3",
                            table: "选项3"
                        }, {index: "5-4", table: "选项4"}]
                    }, {
                        index: "9",
                        table: "导航五",
                        icon: "el-icon-menu",
                        list: [{index: "5-1", table: "选项1"}, {index: "5-2", table: "选项2"}, {
                            index: "5-3",
                            table: "选项3"
                        }, {index: "5-4", table: "选项4"}]
                    }, {
                        index: "18",
                        table: "导航五",
                        icon: "el-icon-menu",
                        list: [{index: "5-1", table: "选项1"}, {index: "5-2", table: "选项2"}, {
                            index: "5-3",
                            table: "选项3"
                        }, {index: "5-4", table: "选项4"}]
                    }, {
                        index: "19",
                        table: "导航五",
                        icon: "el-icon-menu",
                        list: [{index: "5-1", table: "选项1"}, {index: "5-2", table: "选项2"}, {
                            index: "5-3",
                            table: "选项3"
                        }, {index: "5-4", table: "选项4"}]
                    }, {
                        index: "20",
                        table: "导航五",
                        icon: "el-icon-menu",
                        list: [{index: "5-1", table: "选项1"}, {index: "5-2", table: "选项2"}, {
                            index: "5-3",
                            table: "选项3"
                        }, {index: "5-4", table: "选项4"}]
                    }, {
                        index: "10",
                        table: "导航五",
                        icon: "el-icon-menu",
                        list: [{index: "5-1", table: "选项1"}, {index: "5-2", table: "选项2"}, {
                            index: "5-3",
                            table: "选项3"
                        }, {index: "5-4", table: "选项4"}]
                    }, {
                        index: "11",
                        table: "导航一",
                        icon: "el-icon-location",
                        list: [{index: "1-1", table: "选项1"}, {index: "1-2", table: "选项2"}, {
                            index: "1-3",
                            table: "选项3"
                        }, {index: "1-4", table: "选项4"}]
                    }
                ],
                lists: [
                    {
                        index: "17",
                        table: "导航五",
                        icon: "el-icon-menu",
                        list: [{index: "5-1", table: "选项1"}, {index: "5-2", table: "选项2"}, {
                            index: "5-3",
                            table: "选项3"
                        }, {index: "5-4", table: "选项4"}]
                    },
                    {
                        index: "12",
                        table: "导航二",
                        icon: "el-icon-menu",
                        list: [{index: "2-1", table: "选项1"}, {index: "2-2", table: "选项2"}, {
                            index: "2-3",
                            table: "选项3"
                        }, {index: "2-4", table: "选项4"}]
                    },
                    {index: "13", table: "导航三", icon: "el-icon-setting", list: []},
                    {
                        index: "14",
                        table: "导航四",
                        icon: "el-icon-menu",
                        list: [{index: "4-1", table: "选项1"}, {index: "4-2", table: "选项2"}]
                    }
                ],
                data: [{
                    index: "15",
                    table: "导航五",
                    icon: "el-icon-menu",
                    list: [{index: "5-1", table: "选项1"}, {index: "5-2", table: "选项2"}, {
                        index: "5-3",
                        table: "选项3"
                    }, {index: "5-4", table: "选项4"}]
                }, {
                    index: "16",
                    table: "导航五",
                    icon: "el-icon-menu",
                    list: [{index: "5-1", table: "选项1"}, {index: "5-2", table: "选项2"}, {
                        index: "5-3",
                        table: "选项3"
                    }, {index: "5-4", table: "选项4"}]
                }],
                options1: {
                    animation: 100,//拖动过程中的延时动画
                    forceFallback: true,//是否显示原生的html5的拖放
                    ghostClass: "ghost-class",//拖动项的类名
                    group: "description"//分组用的，同一组的不同列表可以相互拖动
                },
                options2: {
                    forceFallback: false,//是否显示原生的html5的拖放
                    dragClass: "drag-class",//被拖动副本的类名
                    group: "description"
                },
                options3: {
                    animation: 100,//拖动过程中的延时动画
                    forceFallback: true,//是否显示原生的html5的拖放
                    ghostClass: "ghost-class",//拖动项的类名
                    dragClass: "drag-class",//被拖动副本的类名,只有forceFallback为true时才有效
                    group: "description"
                },
                options4: {
                    animation: 300,//拖动过程中的延时动画
                    forceFallback: false,//是否显示原生的html5的拖放
                    ghostClass: "ghost-class",//拖动项的类名
                    scroll:true,//当排序的容器是个可滚动的区域，拖放可以引起区域滚动
                    scrollSensitivity:50,//就是鼠标靠近边缘多远开始滚动默认30
                    scrollSpeed:500//滚动速度，单位应该是:像素/秒
                }
            }
        },
        methods: {
            update: function (evt) {
                console.log(evt);
                console.log(this.data);
                console.log("我的列表的排序改变了");
            },
            onRemove: function (evt) {
                console.log(evt);
                console.log(this.data);
                console.log("我的列表的单元被移动到另一个列表");
            },
            onAdd: function (evt) {
                console.log(evt);
                console.log(this.data);
                console.log("我的列表被添加单元时的回调函数");
            },
            /*
            * evt对象的常用属性
            * to: 移动到的列表的容器
            * from：来源列表容器
            * item: 被移动的单元
            * clone: 副本的单元
            * oldIndex：移动前的序号
            * newIndex：移动后的序号
            * */
            getComponentData: function () {
                return {
                    on: {
                        //绑定事件
                    },
                    props: {
                        //绑定参数
                        defaultActive: "2",
                        backgroundColor: "#545c64",
                        textColor: "#fff",
                        activeTextColor: "#ffd04b"
                    }
                }
            }
        },
        computed: {}
    }
</script>

<style scoped>
    ul {
        margin: 0;
        padding: 0;
    }

    .ghost-class {
        opacity: 0;
    }

    .drag-class {
        background-color: #545c64;
        color: #fff;
    }

    .flip-list-move {
        transition: transform 0.5s;
    }

    .container {
        width: 210px;
        text-align: left;
        height: 100vh;
        overflow-y: auto;
        overflow-x: hidden;
    }

    .li-list {
        height: 54px;
        line-height: 54px;
        cursor: move;
        list-style: none;
        padding: 0 20px;
        border: solid 1px #e6e6e6;
    }

    .box-card {
        width: 300px;
        height: 200px;
        float: left;
        cursor: move;
        margin:0 10px 10px 0;
    }
</style>
