## 📌 Component: WPComponent

### Overview

- **Name**: `WPCcontrol`
- **Description**: Standard Form Control component
- **Import path**: `lib/components/wp-form/wp-control`
- **Origin Components**: antd control inputs

### Props WPControl

childrens of WPComponent
| Prop Name | Type | Default | Required | Description |
|-----------|------|---------|----------|-------------|
| `label` | `string` | — | ❌ | control label, this `label` props in Form.Item |
| `name` | `string` | — | ✅ | field name, this `name` props in Form.Item |
| `type` | `checkboxgroup`, `checkbox-group`, `select`, `transfer`, `checkbox`, `requestfor`, `text`, `textarea`, `texteditor`, `texteditor_sun`, `date`, `daterange`, `time-picker`, `datetime-picker`, `datetimerange-picker`, `input-multilang`, `number-currency`, `number-withcurrency`, `upload`, `rate`, `label`, `number`, `filter-employee`, `radio`, `markdown-editor` | — | ✅ | type of wpcontrol |
| `formItemObj` | [Form Item Object](https://4x.ant.design/components/form/#Form.Item) | — | ❌ | Form field component for data bidirectional binding, validation, layout, and so on |

### Usage

```jsx
/* file pages/test/test-control/WPControlTest */
import WPForm from "lib/components/wp-form";
import WPControl from "lib/components/wp-form/wp-control";

const App = () => {
  return (
    <WPForm>
      <WPControl type="text" name="firstname" label="First Name" />
    </WPForm>
  );
};
```

### WPTransfer

All props can be used for create transfer field

| Prop Name             | Type                                                                | Default | Required | Description                                                             |
| --------------------- | ------------------------------------------------------------------- | ------- | -------- | ----------------------------------------------------------------------- |
| `datasource`          | `string`                                                            | —       | ❌       | API for fetching data and set to list data                              |
| `customPayload`       | `Record<string, any>`                                               | —       | ❌       | Payload for fetching data with `datasource`                             |
| `customFetchResult`   | `(data:Record<string, any>, response: any )=>Record<string, any>[]` | —       | ❌       | Customize result after succedeed fetch data                             |
| `listOptions`         | `Record<string,any>[]`                                              | —       | ❌       | Set list data manually or by doing fetch manually                       |
| `selectValue`         | `string`                                                            | —       | ❌       | Custom key selected after fetch data for sending value to backend side  |
| `selectLabel`         | `string`                                                            | —       | ❌       | Custom key selected after fetch data for showing data in transfer field |
| `isLoading`           | `boolean`                                                           | `false` | ❌       | Controlling loading state                                               |
| `isDisabled`          | `boolean`                                                           | `false` | ❌       | Controlling disabled state                                              |
| `showAllSelect`       | `boolean`                                                           | `false` | ❌       | If its `true`, it will show checkbox for auto checked all data          |
| `autoSelect`          | `boolean`                                                           | `false` | ❌       | Auto select data without click transfer button                          |
| `reqPayload`          | `Record<string,any>`                                                | —       | ❌       | Overwrite all of default payload                                        |
| `apiVersion`          | `v${number}`                                                        | `v1`    | ❌       | Versioning api, used by api go                                          |
| `apiType`             | `lc, go, py-go, hrm-go`                                             | `lc`    | ❌       | Type of api used                                                        |
| `customRender`        | `(record: Record<string, any>) => ReactElement[] , ReactElement`    | —       | ❌       | Versioning api, used by api go                                          |
| `isResetWhenCheckAll` | `boolean`                                                           | `false` | ❌       | Auto reset all item when check all is checked                           |

### Usage

```jsx
/* file pages/test/test-control/WPControlTest */
import WPForm from "lib/components/wp-form";
import WPControl from "lib/components/wp-form/wp-control";

const App = () => {
  return (
    <WPForm>
      <WPControl
        type="transfer"
        name="firstname"
        label="First Name"
        datasource="SomeApi"
      />
    </WPForm>
  );
};
```
