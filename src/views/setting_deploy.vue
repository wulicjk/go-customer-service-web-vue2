<template>
  <div id="app" style="width:100%">
    <el-container>

      <el-main class="mainMain">
        <el-tabs type="border-card">
          <el-tab-pane label="普通模式">
            <el-descriptions style="margin-bottom: 10px;" direction="vertical" :column="1" border>
              <el-descriptions-item label="通用聊天链接">
                <a style="margin-right: 10px">{{host}}/chatIndex?kefu_id=kefu2</a>
                <el-button size="mini" v-on:click="copyText(host+'/chatIndex?kefu_id=kefu2')">复制</el-button>
              </el-descriptions-item>
            </el-descriptions>
          </el-tab-pane>
          <el-tab-pane label="弹窗模式">

          </el-tab-pane>
        </el-tabs>
      </el-main>

    </el-container>
  </div>
</template>


<script>
import {copyText, getBaseUrl} from "../../public/static/js/functions";

export default {
  data(){
    return{
      host: getBaseUrl(),
    }
  },
  methods:{
    copyText
  }
}
</script>