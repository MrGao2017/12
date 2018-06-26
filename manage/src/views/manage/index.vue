<template>
    <div class="manage tc">
		<button @click="add">新增</button>
		<div class="input-area" v-show="showAdd">
			<input placeholder="请输入人员姓名" v-model="nameValue">
			<button @click="addName">确定</button>
		</div>
		<table>
			<tr>
				<th>姓名</th>
				<th>操作</th>
			</tr>
			<tr v-for="(item,index) in peoples" :key="index">
				<td>
					{{item.name}}
				</td>
				<td>
                    <span @click="edit(item,index)">编辑</span>
                    <span @click="del(index)">删除</span>
                </td>
			</tr>
		</table>
        <fotter-nav :class="{'isManage':'isNowPage'}"></fotter-nav>
		<div class="wrap" v-show="shoeEdit">
			<div class="content">
				<input type="text" placeholder="请输入新姓名" v-model="newName">
				<button @click="cancel">取消</button>
				<button @click="editName">确定</button>
			</div>
		</div>
		
	</div>
</template>


<style>
	.manage{padding-bottom:50px;}
	.manage >button{width:200px; height:40px; line-height:40px; background-color:#41b883; border: none; border-radius:5px; font-size:16px; color:#fff;}
	table{width:100%; max-width:500px; margin:0 auto; margin-top:20px;}
	.input-area input{width: 200px; height: 40px; line-height:40px; margin:20px 0; outline:none; border:1px solid #333;}
	.input-area button{ width:60px; height: 40px; line-height:40px; background-color:#41b883; border: none; border-radius:5px; font-size:16px; color:#fff;}
	th,td{width:100px;}
	tr input{width:100px; height:30px; padding-left:10px; outline:none; border:1px solid #333;}
	.wrap{display:table; position:fixed; top:0; left:0; height:100%; width:100%; background:rgba(0,0,0,.8); z-index: 10;}
	.wrap .content{display:table-cell; vertical-align:middle;}
	.wrap .content input{height: 40px; line-height: 40px; display:block; margin:0 auto; margin-bottom:10px; font-size:16px;}
	.wrap .content button{width:100px; height: 30px; line-height: 30px; background-color:#41b883; border: none; border-radius:5px; font-size:16px; color:#fff;}
</style>
</style>


<script>
    import FotterNav from '@/components/fotter.vue'
    export default {
        components:{
            FotterNav
        },
        data(){
            return {
               isNowPage:true ,
               showAdd:false,
               nameValue:'',
               shoeEdit:false,
               newName:'',   //记录改变后的值
               editId:0,     //记录改变元素的下标
               peoples: [
                    {
                        'name':'Jack'
                    },
                    {
                        'name':'Joe'
                    }
                ],
            }
        },
        methods:{
            add(){
                this.showAdd = !this.showAdd
            },
            addName(){  //新增
               let v =  this.nameValue;
               if(v.trim() === ''){
                   alert('请输入新增人员姓名')
               }else{
                   this.peoples.push({
                       'name':v
                   })
                   this.nameValue = ''
               }
            },
            edit(item,index){  //编辑
               console.log(index)
                this.shoeEdit = true
                this.editId = index
                this.newName = item.name
            },
            del(index){   //删除
                this.peoples.splice(index,1)
            },
            cancel(){   //取消
                this.shoeEdit = false
            },
            editName(){    //编辑确定
             this.shoeEdit = false
             console.log(this.newName)
             this.peoples[this.editId].name = this.newName    
            }
        }
       
    }
</script>
