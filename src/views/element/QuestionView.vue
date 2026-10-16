<template>
  <el-container class="question-page">
    <el-header class="question-header" height="50px">Quiz后台管理</el-header>

    <el-container class="question-layout">
      <el-aside class="question-sidebar" width="200px">
        <el-menu router :default-openeds="['1']" :default-active="$route.path">
          <el-submenu index="1">
            <template slot="title">管理选项</template>
            <el-menu-item-group>
              <el-menu-item index="/user">
                用户管理
              </el-menu-item>
              <el-menu-item index="/question">
                题目管理
              </el-menu-item>
            </el-menu-item-group>
          </el-submenu>
        </el-menu>
      </el-aside>

      <el-main class="question-main">
        <!-- 查询栏 -->
        <el-form :inline="true" :model="formInline" class="question-search">
          <el-form-item label="题目">
            <el-input
              v-model="formInline.user"
              placeholder="请输入题目关键词"
            ></el-input>
          </el-form-item>
          <el-form-item>
            <el-button type="primary" @click="onSubmit">查询</el-button>
          </el-form-item>
          <el-form-item>
            <el-button type="success" @click="onAddNewQuestion"
              >添加题目</el-button
            >
          </el-form-item>
        </el-form>

        <!-- 序号、题目、选项、答案、操作 -->
        <el-table :data="tableData" class="question-table">
          <el-table-column type="index" label="序号" width="50" align="center">
          </el-table-column>
          <el-table-column prop="question" label="题目" min-width="250">
          </el-table-column>
          <el-table-column label="选项" min-width="260">
            <template slot-scope="scope">
              {{ Object.values(scope.row.options).join("，") }}
            </template>
          </el-table-column>
          <el-table-column label="答案" min-width="180">
            <template slot-scope="scope">
              {{ scope.row.options[scope.row.answer] }}
            </template>
          </el-table-column>
          <el-table-column label="操作" min-width="180">
            <template slot-scope="scope">
              <el-button
                size="mini"
                @click="handleEdit(scope.$index, scope.row)"
              >
                编辑
              </el-button>
              <el-button
                size="mini"
                type="danger"
                @click="handleDelete(scope.$index, scope.row)"
                >删除</el-button
              >
            </template>
          </el-table-column>
        </el-table>

        <el-pagination
          class="question-pagination"
          background
          layout="prev, pager, next"
          :total="1000"
        ></el-pagination>

        <!-- 添加题目对话框 -->
        <el-dialog title="添加题目" :visible.sync="dialogFormVisible">
          <el-form :model="form" :label-width="formLabelWidth">
            <el-form-item label="题目">
              <el-input v-model="form.question" autocomplete="off"></el-input>
            </el-form-item>
            <el-form-item label="选项A">
              <el-input v-model="form.optiona" autocomplete="off"></el-input>
            </el-form-item>
            <el-form-item label="选项B">
              <el-input v-model="form.optionb" autocomplete="off"></el-input>
            </el-form-item>
            <el-form-item label="选项C">
              <el-input v-model="form.optionc" autocomplete="off"></el-input>
            </el-form-item>
            <el-form-item label="选项D">
              <el-input v-model="form.optiond" autocomplete="off"></el-input>
            </el-form-item>
            <el-form-item label="答案">
              <el-input v-model="form.answer" autocomplete="off"></el-input>
            </el-form-item>
          </el-form>
          <div slot="footer" class="dialog-footer">
            <el-button @click="dialogFormVisible = false">取 消</el-button>
            <el-button type="primary" @click="dialogFormVisible = false"
              >确 定</el-button
            >
          </div>
        </el-dialog>
      </el-main>
    </el-container>
  </el-container>
</template>

<script>
export default {
  data() {
    return {
      dialogFormVisible: false,
      formLabelWidth: "80px",

      form: {
        question: "",
        optiona: "",
        optionb: "",
        optionc: "",
        optiond: "",
        answer: "",
      },

      tableData: [
        {
          id: "1",
          question: "法国的首都是哪个城市？",
          options: {
            A: "巴黎",
            B: "伦敦",
            C: "柏林",
            D: "马德里",
          },
          answer: "A",
        },
        {
          id: "2",
          question: "中国的首都是哪个城市？",
          options: {
            A: "北京",
            B: "上海",
            C: "广州",
            D: "深圳",
          },
          answer: "A",
        },
        {
          id: "3",
          question: "美国的首都是哪个城市？",
          options: {
            A: "华盛顿",
            B: "纽约",
            C: "洛杉矶",
            D: "芝加哥",
          },
          answer: "A",
        },
        {
          id: "4",
          question: "日本的首都是哪个城市？",
          options: {
            A: "东京",
            B: "大阪",
            C: "京都",
            D: "名古屋",
          },
          answer: "A",
        },
      ],
      formInline: {
        user: "",
        region: "",
      },
    };
  },
  methods: {
    onAddNewQuestion() {
      this.dialogFormVisible = true;
    },
    onSubmit() {
      console.log("submit!");
    },
    handleEdit(index, row) {
      console.log(index, row);
    },
    handleDelete(index, row) {
      console.log(index, row);
    },
  },
};
</script>

<style scoped>
.question-page {
  text-align: left;
}

.question-header {
  background-color: rgb(238, 241, 246);
  color: #000;
  font-size: 40px;
  line-height: 50px;
}

.question-layout {
  min-height: 420px;
}

.question-sidebar {
  background-color: rgb(238, 241, 246);
}

.question-sidebar .el-menu {
  min-height: 100%;
  background-color: transparent;
}

.question-sidebar .el-submenu {
  background-color: #fff;
}

.question-sidebar .el-menu-item.is-active {
  background-color: #ecf5ff;
}

.question-main {
  min-width: 0;
  padding: 20px;
}

.question-search .el-input {
  width: 210px;
}

.question-table {
  width: 100%;
}

.question-pagination {
  margin-top: 24px;
  text-align: left;
}
</style>
