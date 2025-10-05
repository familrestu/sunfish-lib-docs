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
```
