# el-input-
el-input输入框限制数字，中文，英文，等多种
​
1.只能输入数字



        <el-input
          v-model="rowForm.carriage"
          clearable
          size="small"
          style="width: 90px"
          @input="value => rowForm.carriage= Number(value.replace(/[^\d]/g,''))"
        />
  

2.输入数字和小数点


 @input="rowForm.carriage= rowForm.carriage.replace(/[^\d|\.]/g, '')"
3.只能输入数字和保留2位小数点


 oninput="value= value.match(/\d+(\.\d{0,2})?/) ? value.match(/\d+(\.\d{0,2})?/)[0] : ''" 

4.只能输入数字和英文
onkeyup="value=value.replace(/[^\d|chun]/g,'')"
5.只能输入中文、数字、英文，不包含符号
<el-input onkeyup="value=value.replace(/[^\w\u4E00-\u9FA5]/g, '')">
6.只能输入英文，数字，不能输入中文
onkeyup="value=value.replace(/[^\w\.\/]/ig,'')"
7.只能输入中文，其他都不可输入
  <el-input v-model="rowForm.carriage" clearable @input="handleInput"/>
  handleInput() {
      const regex = /^[\u4e00-\u9fa5]+$/; // 中文字符的正则表达式
      if (!regex.test(this.rowForm.carriage)) {
        this.rowForm.carriage = '';
      }
    },

或者


8.只能英文，其他不可 
<el-input type="text" onkeyup="this.value=this.value.replace(/[^a-zA-Z]/g,'')">


​
