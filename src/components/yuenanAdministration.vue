<template>
  <!-- 管控中心 -->
      <!---->
  <div class="Administration" v-on:dblclick="shuangji()">
    <!-- 顶部logo -->
    <div class="index-top_nav">
      <!-- <img src="..\assets\Administration\gk_logo.png" alt> -->
      <!-- <img src="../assets/index/top_nav.png" alt=""> -->
      <p
        style="text-align: center; font-family: 庞门正道标题体; font-size: 180px;color:#00ecfc; letter-spacing:15px;"
      >
        <img
          src="..\assets\Administration\nav_logo.png"
          alt
          style="vertical-align: middle;margin-top: -37px;"
        />
        <span>数据管控标准</span>
      </p>
    </div>
    <!-- 返回主页 -->
    <div class="index-esc">
      <span @click="esc">
        <img src="..\assets\Administration\home.png" alt />
        返回
      </span>
      <!--<span @click="syj">-->
      <!--<img src="..\assets\Administration\home.png" alt />-->
      <!--上级-->
      <!--</span>-->
    </div>
    <!-- 显示用户登陆和退出 -->
    <login></login>

    <div id="bgColor">
      <div class="ChemicalTable">
        <!--<Table :columns="historyColumns" :data="historyData" height = "1500"></Table>-->
        <div id="building-top"  style="position: relative">
          <button @click="handlpe()" style="cursor: pointer;position: absolute;top: -150px;right: 0;width: 250px;
      height: 80px;line-height: 80px; background: none; color: #fff" >展开</button>
          <!-- #040A53表格背景色 -->
          <!-- :header-cell-style="{background:'#040A53'}" -->
          <el-table
            :data="historyData"
            :span-method="arraySpanMethod"
            :header-cell-style="{background:'#040A53'}"
            :row-style="{background: '#040A53',margin:'200px',height:'200px;',color:'#ffffff'}"
            border
            height="1500"
            ref="table"
            style="width: 100%;text-align: center;color: black; background:#040A53">
            
            <el-table-column
              label="基础信息"
              align="center"
              width="450">
              <el-table-column
                prop="xh"
                label="序号"
                align="center"
                width="200">
              </el-table-column>
              <el-table-column
                prop="pz"
                label="品种"
                align="center"
                width="450">
              </el-table-column>
              <el-table-column
                prop="sh"
                label="色号"
                align="center"
                width="350">
              </el-table-column>
            </el-table-column>
            <el-table-column
              label="原材料标准"
              align="center"
              width="450">
              <el-table-column
                prop="yclzcl"
                label="标准织成率"
                align="center"
                width="400">
              </el-table-column>
              <el-table-column
                prop="yclzhichenglu"
                label="标准制成率"
                align="center"
                width="400">
              </el-table-column>
              <el-table-column
                label="经纱信息"
                align="center"
                width="400">
                  <el-table-column
                    prop="ycljssm"
                    label="纱名"
                    align="center"
                    width="200">
                </el-table-column>
                <el-table-column
                  prop="ycljstf"
                  label="头份"
                  align="center"
                  width="200">
                </el-table-column>
                <el-table-column
                  prop="ycljsbmyl"
                  label="百米用量(kg)"
                  align="center"
                  width="350">
                </el-table-column>
              </el-table-column>
              <el-table-column
                label="纬纱信息"
                align="center"
                width="400">
                <el-table-column
                  prop="yclwssm"
                  label="纱名"
                  align="center"
                  width="200">
                </el-table-column>
                <el-table-column
                  prop="yclwsbmyl"
                  label="百米用量(kg)"
                  align="center"
                  width="350">
                </el-table-column>
              </el-table-column>
            </el-table-column>
            <el-table-column
              label="辅助材料标准"
              align="center"
              width="450">
              <el-table-column
                prop="fzclbzsrl"
                label="标准上染率%"
                align="center"
                width="400">
              </el-table-column>
              <el-table-column
                prop="fzcldlq"
                label="靛蓝前染料标准浓度"
                align="center"
                width="400">
              </el-table-column>
              <el-table-column
                label="靛蓝母液标准配方"
                align="center"
                width="400">
                <el-table-column
                  prop="fzclmydl"
                  label="靛蓝(g/L)"
                  align="center"
                  width="250">
                </el-table-column>
                <el-table-column
                  prop="fzclmysj"
                  label="烧碱(g/L)"
                  align="center"
                  width="250">
                </el-table-column>
                <el-table-column
                  prop="fzclmybxf"
                  label="保险粉(g/L)"
                  align="center"
                  width="250">
                </el-table-column>
              </el-table-column>
              <el-table-column
                prop="fzcldlh"
                label="靛蓝后染料标准浓度"
                align="center"
                width="400">
              </el-table-column>
              <el-table-column
                label="助剂标准配方"
                align="center"
                width="400">
                <el-table-column
                  prop="fzclzjsj"
                  label="烧碱(g/L)"
                  align="center"
                  width="250">
                </el-table-column>
                <el-table-column
                  prop="fzclzjbxf"
                  label="保险粉(g/L)"
                  align="center"
                  width="250">
                </el-table-column>
              </el-table-column>
              <el-table-column
                prop="fzclbzsjl"
                label="标准上浆率%"
                align="center"
                width="400">
              </el-table-column>
              <el-table-column
                label="浆液标准配方"
                align="center"
                width="400">
                <el-table-column
                  prop="fzclpfdfg"
                  label="高粘淀粉(g/L)"
                  align="center"
                  width="250">
                </el-table-column>
                <el-table-column
                  prop="fzclpfdfd"
                  label="低粘淀粉(g/L)"
                  align="center"
                  width="250">
                </el-table-column>
                <el-table-column
                  prop="fzclpfss"
                  label="SS浆料(g/L)"
                  align="center"
                  width="250">
                </el-table-column>
                <el-table-column
                  prop="fzclpfpva"
                  label="PVA"
                  align="center"
                  width="250">
                </el-table-column>
              </el-table-column>
            </el-table-column>

            <el-table-column v-if="show">
              <el-table-column
                label="过程耗能标准"
                align="center"
                width="400">
                <el-table-column

                  label="浆染过程耗能"
                  align="center"
                  width="250">
                  <el-table-column
                    prop="gchnjrrs"
                    label="染色用水(m³/万米)"
                    align="center"
                    width="350">
                  </el-table-column>
                  <el-table-column
                    prop="gchnjrrq"
                    label="染色用汽(m³/万米)"
                    align="center"
                    width="350">
                  </el-table-column>
                  <el-table-column
                    prop="gchnjrjs"
                    label="浆纱用水(m³/万米)"
                    align="center"
                    width="350">
                  </el-table-column>
                  <el-table-column
                    prop="gchnjrjq"
                    label="浆纱用汽(m³/万米)"
                    align="center"
                    width="350">
                  </el-table-column>
                </el-table-column>
                <el-table-column
                  label="织布空调耗能"
                  align="center"
                  width="350">
                  <el-table-column
                    prop="gchnzb"
                    label="用水(m³/万米)"
                    align="center"
                    width="350">
                  </el-table-column>
                </el-table-column>
                <el-table-column
                  label="后整过程耗能"
                  align="center"
                  width="350">
                  <el-table-column
                    prop="gchnhz1"
                    label="用水(m³/万码)"
                    align="center"
                    width="350">
                  </el-table-column>
                  <el-table-column
                    prop="gchnhz2"
                    label="用汽(m³/万码)"
                    align="center"
                    width="350">
                  </el-table-column>
                  <el-table-column
                    prop="gchnhz3"
                    label="用天燃气(m³/万码)"
                    align="center"
                    width="350">
                  </el-table-column>
                </el-table-column>
              </el-table-column>
              <el-table-column
                label="过程耗能标准"
                align="center"
              >
                <el-table-column
                  prop="gbbzys"
                  label="产生原水(m³/万码)"
                  align="center"
                  width="350">
                </el-table-column>
                <el-table-column
                  prop="gbbzpf"
                  label="处理排放(m³/万码)"
                  align="center"
                  width="350">
                </el-table-column>
                <el-table-column
                  prop="gbbzcod"
                  label="COD"
                  align="center"
                  width="250">
                </el-table-column>
                <el-table-column
                  prop="gbbzad"
                  label="氨氮"
                  align="center"
                  width="200">
                </el-table-column>
                <el-table-column
                  prop="gbbzsd"
                  label="色度"
                  align="center"
                  width="200">
                </el-table-column>
                <el-table-column
                  prop="gbbzwd"
                  label="温度"
                  align="center"
                  width="200">
                </el-table-column>
                <el-table-column
                  prop="gbbzlhw"
                  label="硫化物"
                  align="center"
                  width="250">
                </el-table-column>
                <el-table-column
                  prop="gbbzph"
                  label="pH"
                  align="center"
                  width="200">
                </el-table-column>
              </el-table-column>
            </el-table-column>
          </el-table>
        </div>
        <div style="margin: 70px;overflow: hidden">
            <div style="float: right;">
                <!--<Page :total="pageAll" :current="1" @on-change="xuanran" page-size = '20' ></Page>-->
            </div>
        </div>
        <!-- <Page :total="dataCount" :page-size="pageSize" show-total class="paging" @on-change="changepage" @on-page-size-change="pages" show-sizer show-elevator show-total></Page> -->
      </div>
    </div>
    <div v-show="None">
      <el-upload
        class="upload-demo"
        style="float: left"
        name="file"
        ref="upload"
        multiple 
        :action="updataUrl+'/api/UploadFilesSjgk'"
        :on-preview="handlePreview"
        :on-remove="handleRemove"
        :file-list="fileList"
        :auto-upload="false">
        <el-button slot="trigger" size="small" type="primary" style="width: 240px;height: 80px;float: left;">选取文件</el-button>
        <el-button style="margin-left: 10px;width: 240px;height: 80px;float: left" size="small" type="success" @click="submitUpload">上传到服务器</el-button>
        <div slot="tip" class="el-upload__tip" style="clear: both">只能上传jpg/png文件，且不超过500kb</div>
      </el-upload>
    </div>
    <!-- <foot></foot> -->
  </div>
