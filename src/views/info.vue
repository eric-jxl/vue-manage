<script>
import axios from 'axios';

export default {
    name: 'Info',
    data() {
        return {
            users: [],
        }
    },
    methods: {
        getMessage() {
            const path = 'http://localhost:5000/login/';
            axios.get(path)
                .then((res) => {
                    this.users = res.data;
                })
                .catch((error) => {
                    console.error(error);
                });
        },
        formatDate(timestamp) {
            const date = new Date(timestamp);
            const year = date.getFullYear();
            const month = ('0' + (date.getMonth() + 1)).slice(-2);
            const day = ('0' + date.getDate()).slice(-2);
            const hours = ('0' + date.getHours()).slice(-2);
            const minutes = ('0' + date.getMinutes()).slice(-2);
            const seconds = ('0' + date.getSeconds()).slice(-2);
            return `${year}-${month}-${day} ${hours}:${minutes}:${seconds}`;
        },
        // 在maskedPassword计算属性中，我们使用了JavaScript的正则表达式来将密码字符串中的字符替换为星号，同时保留前四个和最后四个字符以便于用户识别。当isVisible标记为true时，计算属性将直接返回未加掩码的原始密码字符串。

    },
    created() {
        this.getMessage();
    },

};
</script>

<template>
    <div class="container">
        <div class="row" style=";font-family: cursive">
            <div class="table-responsive col-auto">
                <h1 style="color:dodgerblue">用户信息</h1>
                <br><br>
                <button type="button" class="btn btn-success btn-sm btn_left">Add User</button>
                <br><br>
                <table class="table table-bordered">
                    <thead>
                    <tr>
                        <th scope="col">序列</th>
                        <th scope="col">用户</th>
                        <th scope="col">密码</th>
                        <th scope="col">创建时间</th>
                        <th scope="col">操作</th>
                    </tr>
                    </thead>
                    <tbody>
                        <tr v-for="(user) in users" :key="user.uid">
                            <td>{{user.uid}}</td>
                            <td>{{user.login}}</td>
                            <td>{{user.password}}</td>
                            <td>{{ formatDate(user.create_date ) }}</td>

                            <td>
                                <div class="btn-group" role="group">
                                    <button type="button" class="btn btn-warning btn-sm">Update</button>
                                    <button type="button" class="btn btn-danger btn-sm">Delete</button>
                                </div>
                            </td>
                        </tr>
                    </tbody>
                </table>

                <el-table :data="users" border class="table table-bordered" ref="multipleTable" header-row-class-name="table_header">
                    <el-table-column prop="uid" label="ID" width="55" align="center"></el-table-column>
                    <el-table-column prop="login" label="用户" width="55"></el-table-column>
                    <el-table-column prop="password" label="密码"></el-table-column>
                    <el-table-column prop="create_date" label="创建时间">
                        <template #default="{ row }">
                            {{ formatDate(row.create_date) }}
                        </template>
                    </el-table-column>
                </el-table>

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

</style>
