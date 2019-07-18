## React 组件化
```
import React, { Component } from "react";
class MyTextArea extends Component {
  constructor(props) {
    super(props);
  }
  static state = {flag:false};
  handleSubmit = (event, buttonTag) => {
    event.preventDefault();
    buttonTag === "0" && this.props.showModal();
    this.props.form.validateFields((err, values) => {
      if (!err) {
        console.log('Received values of form: ', values);
      }
    });
  }

  render() {
    const { getFieldDecorator } = this.props.form;
    return <Form layout="horizontal" onSubmit={this.handleSubmit}>
      <Row>
        <Row style={{ background: '#e2e5e9', marginBottom: "10px" }}><h3>审批意见</h3></Row>
        <Form.Item style={{ marginBottom: '0px' }}>
          {getFieldDecorator('message', {
            rules: [{ required: false, message: 'Please input your Password!' }],
          })(<TextArea rows={4} />)}
        </Form.Item>
        <Form.Item>
          <Button type="primary" onClick={event => this.handleSubmit(event, "1")}>审核通过</Button>
          <Button type="primary" style={{ marginLeft: '20px' }} onClick={event => this.handleSubmit(event, "0")}>审核不通过</Button>
        </Form.Item>
      </Row>
    </Form>
  }
}
```