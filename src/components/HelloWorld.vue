<template>
  <div class="hello">
    <form id="form1">
      <table border="1" width="300" id="tb01" bgcolor="#CCFFCC" style="border:solid 1px black;border-collapse:collapse">
        <tr><td width="133" id="mtb001">
        <font face="黑体" color="#FF0000" size="3"><u>&nbsp;《表单一》&nbsp;</u></font></td></tr>
      </table>
      
      <table border="1" width="300" height="106" cellspacing="0" bgcolor="#CCFFFF" style="border-collapse:collapse;table-layout:fixed;border:solid 1px black;">
        <tr>
          <td width="66" height="16" style="border:solid 1px black"><font color="#0000FF">A</font><font color="#0000FF">等</font></td>
          <td width="51" height="16" style="border:solid 1px black"><font color="#0000FF">B</font><font color="#0000FF">等</font></td>
          <td width="51" height="16" style="border:solid 1px black"><font color="#0000FF">C</font><font color="#0000FF">等</font></td>
        </tr> 
        <tr>
          <td width="66" height="16" style="border:solid 1px black">A<sub>01</sub></td>
          <td width="80" height="12" style="border:solid 1px black">中-001</td>
          <td width="51" height="12" style="border:solid 1px black">C1<sup>x</sup></td>
        </tr> 
        <tr>
          <td width="66" height="16" style="border:solid 1px black">A<sub>02</sub>Φ</td>
          <td width="80" height="16" style="border:solid 1px black">日-スの</td>
          <td width="51" height="16" style="border:solid 1px black"><font face='Vernada'>7</font></td>
        </tr> 
        <tr>
          <td width="66" height="16" style="border:solid 1px black;overflow:hidden">A<sub>03</sub><nobr>over隐藏后面的：1234567890</nobr></td>
          <td width="80" height="16" style="border:solid 1px black;overflow:hidden">韩-안녕</td><td width="51" height="16">C3<sup>x</sup></td>
        </tr> 
      </table>
    </form>
    <p>
      1：若只打印《表单一》,看一下<a @click="prn1_preview()">打印预览</a>,可<a @click="prn1_print()">直接打印</a>也可      
      <a @click="prn1_printA()">选择打印机</a>打印。<br><br>
    </p>  
  </div>
</template>

<script>
import { getLodop } from '../assets/LodopFuncs' //导入模块

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      // 总条数
      LODOP: undefined
    }
  },
  methods: {
    btnClickPrint () {
        this.LODOP = getLodop()//调用getLodop获取LODOP对象
        this.LODOP.PRINT_INIT("")
        this.LODOP.ADD_PRINT_TEXT(50, 231, 260, 39, "打印内容")
        this.LODOP.PREVIEW()
    },
    CreateOneFormPage(){
      this.LODOP=getLodop();  
      this.LODOP.PRINT_INIT("打印控件功能演示_Lodop功能_表单一");
      this.LODOP.SET_PRINT_STYLE("FontSize",18);
      this.LODOP.SET_PRINT_STYLE("Bold",1);
      this.LODOP.ADD_PRINT_TEXT(50,231,260,39,"打印页面部分内容");
      this.LODOP.ADD_PRINT_HTM(88,200,350,600,document.getElementById("form1").innerHTML);
    },
    prn1_preview() {	
      this.CreateOneFormPage();	
      this.LODOP.PREVIEW();	
    },
    prn1_print() {		
      this.CreateOneFormPage();
      this.LODOP.PRINT();	
    },
    prn1_printA() {		
      this.CreateOneFormPage();
      this.LODOP.PRINTA(); 	
    }
  }  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
