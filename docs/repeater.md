# 基本

- layout: default
- order: 0

最简单的用法。

---

## 可执行 DEMO

````js
import Form, { FormItem, Item } from '../src';
import createRepeater  from '../src/repeater';
import * as Antd from 'antd';
import wrapper from '../src/wrapper/antd';
import dialogWrapper from '../src/dialog/antd';
// import '../src/repeater/index.scss';
// import "antd/dist/antd.css";
import "./repeater.scss";

const {Modal, Button, Input}  = wrapper(Antd);
const Dialog = dialogWrapper(Antd)
const { TableRepeater } = createRepeater({ Dialog, Button, Input });
// 自定义的过滤函数
function filter(value, key){
    return value.filter(item => item.drawerName.startsWith(key))
}

ReactDOM.render(<Form onChange={console.log}>
    <Item name="repeat">
        <TableRepeater filter={filter} dialog={Dialog}>
            <FormItem label="开票人" name="drawerName"><Input /></FormItem>
            <FormItem label="税号" name="taxpayerNumber"><Input /></FormItem>
            <FormItem label="子公司" name="branchName"><Input /></FormItem>
            <FormItem label="核查结果" name="checkResultName"><Input /></FormItem>
            <FormItem label="拒绝原因" name="denyReason"><Input /></FormItem>
            <FormItem label="创建人" name="creatorName"><Input /></FormItem>
        </TableRepeater>
    </Item>
</Form>, mountNode);
````

````css
body {
    background-color: #FFF;
}
````