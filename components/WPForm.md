### 📌 Component: WPForm

#### Overview

- **Name**: `WPForm`
- **Description**: A component for every form creation, must use this WPForm component for create a form, so all form will have the same result or layout.
- **Import path**: `import WPForm from 'lib/components/wp-form'`

#### Props

| Prop Name                        | Type                                                                        | Default                      | Required | Description                                                                                           |
| -------------------------------- | --------------------------------------------------------------------------- | ---------------------------- | -------- | ----------------------------------------------------------------------------------------------------- |
| `accesscode`                     | `string`                                                                    | —                            | ❌       | Access code to check if user authorize to view this page or not                                       |
| `datasource`                     | `string`                                                                    | —                            | ❌       | API for fetch default data to fill form automatically                                                 |
| `customFetchResult`              | `(data:Record<string, any>, response: any )=>Record<string, any>[]`         | —                            | ❌       | Customize result after succedeed fetch data                                                           |
| `formAction`                     | `string`                                                                    | -                            | ❌       | Set API for submit data                                                                               |
| `deleteAction`                   | `string`                                                                    | -                            | ❌       | Set API for delete data                                                                               |
| `beforeSubmit`                   | `(data:Record<string, any>, response: any )=>Record<string, any>`           | —                            | ❌       | Reconstruction data payload before sent to backend service                                            |
| `isWorkFlow`                     | `boolean`                                                                   | —                            | ❌       | Turn form into form request                                                                           |
| `keyData`                        | `Record<string,any>`                                                        | —                            | ❌       | Set paylaoad when fetch and sent data to be. Would wrap data inside of `KEY` word                     |
| `reqData`                        | `Record<string,any>`                                                        | —                            | ❌       | Set paylaoad when fetch data only and doesn't wrap with any key                                       |
| `onModalResultOk`                | `(resultType: 'error, warning, success, confirm' )=>void`                   | —                            | ❌       | Event after success submit                                                                            |
| `onModalResultDeleteOk`          | `(resultType: 'error, warning, success, confirm' )=>void`                   | —                            | ❌       | Event after success delete data, it will active if `datasource` is filled                             |
| `onSuccessCallback`              | `(res: Record<string, any>, successMsg: string, formAction: string )=>void` | Showing notification success | ❌       | Override default function of success after submit form                                                |
| `onErrorCallback`                | `(err: Error, errMsg: string, formAction: string )=>void`                   | Showing notification error   | ❌       | Override default function of error after submit form                                                  |
| `showButton`                     | `boolean`                                                                   | `true`                       | ❌       | Show/hide all button form, except `extraButton`                                                       |
| `customPayload`                  | `Record<string, any>`                                                       | `{}`                         | ❌       | Append additional payload and wrapped inside of `ENTRIES` key if `isWrapPayloadWithEntries` is `true` |
| `isWrapPayloadWithEntries`       | `boolean`                                                                   | `true`                       | ❌       | Wrapping payload inside of `ENTRIES` key                                                              |
| `disableCancelButtonIf`          | `boolean`                                                                   | `false`                      | ❌       | Control disable of cancel button                                                                      |
| `disableDeleteButtonIf`          | `boolean`                                                                   | `false`                      | ❌       | Control disable of delete button                                                                      |
| `disableDraftButtonIf`           | `boolean`                                                                   | `false`                      | ❌       | Control disable of delete button                                                                      |
| `disableSubmitButtonIf`          | `boolean`                                                                   | `false`                      | ❌       | Control disable of submit button                                                                      |
| `disablePreviewApproverButtonIf` | `boolean`                                                                   | `false`                      | ❌       | Control disable of preview approver button                                                            |
| `apiType`                        | `lc, go, py-go, hrm-go`                                                     | `lc`                         | ❌       | Set type of api when submit, delete nd fetch data of form                                             |
| `isLoadingSelf`                  | `boolean`                                                                   | `false`                      | ❌       | Control loading of form manually                                                                      |
| `letterProps`                    | [Letter Props](#letter-props)                                               | `{}`                         | ❌       | Set props for supporting form letter                                                                  |

#### Letter Props

| Prop Name            | Type            | Default          | Required | Description                                            |
| -------------------- | --------------- | ---------------- | -------- | ------------------------------------------------------ |
| `letterContentProps` | `string`        | `letter_content` | ✅       | Name field of `letter content` value                   |
| `letterNoProps`      | `string`        | `letter_no`      | ✅       | Name field of `letter no` value                        |
| `emailToProps`       | `string`        | `email`          | ❌       | Name field of `email` value                            |
| `headerName`         | `string`        | -                | ❌       | Name field of `header` value                           |
| `footerName`         | `string`        | -                | ❌       | Name field of `footer` value                           |
| `sendEmailAction`    | `string`        | -                | ❌       | Set api when send email                                |
| `customPayloadList`  | `string,string` | -                | ❌       | Get custom payload by name setted in customPayloadList |
| `protectLetterIf`    | `boolean`       | false            | ❌       | Protect field letter by making the field is readOnly   |
| `isDigitalSignature` | `boolean`       | false            | ❌       | Turn wpform for support digital signature              |

#### Usage

###### Regular Form

```jsx
/* file src/pages/hrm/test-page/components/wp-form/TestWPForm.js */
import WPForm from "lib/components/wp-form";
import WPControl from "lib/components/wp-form/wp-control";

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

###### Form Request

```jsx
/* file src/pages/hrm/test-page/components/wp-form/TestWPForm.js */
import WPForm from "lib/components/wp-form";
import WPControl from "lib/components/wp-form/wp-control";

const FormPage = (props) => {
  return (
    <WPForm
      isWorkflow
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
