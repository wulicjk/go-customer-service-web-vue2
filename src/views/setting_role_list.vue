{{template "header" }}
<div id="app" style="width:100%">
    <template>
        <el-container v-loading.fullscreen.lock="fullscreenLoading">

            <el-main class="mainMain">
                <el-button style="margin-bottom: 10px;" @click="" type="primary" size="small">添加角色</el-button>
                <el-table
                        :data="roleList"
                        border
                        style="width: 100%">
                    <el-table-column
                            prop="role_name"
                            label="角色名称">
                    </el-table-column>
                    <el-table-column
                            prop="method"
                            label="允许方法">
                    </el-table-column>
                    <el-table-column
                            prop="path"
                            label="路径">
                    </el-table-column>
                    <el-table-column
                            prop="id"
                            label="操作">
                        <template slot-scope="scope">
                            <el-button @click="showAuthDialog(scope.row.role_id,scope.row.role_name,scope.row.method,scope.row.path)" type="primary" size="small" plain>配置权限</el-button>
                        </template>
                    </el-table-column>
                </el-table>
            </el-main>

        </el-container>
        <el-dialog
                    title="配置权限"
                :visible.sync="roleDialog"
                width="30%"
        >
            <el-form ref="roleForm" :model="roleForm" :rules="rules" label-width="70px">
                <el-form-item label="角色名"  prop="name">
                    <el-input v-model="roleForm.name"></el-input>
                </el-form-item>
                <el-form-item label="方法"  prop="method">
                    <el-input v-model="roleForm.method"></el-input>
                </el-form-item>
                <el-form-item label="路径"  prop="path">
                    <el-input type="textarea" v-model="roleForm.path"></el-input>
                </el-form-item>
            </el-form>
            <span slot="footer" class="dialog-footer">
                <el-button @click="roleDialog = false">取 消</el-button>
                <el-button type="primary" @click="submitRoleForm('roleForm')">确 定</el-button>
              </span>
        </el-dialog>
    </template>

</div>
{{template "setting_bottom" .}}
