<template>
    <div style="width:100%">
      <Header></Header>
        <el-container v-loading.fullscreen.lock="fullscreenLoading">

            <el-main class="mainMain">
                <el-button style="margin-bottom: 10px;" @click="addWelcome" type="primary" size="small">添加欢迎
                </el-button>
                <el-table
                        :data="noticeList"
                        border
                        style="width: 100%">
                    <el-table-column
                            prop="content"
                            label="回复内容">
                        <template slot-scope="scope">
                            <el-input @change="setWelcomeItem(scope.row.id,scope.row.content)"
                                      v-model="scope.row.content"></el-input>
                        </template>
                    </el-table-column>
                    <el-table-column
                            prop="ctime"
                            label="添加时间">
                    </el-table-column>
                    <el-table-column
                            prop="id"
                            label="操作">
                        <template slot-scope="scope">
                            <el-button v-show="scope.row.is_default==0" @click="deleteWelcome(scope.row.id)"
                                       type="danger" size="small" plain>删除
                            </el-button>
                        </template>
                    </el-table-column>
                </el-table>
            </el-main>

        </el-container>
        <el-dialog
                title="欢迎"
                :visible.sync="welcomeDialog"
                width="30%"
        >
            <el-form ref="welcomeForm" :model="welcomeForm" :rules="rules" label-width="70px">
                <el-form-item label="内容" prop="content">
                    <el-input v-model="welcomeForm.content"></el-input>
                </el-form-item>
            </el-form>
            <span slot="footer" class="dialog-footer">
                <el-button @click="welcomeDialog = false">取 消</el-button>
                <el-button type="primary" @click="submitWelcomeForm('welcomeForm')">确 定</el-button>
              </span>
        </el-dialog>
      <setting_bottom></setting_bottom>
    </div>
</template>
<script>
import setting_bottom from "@/template/setting_bottom.vue";
import Header from "@/template/header.vue";

export default {
  components:{
    setting_bottom,
    Header
  }
}
</script>