</template>

<script>
  import {mapState,mapGetters} from 'vuex'
  import yuenanUrl from "../assets/url";
  import shaoguanUrl from '../assets/s_url';
import axios from "axios";
import foot from "./foot.vue";
import login from "./login_assembly.vue";
import Vue from 'vue';
import {Upload,Button}from 'element-ui';

Vue.use(Upload);
Vue.use(Button);
export default {
  data() {
    return {
      show:false,
      pageNum:1,
      fileList: [],
      None:false,
        // 总页数
      pageAll: 0,
      // 初始化信息总条数
      dataCount: 0,
      // 每页显示多少条
      pageSize: 10,
      xia: 0, //下一页或者上一页的第一项索引值
      historyData: [],
      showShaoguan: false,
      updataUrl: yuenanUrl + '/ErpYn',
      gd: ''
      
    };
  },
  components: { foot, login },
  computed: {
      ...mapGetters([
    'changeShaoguan'
  ])
   },
    watch:{
    showShaoguan: function(newdata,olddata){

      if(newdata != 'false'){
        this.updataUrl = shaoguanUrl + '/ErpSg'
      }else{
        this.updataUrl = yuenanUrl+'/ErpYn'
      }
    }
  },
  created() {
    this.showShaoguan = this.changeShaoguan;
     if(this.changeShaoguan != 'false'){
        this.updataUrl = shaoguanUrl + '/ErpSg'
      }else{
        this.updataUrl = yuenanUrl+'/ErpYn'
      }
  },
  mounted() {
    this.xuanran(1);
    // layui.use('element', function(){
    //       var element = layui.element
    //     }) 
  },
  beforeDestroy() {

    clearInterval(this.str);
  },
  methods: {
    handlpe(){
      this.show=!this.show;

      // "{background: '#040A53',margin:'200px',height:'200px;',color:'#ffffff'}"
    },
    arraySpanMethod({row, column, rowIndex, columnIndex}) {

    },
    shuangji(){
      this.None=!this.None;
    },
    submitUpload() {
      this.$refs.upload.submit();
      // var usp = new URLSearchParams();
      // usp.append("upload", this.fileList);
      // //console.log( this.$refs.upload.submit())
      // axios.post(yuenanUrl + "/ErpYn/api/UploadFilesGhb", usp).then(res => {
      //   console.log("res", res.data);
      //
      // });
    },
    handleRemove(file, fileList) {
    },
    handlePreview(file) {
    },
    xuanran(page) {
      let params = new URLSearchParams();
      axios.post(this.updataUrl+"/api/getSjgkData",{
        // params:{
        //   pageNum:20,
        //   pageSize:page
        // }
      }).then(res => {
        this.gd = res.data.total
        this.historyData = res.data.data;
        this.pageAll = res.data.pageTotle;
        this.dom = this.$refs.table.bodyWrapper;
        this.dom.addEventListener('scroll', () => {
          let scrollTop = this.dom.scrollTop;
          // 变量windowHeight是可视区的高度
          let windowHeight = this.dom.clientHeight || this.dom.clientHeight;
          // 变量scrollHeight是滚动条的总高度
          let scrollHeight = this.dom.scrollHeight || this.dom.scrollHeight;
          const scrollDistance =this.dom.scrollHeight - this.dom.scrollTop - this.dom.clientHeight;
          params.delete("pageNum")
          if(scrollDistance <=0){//等于0证明已经到底，可以请求接口
            if(this.pageNum < this.pageAll){//当前页数小于总页数就请求
              this.pageNum++;//当前页数自增
              params.append("pageNum",this.pageNum)
              //请求接口的代码
              axios.post(this.updataUrl + "/api/getSjgkData", params).then(res => {

                this.historyData = this.historyData.concat(res.data.data)//将请求回来的数据和当前展示的数据合并在一起
              })

            }
          }
        })
      });
    },
     esc() {
      var editType = 0;
      if(this.changeShaoguan != 'false'){
        editType = 0
      }else{
        editType = 1
      }
      this.$router.push({
        path: '/index',
        query: {
          editType: editType,
        }
      })
    },
    syj() {
      this.$router.push("/index");
    },

    pro() {
      this.$router.push("/personal");
    }
  }
};
</script>
<style scoped>
#bgColor {
  background: transparent;
   margin: 200px auto 0;
  padding: 16px;
  width: 6800px; 
}

