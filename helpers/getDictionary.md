## 📌 Helpers: getDictionary

### Overview
- **Name**: `getDictionary`  
- **Description**: to translate our words
- **Import path**: `lib/helpers/utils/getDictionary`

### Parameters
childrens of ComponentName
| Param Name | Type | Description |
|-----------|------|-------------|
| `textID`   | `string` | text id used for translate |
| `defaultTranslations`   | `string` | default translations |

### Usage
```jsx
import getDictionary from 'lib/helpers/utils/getDictionary'

const TranslateExample = () => {
    return getDictionary('Employee', 'Employee')
}

export default TranslateExample
```
