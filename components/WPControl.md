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
| `required` | `boolean` | — | ❌ | controlling required state of field, if no `props.rules` provided, message will be appended from label. eg: label = Employee, then required message will be `Employee is Required` |
| `disabled` | `boolean` | — | ❌ | controlling disabled state of field |
| `rules` | `{ [key: string]: any }[]` | — | ❌ | controlling extended rules of field |
| `type` | `checkboxgroup`, `checkbox-group`, `select`, `transfer`, `checkbox`, `requestfor`, `text`, `textarea`, `texteditor`, `texteditor_sun`, `date`, `daterange`, `time-picker`, `datetime-picker`, `datetimerange-picker`, `input-multilang`, `number-currency`, `number-withcurrency`, `upload`, `rate`, `label`, `number`, `filter-employee`, `radio`, `markdown-editor` | — | ✅ | list of available control |
| `formItemObj` | [Form Item Object](https://4x.ant.design/components/form/#Form.Item) | — | ❌ | Form field component for data bidirectional binding, validation, layout, and so on |

### Usage

```jsx
/* file pages/test/test-control/WPControlTest */
import WPForm from "lib/components/wp-form";
import WPControl from "lib/components/wp-form/wp-control";

const WPControlTest = () => {
  return (
    <WPForm>
      <WPControl type="text" name="firstname" label="First Name" />
    </WPForm>
  );
};

export default WPControlTest;
```

---

### List usage for each WPControl Types

#### WPInput

All props can be used for create text input field

| Prop Name | Type| Default | Required | Description|
| --- | --- | --- | --- | --- |
| `hidden`| `boolean` | `false` | ❌ | controlling to show field |

#### Usage

```jsx
/* file pages/test/test-control/WPControlTest */
import WPForm from "lib/components/wp-form";
import WPControl from "lib/components/wp-form/wp-control";

const App = () => {
  return (
    <WPForm>
      <WPControl
        type="checkbox"
        name="firstname"
        label="text"
      />
    </WPForm>
  );
};
```

---

#### WPTextArea

All props can be used for create text input field

| Prop Name | Type| Default | Required | Description|
| --- | --- | --- | --- | --- |
| `rows`| `number` | `5` | ❌ | controlling how many rows in text area |
| `maxLength`| `number` | — | ❌ | maximum length of character can be typed |
| `showCount`| `number` | — | ❌ | showing total of `maximumLength` and total character typed |

#### Usage

```jsx
/* file pages/test/test-control/WPControlTest */
import WPForm from "lib/components/wp-form";
import WPControl from "lib/components/wp-form/wp-control";

const App = () => {
  return (
    <WPForm>
      <WPControl
        type="checkbox"
        name="firstname"
        label="text"
      />
    </WPForm>
  );
};
```

---

#### WPTransfer

All props can be used for create transfer field

| Prop Name | Type| Default | Required | Description |
| --- | --- | --- | --- | --- |
| `datasource`| `string`| — | ❌ | API for fetching data and set to list data|
| `customPayload` | `Record<string, any>` | — | ❌ | Payload for fetching data with `datasource` |
| `customFetchResult` | `(data:Record<string, any>, response: any )=>Record<string, any>[]` | — | ❌ | Customize result after succedeed fetch data |
| `listOptions` | `Record<string,any>[]`| — | ❌ | Set list data manually or by doing fetch manually |
| `selectValue` | `string`| — | ❌ | Custom key selected after fetch data for sending value to backend side|
| `selectLabel` | `string`| — | ❌ | Custom key selected after fetch data for showing data in transfer field |
| `isLoading` | `boolean` | `false` | ❌ | controlling loading state |
| `isDisabled`| `boolean` | `false` | ❌ | controlling disabled state|
| `showAllSelect` | `boolean` | `false` | ❌ | If its `true`, it will show checkbox for auto checked all data|
| `autoSelect`| `boolean` | `false` | ❌ | Auto select data without click transfer button|
| `reqPayload`| `Record<string,any>`| — | ❌ | Overwrite all of default payload|
| `apiVersion`| `v${number}`| `v1`| ❌ | Versioning api, used by api go|
| `apiType` | `lc, go, py-go, hrm-go` | `lc`| ❌ | Type of api used|
| `customRender`| `(record: Record<string, any>) => ReactElement[] , ReactElement`| — | ❌ | Custom how data appear in list|
| `isResetWhenCheckAll` | `boolean` | `false` | ❌ | Auto reset all item when check all is checked |

#### Usage

```jsx
/* file pages/test/test-control/WPControlTest */
import WPForm from "lib/components/wp-form";
import WPControl from "lib/components/wp-form/wp-control";

const WPControlTest = () => {
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

export default WPControlTest;
```

---

#### WPSelect

All props can be used for create select field

| Prop Name | Type| Default | Required | Description|
| --- | --- | --- | --- | --- |
| `datasource`| `string`| — | ❌ | API for fetching data and set to list data |
| `customPayload` | `Record<string, any>` | — | ❌ | Payload for fetching data with `datasource`|
| `customFetchResult` | `(data:Record<string, any>, response: any )=>Record<string, any>[]` | — | ❌ | Customize result after succedeed fetch data|
| `listOptions` | `Record<string,any>[]`| — | ❌ | Set list data manually or by doing fetch manually|
| `selectValue` | `string`| — | ❌ | Custom key selected after fetch data for sending value to backend side |
| `selectLabel` | `string`| — | ❌ | Custom key selected after fetch data for showing data in select field|
| `isLoading` | `boolean` | `false` | ❌ | controlling loading state|
| `disabled`| `boolean` | `false` | ❌ | controlling disabled state |
| `autoPickKey` | `search`| - | ❌ | Set key to payload when search data. It will active if prop `isAsync`|
| `isAsync` | `boolean` | `false` | ❌ | If its `true`, will fetch data to backend every search |
| `apiVersion`| `v${number}`| `v1`| ❌ | Versioning api, used by api go |
| `apiType` | `lc, go, py-go, hrm-go` | `lc`| ❌ | Type of api used |
| `customRender`| `(record: Record<string, any>) => ReactElement[] , ReactElement`| — | ❌ | Custom how data appear in list |

#### Usage

```jsx
/* file pages/test/test-control/WPControlTest */
import WPForm from "lib/components/wp-form";
import WPControl from "lib/components/wp-form/wp-control";

const WPControlTest = () => {
  return (
    <WPForm>
      <WPControl
        type="select"
        name="firstname"
        label="First Name"
        datasource="SomeApi"
      />
    </WPForm>
  );
};

export default WPControlTest;
```

---

#### WPRequestFor

All props can be used for create request for field

| Prop Name | Type| Default | Required | Description|
| --- | --- | --- | --- | --- |
| `datasource`| `string`| — | ❌ | API for fetching request for data based on workflow approval |
| `customPayload` | `Record<string, any>` | — | ❌ | Payload for fetching data with `datasource`|
| `disabled`| `boolean` | `false` | ❌ | controlling disabled state |

#### Usage

```jsx
/* file pages/test/test-control/WPControlTest */
import WPForm from "lib/components/wp-form";
import WPControl from "lib/components/wp-form/wp-control";

const WPControlTest = () => {
  return (
    <WPForm>
      <WPControl
        type="requestfor"
        name="emp_id"
        label="Request For"
        datasource="leaveRequest" // full datasource will be leaveRequest._filterEmployeeRequestFor
      />
    </WPForm>
  );
};

export default WPControlTest;
```

---

#### WPCheckBox

All props can be used for create checkbox field

| Prop Name | Type| Default | Required | Description|
| --- | --- | --- | --- | --- |
| `listOptions`| `{ value: string, label: string }[]` | — | ✅ | controlling field checkbox checklist, for single value, you can put `Y\|N` in value key, means if checked will sent `Y` value to backend if not then will send the right side of the `\|` pipes. for multiple value, it will send the value in array |
| `disabled`| `boolean` | `false` | ❌ | controlling disabled state |

#### Usage

```jsx
/* file pages/test/test-control/WPControlTest */
import WPForm from "lib/components/wp-form";
import WPControl from "lib/components/wp-form/wp-control";

const App = () => {
  return (
    <WPForm>
      <WPControl
        type="checkbox"
        name="firstname"
        label="CheckBox"
        listOptions={[{ value: "Y|N", label: "Yes" }]} // single item
      />

      <WPControl
        type="checkbox"
        name="firstname"
        label="CheckBox"
        listOptions={[{ value: "APPLE", label: "Apple" }, { value: "ANDROID", label: "Android" }]} // multiple
      />
    </WPForm>
  );
};
```

---