.layui-table-body {
  text-align: center;
  background: white;
}

h1,
h2 {
  padding: 10px 0;
}

.layui-row {
  padding: 10px 50px;
  text-align: center;
}

.layui-row p {
  display: inline-block;
}

.ChemicalFindBox {
  /* font-size: 20px; */
  height: 30px;
  padding: 18px 0;
  /* display: none; */
}

.findA1,
.findA2,
.findA4,
.findA3 {
  height: 24px;
  display: inline-block;
  font-size: 14px;
  padding-left: 10px;
}

.ChemicalFind {
  height: 30px;
  display: inline-block;
  border: solid 1px #009688;
}

/* 编辑 */
.chemicalTypeBg {
  /* display: none; */
  background: rgba(158, 158, 158, 0.5);
  width: 100%;
  height: 100%;
  position: fixed;
  top: 0;
  left: 0;
  z-index: 1000;
}

.chemicalTypeBgContent {
  overflow: hidden;
  position: absolute;
  /* padding: 10px 37px; */
  background: white;
  /* width: 310px; */
  /* height: 660px; */
  top: 50%;
  left: 50%;
  transform: translateX(-50%) translateY(-50%);
}

.chemicalTypeBgContent h2 {
  /* width: 100%; */
  height: 40px;
  /* font-size: 26px; */
  line-height: 40px;
  padding-left: 20px;
  background: #f3f3f3;
}

