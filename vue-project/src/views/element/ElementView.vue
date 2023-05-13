<template>

    <div>
        <!--        button 按钮-->
        <el-row>
            <el-button>默认按钮</el-button>
            <el-button type="primary">主要按钮</el-button>
            <el-button type="success">成功按钮</el-button>
            <el-button type="info">信息按钮</el-button>
            <el-button type="warning">警告按钮</el-button>
            <el-button type="danger">危险按钮</el-button>
        </el-row>

        <!--        table 按钮-->

        <el-table
                :data="tableData"
                style="width: 100%">
            <el-table-column
                    label="日期"
                    prop="date"
                    width="180">
            </el-table-column>
            <el-table-column
                    label="姓名"
                    prop="name"
                    width="180">
            </el-table-column>
            <el-table-column
                    label="地址"
                    prop="address">
            </el-table-column>
        </el-table>

        <!--        分页代码-->
        <el-pagination
                :total="1000"
                background

                layout="sizes, prev, pager, next,jumper , total"
                @size-change="handleSizeChange"
                @current-change="handleCurrentChange">
        </el-pagination>
        <br><br>


        <!-- Table -->
        <el-button type="text" @click="dialogTableVisible = true">打开嵌套表格的 Dialog</el-button>

        <el-dialog :visible.sync="dialogTableVisible" title="收货地址">
            <el-table :data="gridData">
                <el-table-column label="日期" property="date" width="150"></el-table-column>
                <el-table-column label="姓名" property="name" width="200"></el-table-column>
                <el-table-column label="地址" property="address"></el-table-column>
            </el-table>
        </el-dialog>

        <el-button type="text" @click="outerVisible = true">点击打开外层 Dialog</el-button>

        <el-dialog :visible.sync="outerVisible" title="外层 Dialog">
            <el-dialog
                    :visible.sync="innerVisible"
                    append-to-body
                    title="内层 Dialog"
                    width="30%">
            </el-dialog>
            <div slot="footer" class="dialog-footer">
                <el-button @click="outerVisible = false">取 消</el-button>
                <el-button type="primary" @click="innerVisible = true">打开内层 Dialog</el-button>
            </div>
        </el-dialog>
        <br>
        <br>

        <!--       对话框组件进入 表单组件-->
        <el-button type="text" @click="dialogFormVisible = true">表单</el-button>

        <el-dialog :visible.sync="dialogFormVisible" title="form">
            <el-form ref="form" :model="form" label-width="80px">
                <el-form-item label="活动名称">
                    <el-input v-model="form.name"></el-input>
                </el-form-item>
                <el-form-item label="活动区域">
                    <el-select v-model="form.region" placeholder="请选择活动区域">
                        <el-option label="区域一" value="shanghai"></el-option>
                        <el-option label="区域二" value="beijing"></el-option>
                    </el-select>
                </el-form-item>
                <el-form-item label="活动时间">
                    <el-col :span="11">
                        <el-date-picker v-model="form.date1" placeholder="选择日期" style="width: 100%;"
                                        type="date"></el-date-picker>
                    </el-col>
                    <el-col :span="2" class="line">-</el-col>
                    <el-col :span="11">
                        <el-time-picker v-model="form.date2" placeholder="选择时间"
                                        style="width: 100%;"></el-time-picker>
                    </el-col>
                </el-form-item>
                <el-form-item>
                    <el-button type="primary" @click="onSubmit">立即创建</el-button>
                    <el-button>取消</el-button>
                </el-form-item>
            </el-form>
        </el-dialog>

        <br><br>
    </div>
</template>

<script>
export default {
    data() {
        return {
            form: {
                name: '',
                region: '',
                date1: '',
                date2: '',
                delivery: false,
                type: [],
                resource: '',
                desc: ''
            },
            tableData: [{
                date: '2016-05-02',
                name: '王小虎',
                address: '上海市普陀区金沙江路 1518 弄'
            }],
            gridData: [{
                date: '2016-05-02',
                name: '王小虎',
                address: '上海市普陀区金沙江路 1518 弄'
            }],
            dialogTableVisible: false,
            dialogFormVisible: false,
            outerVisible: false,
            innerVisible: false,

        }
    },
    methods: {
        handleCurrentChange: function (val) {
            alert("页码变化记录" + val)
        },
        handleSizeChange: function (val) {
            alert("每页变化记录" + val)
        },
        onSubmit: function () {
            alert(JSON.stringify(this.form))
        }
    }
}
</script>

<style>

</style>