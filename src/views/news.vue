<template>
    <div class="pos">
        <div>
            <el-row>
                <el-col :span='7' id="list">
                    <el-tabs>
                        <el-tab-pane label='点餐'>
                            <el-table :data='tableData' border show-summary style="width:100%">
                                <el-table-column label='商品' prop='names'></el-table-column>
                                <el-table-column label='量' prop='count'></el-table-column>
                                <el-table-column label='金额' prop='pri'></el-table-column>
                                <el-table-column label='操作'>
                                     <template slot-scope="scope">
								        <el-button
								          size="mini"
								          @click="handleEdit(scope.$index, scope.row)">编辑</el-button>
								        <el-button
								          size="mini"
								          type="danger"
								          @click="handleDelete(scope.$index, scope.row)">删除</el-button>
								      </template>
                                </el-table-column>
                            </el-table>
                        </el-tab-pane>
                        <el-tab-pane label='外卖'>
                            <el-table :data='tableData1' border show-summary style="width:100%">
                                <el-table-column label='商品' prop='names'></el-table-column>
                                <el-table-column label='量' prop='count'></el-table-column>
                                <el-table-column label='金额' prop='pri'></el-table-column>
                                <el-table-column label='操作'>
                                    <template slot-scope="scope">
								        <el-button
								          size="mini"
								          @click="handleEdit(scope.$index, scope.row)">编辑</el-button>
								        <el-button
								          size="mini"
								          type="danger"
								          @click="handleDelete(scope.$index, scope.row)">删除</el-button>
								      </template>
                                </el-table-column>
                            </el-table>
                        </el-tab-pane>
                    </el-tabs>
                </el-col>
                <el-col :span='15'>
                    <div class="pro">
                        <div class="title">常用商品</div>
                        <div class="pro-list">
                            <ul>
                               <li v-for='lly in jitui'>
                                   <span>{{lly.name}}</span>
                                   <span class="pro-pri">￥{{lly.pri}}</span>
                               </li>
                            </ul>
                        </div>
                    </div>
                    <div class="pro-type">
                        <el-tabs>
                            <el-tab-pane label='肥宅区'>
                                <ul class="ckList">
                                    <li v-for='val in feizai'>
                                        <span class="foodImg"><img :src="val.src" alt=""></span>
                                        <span class="foodName">{{val.name}}</span>
                                        <span class="foodPri">￥{{val.pri}}</span>
                                        <br />
                                         <el-button type="primary">主要按钮</el-button>
                                    </li>
                                </ul>
                            </el-tab-pane>
                            <el-tab-pane label='儿童区'>
                                <ul class="ckList">
                                    <li v-for='val in feizai1'>
                                        <span class="foodImg"><img :src="val.src" alt=""></span>
                                        <span class="foodName">{{val.name}}</span>
                                        <span class="foodPri">￥{{val.pri}}</span>
                                        <br />
                                         <el-button type="primary">主要按钮</el-button>
                                    </li>
                                </ul>
                            </el-tab-pane>
                            <el-tab-pane label='LLY区'>
                                <ul class="ckList">
                                    <li v-for='val in feizai2'>
                                        <span class="foodImg"><img :src="val.src" alt=""></span>
                                        <span class="foodName">{{val.name}}</span>
                                        <span class="foodPri">￥{{val.pri}}</span>
                                        <br />
                                         <el-button type="primary">主要按钮</el-button>
                                    </li>
                                </ul>
                            </el-tab-pane>
                        </el-tabs>
                    </div>
                </el-col>

            </el-row>
        </div>
    </div>
</template>
<script>
import axios from 'axios'
export default {

  
  name: "Pos",
  data(){
      return {
          tableData:[],
          tableData:[],
          feizai:[],
          jitui:[],
          feizai1:[],
          feizai2:[]
          
      }
  },
  created(){
   	axios.get("http://localhost:8080/static/shiping.json")
   	 .then(res => {
   	 	console.log(res)
            this.tableData = res.data.tableData;
            this.tableData1 = res.data.tableData1;
            this.feizai = res.data.feizai;
            this.jitui = res.data.jitui;
            this.feizai1 = res.data.feizai1;
            this.feizai2 = res.data.feizai2
        })
        .catch(err => {
            console.log('网络出错，无法访问')
        })

  },
  mounted(){
        let h = document.body.clientHeight;
        let list = document.querySelector('#list');
        list.style.height = h + 'px';
   },methods: {
      handleClick(row) {
        console.log(row);
      }
    },
   
}
</script>
<style scoped>
/* 因为虚拟dom的关系，这些元素无法继承到父亲的高度
    所以，我们需要用到js去给予一点帮助
*/

.pro-list{
	width: 100%;
}
.pro-list>ul{
	overflow: hidden;
}
.pro-list>ul>li{
	width: 10%;
	border: 1px solid #272822;
	border-radius: 4px;
	float: left;
	text-align: center;
	margin: 20px 10px;
}
.pro-list>ul>li>span{
	display: block;
}
.pro-list>ul>li>span:last-child{
	color: red;
	font-size: 16px;
}
.ckList{
	width: 100%;
}
.ckList>li{
	height: 400px;
	width: 45%;
	float: left;
	margin: 10px 25px;
	border: 1px solid aqua;
	text-align: center;
}
.ckList>li>span>img{
	width: 100%;
	height: 300px;
	padding-bottom: 10px;
}
.ckList>li>span:nth-child(3){
	color: red;
}
.el-button--primary{
	margin-top: 20px;
}
.el-button--mini, .el-button--mini.is-round {
    padding: 7px 10px;
}
</style>