.chemicalTypeBgContent input {
  font-size: 14px;
  width: 150px;
  height: 28px;
  margin: 10px 0;
  padding-left: 10px;
  border-radius: 5px;
  border: solid 1px #b3b3b3;
}

#date1,
#date2 {
  width: 148px;
  height: 28px !important;
  display: inline-block;
  border: solid 1px #b3b3b3;
}

#date3 {
  width: 162px;
  height: 28px !important;
  display: inline-block;
  border: solid 1px #b3b3b3;
}

.TypeBgContent {
  padding: 20px 10px 20px 20px;
}

#submitInt {
  width: 66px;
  float: right;
  /* margin-right: 18px; */
  margin: 10px 24px 10px 0;
  border-radius: 5px;
  /* padding: 10px 0; */
}

#escInt {
  position: absolute;
  top: 10px;
  right: 10px;
  background: transparent;
}

#escInt i {
  color: gray;
}

#dianLanMuYeNo,
#dianLanAfterMuYeNo,
#dianLanBeforeMuYeNo {
  width: 15px;
  vertical-align: -9px;
  /* padding: 0 10px; */
  margin-right: 5px;
}

#colorNo {
  font-size: 14px;
  width: 164px;
  height: 28px;
  margin: 10px 0;
  padding-left: 10px;
  border-radius: 5px;
  border: solid 1px #b3b3b3;
}

.layui-table-page {
  overflow: hidden;
}

.layui-laypage {
  width: 40%;
  float: right;
}

.TableContent {
  width: 615px;
}

.add {
  position: relative;
  top: -45px;
  left: 20px;
}

/* label {
            margin-left: 24px;
        } */
</style>
<style>
.layui-table-cell {
  height: 60px;
  line-height: 60px;
}
.layui-table th {
  font-size: 60px;
  height: 110px;
}
#layui-chemicalType-table1 {
  background: transparent;
  color: white;
}
.layui-table-body .layui-none {
  font-size: 60px;
}
.layui-none {
  margin: 20px auto;
}
.layui-table-header {
  background: transparent;
}
</style>
<style scoped>
* {
  margin: 0;
  padding: 0;
}
li {
  list-style: none;
}
a {
  text-decoration: none;
}

