<template>
  <div class="table">
    <div class="container">
      <div class="handle-box">
        <el-breadcrumb separator-class="el-icon-arrow-right">
          <el-breadcrumb-item :to="{ path: '/DigitalSign_1' }">Generate Keys</el-breadcrumb-item>
          <el-breadcrumb-item :to="{ path: '/DigitalSign_2' }">Send Public Key to Bob</el-breadcrumb-item>
          <el-breadcrumb-item>Sign and Validate Messages</el-breadcrumb-item>
        </el-breadcrumb>
        <br />
        <br />
        <br />
        <!-- <el-button type="plain" @click="clear">清除/刷新</el-button> -->
      </div>
      <el-row :type="flex" justify="center">
        <el-col :span="6" offset="6">
          <div class="grid-content">
            <el-image style="width: 100px; height: 100px" :src="guiUrl" :fit="fit"></el-image>
            <br />
            <br />
            <br />
            Public key: 
            <div class="truncate-brief"> {{pub_key}} </div>
            <br />
            <br />
            Private key: 
            <div class="truncate-brief"> {{pri_key}} </div>
            <br />
            <br />
            <el-button type="primary" @click="publish">Publish My Public Key</el-button>
          </div>
        </el-col>
        <el-col :span="6" offset="2">
          <div class="grid-content">
            <el-image style="width: 100px; height: 100px" :src="waUrl" :fit="fit"></el-image>
            <br />
            <br />
            <br />
            Alice's Public key: 
            <div class="truncate-brief"> {{pub_key_fromA}} </div>
          </div>
        </el-col>
      </el-row>
      <br />
      <br />
      <el-button style="margin-top: 12px;" @click="previous">Previous</el-button>
      <el-button style="margin-top: 12px;" @click="next">Next</el-button>

      <!-- <br />
      <br />
      <el-row :type="flex" justify="center">
        <el-col :span="6" offset="6">
          <div class="grid-content">
            Public key:
            <div class="truncate"> {{pub_key}} </div>
            <br />
            <br />
            Private key:
            <div class="truncate"> {{pri_key}} </div>
          </div>
        </el-col>
        <el-col :span="6" offset="2">
          <div class="grid-content">
            Alice's Public key: 
            <div class="truncate"> {{pub_key_fromA}} </div>
          </div>
        </el-col>
      </el-row> -->
    </div>
  </div>
</template>

<script>
import gui from "@/assets/img/gui.png";
import wa from "@/assets/img/wa.png";
export default {
  name: "order",
  data() {
    return {
      urlPublish: "/sign/publish",
      guiUrl: gui,
      waUrl: wa,
      pub_key: "",
      pri_key: "",
      pub_key_fromA: ""
    };
  },
  created() {
    this.pub_key = sessionStorage.getItem("pub_key");
    this.pri_key = sessionStorage.getItem("pri_key");
  },
  methods: {
    previous() {
      this.$router.push("/DigitalSign_1");
    },
    next() {
      this.$router.push("/DigitalSign_3");
    },
    publish(user) {
      this.pub_key_fromA = this.pub_key;
    }
  }
};
</script>

<style scoped>
.truncate{
width:300px;
word-break:break-word;
text-overflow:ellipsis;
white-space:no-wrap;
}

.truncate-brief{
width:300px;
overflow:hidden;
text-overflow:ellipsis;
white-space:no-wrap;
}

.handle-box {
  margin-bottom: 20px;
}

.handle-select {
  width: 120px;
}

.handle-input {
  width: 300px;
  display: inline-block;
}
.del-dialog-cnt {
  font-size: 16px;
  text-align: center;
}
.table {
  width: 100%;
  font-size: 14px;
}
.red {
  color: #ff0000;
}
.mr10 {
  margin-right: 10px;
}
.el-row {
  margin-bottom: 20px;
}
.el-col {
  border-radius: 4px;
}
.bg-purple-dark {
  background: #99a9bf;
}
.bg-purple {
  background: #d3dce6;
}
.bg-purple-light {
  background: #e5e9f2;
}
.grid-content {
  border-radius: 4px;
  min-height: 36px;
}
.row-bg {
  padding: 10px 0;
  background-color: #f9fafc;
}
</style>
