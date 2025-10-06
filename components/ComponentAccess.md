### 📌 Helpers: ComponentAccess

#### Overview
- **Name**: `ComponentAccess`  
- **Description**: standard components to show and hide components based on access, same as `useComponentAccess` but simplified for `React.Component`
- **Import path**: `lib/components/global/component-access'`

#### Usage
```jsx
import ComponentAcces from 'lib/components/global/component-access'
import { ForbiddenFallback } from 'lib/components/other/verify-access';

const ComponentAccessComponentsExample = () => {
    return (
        <ComponentAccess auth="hrm.attendance.leave.myleavebalance:read">
            <WPListing datasource="employee-api" />
        </ComponentAccess>
    )
}

export default ComponentAccessComponentsExample
```

---