.ChemicalTable{
      margin: 200px auto 0;
    /* width: 1751px; */
}
.ChemicalFindBox{
  height: 60px;
  line-height: 60px;
  color: white;
  font-size: 60px;
  width: 1500px;
  margin: 200px auto 0;
}
.ChemicalFindBox input{
  width: 400px;
  background: #000836;
  height: 80px;
  line-height: 80px;
  color: white;
  font-size: 60px;
}
#ChemicalFind{
  width: 250px;
  height: 80px;
  line-height: 80px;
  border: white 1px solid;
  background: #000836;
  color: white;
}

/* 生产线 */
#lineID {
  width: 100%;
  height: 100%;
  background: transparent;
  color: #00ecfc;
  font-size: 60px;
  line-height: 120px;
}
#lineID > option {
  background: #000836;
}
/* 数据 */
.Administration-box {
  width: 7600px;
  height: 2290px;
  margin: 103px auto 0;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}
.Administration-gkbz,
.Administration-gybz,
.Administration-gcjcbz {
  width: 2500px;
  height: 1040px;
  background: url(..\assets\Administration\gk_bg_1.png);
}
.Administration-myhlbz,
.Administration-myjcbz,
.Administration-gcbz {
  width: 2500px;
  height: 1200px;
  background: url(..\assets\Administration\gk_bg_2.png);
}

/* tab切换 */
.mother-ul {
  display: flex;
  justify-content: center;
  width: 2658px;
  /* height: 278px; */
  margin: 88px auto 78px;
  /* background: url(..\assets\mother\my_nav.png); */
}
.mother-ul li {
  cursor: pointer;
  width: 18%;
  text-align: center;
  font-size: 100px;
  /* line-height: 270px; */
  color: #00ecfc;
}
.mother-ul .active {
  color: #e4c072;
}
/* 管控标准 */
.el-input--suffix .el-input__inner {
  width: 100%;
  height: 100%;
}
.ivu-input-prefix,
.ivu-input-suffix {
  width: 80px;
  line-height: 115px;
  height: 100%;
  text-align: center;
  position: absolute;
  left: 0;
  top: 0;
  z-index: 1;
}

.Admin-gkbz-box {
  display: flex;
  flex-wrap: wrap;
  width: 100%;
}
.Administration-gkbz p {
  padding: 60px 0 0 100px;
  color: white;
  font-size: 94px;
}
.Admin-gkbz-1-1,
.Admin-gkbz-1-2,
.Admin-gkbz-2-1 {
  width: 350px;
  height: 120px;
  color: white;
  /* margin-top: 60px; */
  line-height: 120px;
  font-size: 60px;
  display: flex;
  justify-content: space-between;
}
.Admin-gkbz-1-1 {
  margin-top: 60px;
}
.Admin-gkbz-1-2 {
  margin-top: 60px;
}

.Admin-gkbz-1 {
  margin-left: 100px;
}
.Admin-gkbz-1-1 {
  margin-left: 100px;
}
.Admin-gkbz-1-2 {
  margin-left: 330px;
}
.Admin-gkbz-2-1 {
  margin-left: 100px;
}
/* 向上的距离 */
.adis {
  margin-top: 170px;
}

.Admin-gkbz-2 {
  margin-left: 300px;
}
.Admin-select {
  width: 100%;
  height: 120px;
  background: transparent;
  border: solid 1px white;
  color: white;
  padding-left: 40px;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
  font-size: 60px;
}
.Admin-select option {
  background: #000836;
}
.Admin-gkbz-text-1 {
  width: 600px;
  height: 120px;
  margin-top: 60px;
  margin-left: 50px;
}
.Admin-gkbz-text {
  width: 600px;
  height: 120px;
  margin-top: 170px;
  margin-left: 50px;
}
.Admin-gkbz-text-1 p,
.Admin-gkbz-text p {
  line-height: 120px;
  border: solid 1px white;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0%);
  outline-color: #ec9c45;
  color: #00ecfc;
  padding: 0 40px;
  font-size: 60px;
}
/* .Admin-gkbz-text input::-webkit-input-placeholder {
  color: rgb(199, 199, 199);
  font-size: 60px;
} */
/* 工艺标准 */
.Administration-gybz p {
  padding: 60px 0 0 100px;
  color: white;
  font-size: 94px;
}
.Administration-gybz table {
  border-collapse: collapse;
  border: 1px rgb(0, 0, 0) solid;
  margin: 50px auto 0;
  width: 2300px;
  height: 760px;
}

