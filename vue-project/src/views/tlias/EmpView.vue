<template>
    <div>
        <el-container style="height: 700px; border: 1px solid #eee">
            <el-header style="font-size: 40px">布局并用axios导入数据</el-header>
            <el-container>
                <el-aside width="200px">
                    <el-menu :default-openeds="['1', '3']">
                        <el-submenu index="1">
                            <template slot="title"><i class="el-icon-message"></i>系统信息</template>
                            <el-menu-item-group>
                                <el-menu-item index="1-1">部门</el-menu-item>
                                <el-menu-item index="1-2">员工</el-menu-item>
                            </el-menu-item-group>
                        </el-submenu>
                    </el-menu>
                </el-aside>
                <el-main>
                    <!--                    表单-->
                    <el-form :inline="true" :model="searchForm" class="demo-form-inline">

                        <el-form-item label="name">
                            <el-input v-model="searchForm.name" placeholder="name"></el-input>
                        </el-form-item>
                        <el-form-item label="sex">
                            <el-select v-model="searchForm.gender" placeholder="sex">
                                <el-option label="man" value="1"></el-option>
                                <el-option label="feman" value="2"></el-option>
                            </el-select>
                        </el-form-item>
                        <el-form-item label="Entrydate">
                            <el-date-picker
                                v-model="searchForm.entrydate"
                                type="daterange"
                                range-separator="至"
                                start-placeholder="开始日期"
                                end-placeholder="结束日期">
                            </el-date-picker>
                        </el-form-item>
                        <el-form-item>
                            <el-button type="primary" @click="onSubmit">查询</el-button>
                        </el-form-item>
                    </el-form>
<!--                    表格-->
                    <el-table :data="tableData" border>

                        <el-table-column label="Name" prop="name" width="180"></el-table-column>
                        <el-table-column label="Image" prop="image" width="180"></el-table-column>
                        <el-table-column label="Gender" prop="gender" width="180"></el-table-column>
                        <el-table-column label="Job" prop="job" width="120"></el-table-column>
                        <el-table-column label="Entrydate" prop="entrydate" width="180"></el-table-column>
                        <el-table-column label="Updatetime" prop="updatetime" width="230"></el-table-column>
                        <el-table-column label="Option">
                            <el-button type="primary" size="mini">edit</el-button>
                            <el-button type="danger" size="mini">delete</el-button>
                        </el-table-column>
                    </el-table>
                    <br>
<!--                    分页条-->
                    <el-pagination
                        :total="1000"
                        background

                        layout="sizes, prev, pager, next,jumper , total"
                        @size-change="handleSizeChange"
                        @current-change="handleCurrentChange">
                    </el-pagination>
                </el-main>
            </el-container>
        </el-container>
    </div>
</template>

<script>
export default {
    data(){
        return{
            tableDate:[],
            searchForm: {
                name: '',
                gender: '',
                entrydate:[]
            }
        }
    },
    methods: {
        handleCurrentChange: function (val) {
            alert("页码变化记录" + val)
        },
        handleSizeChange: function (val) {
            alert("每页变化记录" + val)
        },
        onSubmit() {
            alert("serach")
        }
    }
}
</script>

<style scoped>


.el-header {
    background-color: #B3C0D1;
    color: #333;
    text-align: center;
    line-height: 60px;
}

.el-aside {
    background-color: #D3DCE6;
    color: #333;
    text-align: center;
    line-height: 200px;
}

.el-main {
    background-color: #E9EEF3;
    color: #333;

}
</style>