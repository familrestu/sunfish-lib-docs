### 📌 Component: WPForm

#### Overview

- **Name**: `WPForm`
- **Description**: A component for every form creation, must use this WPForm component for create a form, so all form will have the same result or layout.
- **Import path**: `import WPForm from 'lib/components/wp-form'`

#### Props

| Prop Name | Type | Default | Required | Description |
| ---- | ---- | ---- | ---- | ---- |
| `accesscode` | `string` | — | ❌ | Access code to check if user authorize to view this page or not |
| `datasource` | `string` | — | ❌ | API for fetch default data to fill form automatically |
| `formAction` | `string` | — | ❌ | Set API for submit data |
| `deleteAction` | `string` | — | ❌ | Set API for delete data |
| `customFetchResult` | `(data:Record<string, any>, response: any )=>Record<string, any>[]` | — | ❌ | Customize result after succedeed fetch data |
| `beforeSubmit` | `(data:Record<string, any>, response: any )=>Record<string, any>` | — | ❌ | Reconstruction data payload before sent to backend service |
| `isWorkFlow` | `boolean` | — | ❌ | Turn form into form request |
| `keyData` | `Record<string,any>` | — | ❌ | Set paylaoad when fetch and sent data to be. Would wrap data inside of `KEY`, word. this props will be required when datasource is specified |
| `reqData` | `Record<string,any>` | — | ❌ | Set paylaoad when fetch data only and doesn't wrap with any key |
| `onModalResultOk` | `(resultType: 'error, warning, success, confirm' )=>void` | — | ❌ | Event after success submit |
| `onModalResultDeleteOk` | `(resultType: 'error, warning, success, confirm' )=>void` | — | ❌ | Event after success delete data, it will active if `datasource` is filled |
| `onSuccessCallback` | `(res: Record<string, any>, successMsg: string, formAction: string )=>void` | Showing notification success | ❌ | Override default function of success after submit form |
| `onErrorCallback` | `(err: Error, errMsg: string, formAction: string )=>void` | Showing notification error | ❌ | Override default function of error after submit form |
| `showButton` | `boolean` | `true` | ❌ | Show/hide all button form, except `extraButton` |
| `customPayload` | `Record<string, any>` | `{}` | ❌ | Append additional payload and wrapped inside of `ENTRIES` key if `isWrapPayloadWithEntries` is `true` |
| `isWrapPayloadWithEntries` | `boolean` | `true` | ❌ | Wrapping payload inside of `ENTRIES` key|
| `disableCancelButtonIf`| `boolean` | `false`| ❌ | Control disable of cancel button|
| `disableDeleteButtonIf`| `boolean` | `false`| ❌ | Control disable of delete button|
| `disableDraftButtonIf` | `boolean` | `false`| ❌ | Control disable of delete button|
| `disableSubmitButtonIf`| `boolean` | `false`| ❌ | Control disable of submit button|
| `disablePreviewApproverButtonIf` | `boolean` | `false`| ❌ | Control disable of preview approver button|
| `apiType`| `lc, go, py-go, hrm-go` | `lc` | ❌ | Set type of api when submit, delete nd fetch data of form |
| `isLoadingSelf`| `boolean` | `false`| ❌ | Control loading of form manually|
| `letterProps`| [Letter Props](#letter-props) | `{}` | ❌ | Set props for supporting form letter|

#### Letter Props

| Prop Name| Type| Default| Required | Description|
| ---- | ---- | ---- | ---- | ---- |
| `letterContentProps` | `string`| `letter_content` | ✅ | Name field of `letter content` value |
| `letterNoProps`| `string`| `letter_no`| ✅ | Name field of `letter no` value|
| `emailToProps` | `string`| `email`| ❌ | Name field of `email` value|
| `headerName` | `string`| -| ❌ | Name field of `header` value |
| `footerName` | `string`| -| ❌ | Name field of `footer` value |
| `sendEmailAction`| `string`| -| ❌ | Set api when send email|
| `customPayloadList`| `string,string` | -| ❌ | Get custom payload by name setted in customPayloadList |
| `protectLetterIf`| `boolean` | false| ❌ | Protect field letter by making the field is readOnly |
| `isDigitalSignature` | `boolean` | false| ❌ | Turn wpform for support digital signature|

---

#### Usage

Creaiting Regular Form

```jsx
/* file src/pages/hrm/test-page/components/wp-form/TestWPForm.js */
import WPForm from 'lib/components/wp-form';
import WPControl from 'lib/components/wp-form/wp-control';

const FormPage = (props) => {
  return (
    <WPForm
      accesscode="some-accesscode"
      datasource="datasource-api"
      formAction="submit-api"
      deleteAction="delete-api"
    >
      <WPControl type="text" name="field1" label="Field1" />
    </WPForm>
  );
};

export default FormPage;
```

---

Creating Form Request

```jsx
/* file src/pages/hrm/test-page/components/wp-form/TestWPForm.js */
import WPForm from 'lib/components/wp-form';
import WPControl from 'lib/components/wp-form/wp-control';

const FormPage = (props) => {
  return (
    <WPForm
      isWorkflow
      accesscode="some-accesscode"
      datasource="datasource-api"
      formAction="submit-api"
      deleteAction="delete-api"
      keyData={{
        emp_id: 'emp_id'
      }}
    >
      <WPControl type="text" name="field1" label="Field1" />
    </WPForm>
  );
};

export default FormPage;
```

---

Updating form fetch result from datasource and updating payload before submit form to back-end

```jsx
/* file src/pages/hrm/test-page/components/wp-form/TestWPForm.js */
import WPForm from 'lib/components/wp-form';
import WPControl from 'lib/components/wp-form/wp-control';

const FormPage = (props) => {
  return (
    <WPForm
      accesscode="some-accesscode"
      datasource="datasource-api"
      formAction="submit-api"
      deleteAction="delete-api"
      customFetchResult={(formData) => {
        formData.original_first_name = formData?.first_name;
        formData.original_middle_name = formData?.middle_name;
        formData.original_last_name = formData?.last_name;
        
        return formData
      }}
      beforeSubmit={(formData) => {
        if(formData?.first_name) formData.first_name = formData?.original_first_name
        if(formData?.middle_name) formData.middle_name = formData?.original_middle_name
        if(formData?.last_name) formData.last_name = formData?.original_last_name
        
        return formData
      }}
    >
      <WPControl type="text" name="emp_no" label="Employee No" />
      <WPControl type="text" name="first_name" label="First Name" />
      <WPControl type="text" name="middle_name" label="Middle Name" />
      <WPControl type="text" name="last_name" label="Last Name" />

      <WPControl type="text" name="emp_id" hidden />
      <WPControl type="text" name="original_first_name" hidden />
      <WPControl type="text" name="original_middle_name" hidden />
      <WPControl type="text" name="original_last_name" hidden />
    </WPForm>
  );
};

export default FormPage;
```

#### Frequently Asked Question

- Q: how do I set value in Form?
- A: for initial values of Form, you can you inside `initialValues` props in `WPForm`. eg:

```jsx
const Example = () => {
  /* ... your other code ... */
  return (
    <WPForm initialValues={
      emp_no: "XXXX"
    }>
      {/* your code  */}
      <WPControl name="emp_no" type="text" />
    </WPForm>
  )
}
```

- Q: how do I set value if the control field is dynamically rendered based on some value
- A: we can use props `initialValue` from `Form.Item` components. eg:

```jsx
const Example = () => {
  /* ... your other code ... */

  const arrData = [{
    emp_no_1: "XXX_1",
    name_1: "NAME_1",
    join_1: "2025-05-05",
    end_1: null
  }, {
    emp_no_2: "XXX_2",
    name_2: "NAME_2",
    join_2: "2025-05-05",
    end_2: "2025-10-06"
  }]

  return (
    <WPForm>
      {
        arrData.map((item, index) => {
          return (
            <Row key={item[`emp_no_${index + 1}`]}>
              <Col span={24}>
                <WPControl type="text" name={`emp_no_${index + 1}`} formItemObj={{ initialValue: item[`emp_no_${index + 1}`] }} />
                <WPControl type="text" name={`name_${index + 1}`} formItemObj={{ initialValue: item[`name_${index + 1}`] }} />
                <WPControl type="text" name={`join_${index + 1}`} formItemObj={{ initialValue: item[`join_${index + 1}`] ? moment(item[`join_${index + 1}`]) : null }} />
                <WPControl type="text" name={`end_${index + 1}`} formItemObj={{ initialValue: item[`end_${index + 1}`] ? moment(item[`end_${index + 1}`]) : null }} />
              </Col>
            </Row>
          )
        })
      }
    </WPForm>
  )
}
```

- Q: how do we set value when we click another field? or when we fetch something to backend and set the response base on it
- A: we can use `Form.Instance`, eg:

```jsx
const Example = () => [
  const [form] = Form.useForm();

  const fetchSomething = () => {
    form.setFieldsValue({
      emp_no: "XXX",
      emp_name: "XXX"
    })
  }

  return (
    <WPForm form={form}>
      <WPControl type="text" name="emp_no" label="emp_no" />
      <WPControl type="text" name="emp_name" label="emp_name" />
      <WPControl type="select" name="gender" label="gender" listOptions={[{ value: 0, label: 'Female' }, { value: 1, label: 'Male' }]} onChange={(value) => {        
        form.setFieldsValue({ emp_name: `${value === 0 ? 'Mrs' : 'Mr'} ${form.getFieldValue(emp_name)}` })
      }} />
    </WPForm>
  )
]
```



- Q: why our page become error when set field of date?
- A: make sure to format your date into `moment` format data 