.Administration-gybz table thead th {
  font-weight: 100;
  height: 158px;
  background: rgba(255, 255, 255, 10%);
}
.Administration-gybz table thead th p {
  padding: 0;
}
.Administration-gybz table thead th p:nth-child(1) {
  /* margin-top: -40px; */
  font-size: 60px;
}
.Administration-gybz table thead th p:nth-child(2) {
  margin-top: -15px;
  font-size: 20px;
}
.Administration-gybz table thead th:nth-child(1) {
  width: 400px;
}
.Administration-gybz table thead th:nth-child(2) {
  width: 390px;
}
.Administration-gybz table thead th:nth-child(3) {
  width: 500px;
}
.Administration-gybz table thead th:nth-child(4) {
  width: 500px;
}
.Administration-gybz table thead th:nth-child(5) {
  width: 500px;
}
.Administration-gybz table tbody tr {
  font-size: 59px;
  color: white;
  height: 200px;
  text-align: center;
  line-height: 200px;
}
.Administration-gybz table tbody td {
  height: 200px;
}
.Administration-gybz table tbody td p {
  /* line-height: none; */
  outline-color: #ec9c45;
  /* outline:solid 1px #ec9c45; */
  width: 100%;
  height: 100%;
  background: rgba(255, 255, 255, 0%);
  border: none;
  text-align: center;
  /* line-height: 100%; */
  color: #00ecfc;
  font-size: 100px;
  padding: 0;
}
.pType {
  line-height: 600px;
}

/* 母液化料标准 */
.Administration-myhlbz p {
  padding: 60px 0 0 100px;
  color: white;
  font-size: 94px;
  margin-bottom: 15px;
  /* margin: 40px 0 45px 40px; */
}
.Administration-myhlbz p span {
  float: right;
  font-size: 60px;
  margin-right: 100px;
}
.Administration-myhlbz-left {
  overflow: hidden;
  box-sizing: border-box;
  padding: 0 20px;
  width: 700px;
  height: 860px;
  background: rgba(255, 255, 255, 10%);
  margin-left: 100px;
  float: left;
}
.Administration-myhlbz-left p {
  text-align: center;
  font-size: 60px;
  padding: 0;
  margin: 30px 0 20px;
}
.Administration-myhlbz-left-inp {
  text-align: center;
  font-size: 100px !important;
  color: #00ecfc !important;
  width: 660px;
  height: 120px;
  border: solid 1px white;
  background: rgba(255, 255, 255, 0%);
  outline-color: #ec9c45;
  line-height: 120px;
}

.Administration-myhlbz-left-table {
  color: white;
  border-collapse: collapse;
  margin-top: 40px;
  width: 660px;
  height: 360px;
  border: white;
  font-size: 54px;
}

.Administration-myhlbz-left-table p {
  color: #00ecfc;
  padding: 0 40px;
  font-size: 60px;
  line-height: 120px;
  /* color: white; */
  width: 100%;
  height: 100%;
  text-align: right;
  background: rgba(0, 0, 0, 0%);
  border: none;
  outline-color: #ec9c45;
  margin: 0;
}
.Administration-myhlbz-left-table tr td:nth-child(1) {
  width: 320px;
  padding-left: 40px;
}
.Administration-myhlbz-left-2 {
  overflow: hidden;
  box-sizing: border-box;
  padding: 0 20px;
  width: 660px;
  height: 800px;
  background: rgba(255, 255, 255, 10%);
  margin-left: 50px;
  float: left;
}
.Administration-myhlbz-left-table-2 {
  color: white;
  border-collapse: collapse;
  margin-top: 40px;
  width: 660px;
  height: 470px;
  border: white;
  font-size: 54px;
}
.Administration-myhlbz-left-table-2 tr {
  height: 100px;
}

