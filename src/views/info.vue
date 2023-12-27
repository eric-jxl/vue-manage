<script setup lang="ts">
	import axios from 'axios';
	import {reactive, onMounted} from 'vue'

	const data = reactive({"users": []});
	const formatDate = (timestamp: any) => {
		const date = new Date(timestamp);
		const year = date.getFullYear();
		const month = ('0' + (date.getMonth() + 1)).slice(-2);
		const day = ('0' + date.getDate()).slice(-2);
		const hours = ('0' + date.getHours()).slice(-2);
		const minutes = ('0' + date.getMinutes()).slice(-2);
		const seconds = ('0' + date.getSeconds()).slice(-2);
		return `${year}-${month}-${day}`;
	};

	onMounted(() => {
		axios.get('http://localhost:5000/login/').then(response => {
			data.users  = response.data
		}).catch((error) => {
			console.error(error);
		})
	});


</script>

<template>
    <div class="container">
		<div class="row" style=";font-family: cursive">
			<div class="table-responsive col-auto">
				<h1 style="color:#395e83">用户信息</h1>
				<br><br>
				<!--element-plus 写法-->
				<el-table :data="data.users" border class="table table-bordered"
						  :row-class-name="table-row" :default-sort="{prop:'uid',order: 'descending'}">
					<el-table-column prop="uid" label="ID" width="55" align="center"></el-table-column>
					<el-table-column prop="login" label="用户" width="55"></el-table-column>
					<el-table-column prop="password" label="密码"></el-table-column>
					<el-table-column prop="create_date" label="创建时间">
						<template #default="{ row }">
							{{ formatDate(row.create_date) }}
						</template>
					</el-table-column>
				</el-table>


<!--                <button type="button" class="btn btn-success btn-sm btn_left">Add User</button>-->
<!--                <br><br>-->
<!--                <table class="table table-bordered">-->
<!--                    <thead>-->
<!--                    <tr>-->
<!--                        <th scope="col">序列</th>-->
<!--                        <th scope="col">用户</th>-->
<!--                        <th scope="col">密码</th>-->
<!--                        <th scope="col">创建时间</th>-->
<!--                        <th scope="col">操作</th>-->
<!--                    </tr>-->
<!--                    </thead>-->
<!--                    <tbody>-->
<!--                        <tr v-for="(user) in data.users" :key="user.uid">-->
<!--                            <td>{{user.uid}}</td>-->
<!--                            <td>{{user.login}}</td>-->
<!--                            <td>{{user.password}}</td>-->
<!--                            <td>{{ formatDate(user.create_date ) }}</td>-->

<!--                            <td>-->
<!--                                <div class="btn-group" role="group">-->
<!--                                    <button type="button" class="btn btn-warning btn-sm">Update</button>-->
<!--                                    <button type="button" class="btn btn-danger btn-sm">Delete</button>-->
<!--                                </div>-->
<!--                            </td>-->
<!--                        </tr>-->
<!--                    </tbody>-->
<!--                </table>-->

            </div>
        </div>
    </div>


</template>

<style scoped>
	.btn_left {
		float: left;
	}

	.table-responsive {
		overflow-x: auto;
	}

	.el-table .warning-row {
		--el-table-tr-bg-color: var(--el-color-warning-light-9);
	}

	.table-row:nth-child(2n) {
		--el-table-tr-bg-color: var(--el-color-success-light-9);
	}

</style>
