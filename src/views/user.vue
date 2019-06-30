<template>
  <div class="main">
    <el-table :data="userdata" stripe style="width: 100%">
      <el-table-column prop="username" label="姓名" width="180"></el-table-column>

      <el-table-column prop="email" label="邮箱" width="180"></el-table-column>

      <el-table-column prop="mobile" label="电话"></el-table-column>

        
            <el-table-column prop="address" label="用户状态">
                <template v-slot='{row}'>
                    <!-- {{row}} -->
                <el-switch v-model="row.type" active-color="#13ce66" inactive-color="#ff4949"></el-switch>
                </template>
            </el-table-column>
        
      

      <el-table-column prop="address" label="操作">
        <el-button type="primary" plain size="mini">
          <i class="el-icon-edit"></i>
        </el-button>
        <el-button type="success" plain size="mini">
          <i class="el-icon-delete"></i>
        </el-button>
        <el-button type="warning" plain size="mini">
          <i class="el-icon-check"></i>分配角色
        </el-button>
      </el-table-column>

    </el-table>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      userdata: []
    };
  },
  created() {
    axios({
      url: "http://localhost:8888/api/private/v1/users",
      params: {
        pagenum: 1,
        pagesize: 5
      },
      headers: {
        Authorization: localStorage.getItem("token")
      }
    }).then(res => {
      res = res.data.data.users;
      this.userdata = res;
    });
  }
};
</script>