.Administration-myhlbz-left-table-2 p {
  color: #00ecfc;
  padding: 0 40px;
  font-size: 60px;
  /* color: wheat; */
  width: 100%;
  height: 100%;
  text-align: right;
  background: rgba(0, 0, 0, 0%);
  border: none;
  outline-color: #ec9c45;
  margin: 0;
  line-height: 100px;
}
.Administration-myhlbz-left-table-2 tr td:nth-child(1) {
  width: 320px;
  padding-left: 40px;
}
/* 母液检测标准 */
.Administration-myjcbz p {
  padding: 60px 0 0 100px;
  color: white;
  font-size: 94px;
  margin-bottom: 15px;
}
.Administration-myjcbz p span {
  float: right;
  font-size: 60px;
  margin-right: 100px;
}
.Administration-myjcbz-left {
  width: 1160px;
  height: 820px;
  float: left;
}
.myjcbz-left-top {
  overflow: hidden;
  width: 1060px;
  height: 440px;
  background: rgba(255, 255, 255, 10%);
  margin-bottom: 10px;
  margin-left: 100px;
}
.myjcbz-left-top-2 {
  margin-top: 40px;
}
.myjcbz-left-top p {
  text-align: center;
  font-size: 60px;
  padding: 0;
  margin: 30px 0 20px;
}
.myjcbz-left-top-inp {
  border: solid 1px white;
  text-align: center;
  width: 1000px;
  height: 120px;
  line-height: 120px;
  font-size: 100px;
  display: block;
  margin: 0 auto 30px !important;
  background: rgba(0, 0, 0, 0%);
  outline-color: #ec9c45;
  padding: 40px;
  color: #00ecfc !important;
}
.nd {
  text-align: center;
  line-height: 120px;
  margin: 0 !important;
  color: #00ecfc !important;
}
.myjcbz-left-top-inp::-webkit-input-placeholder {
  font-size: 40px;
}
.myjcbz-left-top-box {
  /* border: solid 1px red; */
  width: 1000px;
  height: 100px;
  margin: 80px auto;
}
.myjcbz-left-top-box div {
  display: block;
  width: 370px;
  height: 120px;
  font-size: 60px;
  color: white;
  border: solid 1px;
  float: left;
  line-height: 120px;
}
.myjcbz-left-top-box div:nth-child(1) {
  width: 360px;
  padding-left: 40px;
}
.myjcbz-left-top-box div:nth-child(2) {
  width: 640px;
  /* padding-left: 40px; */
}
.myjcbz-left-top-box div input {
  text-align: right;
  width: 100%;
  height: 100%;
  display: block;
  background: rgba(0, 0, 0, 0%);
  border: none;
  outline-color: #ec9c45;
  font-size: 30px;
  color: white;
  padding: 40px;
}
.Administration-myjcbz-right {
  width: 1180px;
  height: 920px;
  background: rgba(255, 255, 255, 10%);
  margin-left: 60px;
  float: left;
}

.myjcbz-right p {
  text-align: center;
  font-size: 60px;
  padding: 0;
  margin: 30px 0 20px;
}
.myjcbz-right-inp {
  border: solid 1px white;
  text-align: center;
  width: 1060px;
  height: 120px;
  font-size: 60px;
  display: block;
  margin: 0 auto 30px !important;
  background: rgba(0, 0, 0, 0%);
  outline-color: #ec9c45;
  /* padding-left: 40px; */
  color: #00ecfc !important;
  line-height: 120px;
}
.myjcbz-left-top-inp::-webkit-input-placeholder {
  font-size: 40px;
}
.myjcbz-right-table {
  border-collapse: collapse;
  border: 1px solid white;
  height: 480px;
  width: 1060px;
  margin: 80px auto;
}
.myjcbz-right-table tr td:nth-child(1) {
  width: 510px;
  height: 120px;
  padding-left: 40px;
  font-size: 60px;
  color: white;
}
.myjcbz-right-table tr td p {
  text-align: right;
  width: 550px;
  height: 120px;
  font-size: 60px;
  line-height: 120px;
  border: none;
  background: rgba(0, 0, 0, 0%);
  outline-color: #ec9c45;
  padding: 0 40px !important;
  color: #00ecfc;
  margin: 0px !important;
}

/* 母液用量标准 */
.Administration-gcbz-p {
  padding: 60px 0 0 100px;
  color: white;
  font-size: 94px;
  margin-bottom: 15px;
  text-align: left;
}

.Administration-gcbz-gm,
.Administration-gcbz-nh,
.Administration-gcbz-yj {
  margin: 20px 0 20px;
  text-align: center;
  color: white;
  font-size: 50px;
}
.gcbz-top-table {
  margin: 0;
  padding: 0;
  width: 2300px;
  height: 300px;
  margin: 0 auto;
  border: solid 1px white;
  border-collapse: collapse;
  text-align: center;
  color: white;
  font-size: 60px;
}
.gcbz-top-table td:nth-child(1) {
  width: 800px;
}
.gcbz-top-table td:nth-child(2) {
  width: 700px;
}
.gcbz-top-table td:nth-child(3) {
  width: 800px;
}
.gcbz-top-table p {
  width: 100%;
  height: 80px;
  text-align: center;
  font-size: 60px;
  border: none;
  background: rgba(0, 0, 0, 0%);
  /* outline-color: #ec9c45; */
  /* padding-left: 40px; */
  color: #00ecfc;
  /* line-height: 120px; */
}
.gcbz-top-table input::-webkit-input-placeholder {
  font-size: 30px;
  line-height: 100%;
}
.gcbz-bottom-l {
  width: 1500px;
  height: 426px;
  /* border: solid 1px; */
  margin-left: 100px;
  float: left;
}
.gcbz-bottom-table {
  width: 1500px;
  height: 300px;
  text-align: center;
  font-size: 60px;
  color: white;
  border: solid 1px white;
  border-collapse: collapse;
}
.gcbz-bottom-table td:nth-child(1) {
  width: 800px;
}
.gcbz-bottom-table p {
  /* width: 100%; */
  /* height: 100%; */
  text-align: center;
  font-size: 60px;
  /* border: none; */
  background: rgba(0, 0, 0, 0%);
  /* outline-color: #ec9c45; */
  /* padding-left: 40px; */
  color: #00ecfc;
}
.gcbz-bottom-table input::-webkit-input-placeholder {
  font-size: 30px;
  line-height: 100%;
}
.gcbz-bottom-r {
  width: 700px;
  float: left;
  margin-left: 100px;
  /* border: solid 1px; */
}
.gcbz-bottom-r p:nth-child(2) {
  width: 700px;
  height: 120px;
  text-align: center;
  font-size: 60px;
  border: solid 1px white;
  background: rgba(0, 0, 0, 0%);
  outline-color: #ec9c45;
  padding-left: 40px;
  color: #00ecfc;
  line-height: 120px;
}
.Administration-gcbz-submit {
  cursor: pointer;
  width: 600px;
  height: 160px;
  margin: 50px auto 0;
  background: url(..\assets\Administration\button.png);
}
.Administration-gcbz-submit p {
  text-align: center;
  font-size: 80px;
  color: white;
  line-height: 160px;
}

/* 头部 */
.Administration {
  position: relative;
  width: 7680px;
  height: 3240px;
  background: url(..\assets\Administration\other_bg.png);
}
.index-top_nav {
  overflow: hidden;
  width: 3358px;
  height: 292px;
  margin: 0 auto;
  background: url(../assets/index/top_nav.png);
}
/* .index-top_nav img {
  display: block;
  margin: 45px auto;
  width: 1052px;
  height: 168px;
} */
/* 返回首页 */
.index-esc {
  position: absolute;
  top: 100px;
  left: 640px;
  width: 1000px;
  height: 100px;
}
.index-esc img {
  padding-right: 40px;
  width: 140px;
  height: 100px;
  vertical-align: -20px;
}
.index-esc span {
  padding: 0 100px;
  color: #00ecfc;
  font-size: 80px;
  line-height: 100px;
}
/* 退出登陆 */
.index-name_esc {
  position: absolute;
  top: 100px;
  right: 400px;
  width: 1000px;
  height: 100px;
}
.index-name_esc img {
  padding-right: 40px;
  width: 140px;
  height: 100px;
  vertical-align: -20px;
}
.index-name_esc span {
  padding: 0 100px;
  color: #00ecfc;
  font-size: 80px;
  line-height: 100px;
}
/*  */
/*  */
/*  */
/*  */
</style>
<style>
.ivu-input {
  font-size: 60px;
  background: transparent;
  height: 120px !important;
  color: white !important;
}
.ivu-date-picker-focused input,
.ivu-input-with-suffix {
  background: transparent;
}
.ivu-input-with-suffix {
  background: transparent !important;
}
.ivu-input-prefix,
.ivu-input-suffix {
  width: 80px;
  line-height: 115px;
}
.ivu-input-with-suffix {
  background: transparent;
}
.ivu-input-wrapper {
  border: solid 1px white;
  outline-color: #ec9c45 !important;
}
.ivu-date-picker-focused input {
  font-size: 60px;
  color: #00ecfc;
  padding-left: 40px;
}
.ivu-input-with-suffix {
  font-size: 60px;
  color: #00ecfc !important;
  padding-left: 40px;
}
.ivu-input-prefix i,
.ivu-input-suffix i {
  font-size: 60px;
}
.el-dropdown {
  border: solid 1px white;
  display: inline-block;
  position: relative;
  color: #606266;
  font-size: 40px;
  width: 400px;
  height: 120px;
  line-height: 120px;
}
.el-dropdown span {
  color: white;
  width: 100%;
}
.el-dropdown-link .el-dropdown-selfdefine {
  color: white;
  width: 100px;
}
.el-dropdown-menu__item {
  padding-left: 40px;
  width: 400px;
  height: 40px;
  font-size: 30px;
}
.el-dropdown-menu__item i {
  display: none;
}
.index-esc{
    position: absolute;
    top: 100px;
    left: 640px;
    width: 1060px;
    height: 100px;
}
#building-top .el-table__empty-block{
  background: #01AAED;
}
#building-top .el-table__empty-text{
  color:#c00050;
}
#building-top .is-group {
  background: #01AAED;
}
.el-table__body tr:hover>td {
  background-color: #134087 !important;
}
.cell{
  padding: 20px !important;
}
</style>


