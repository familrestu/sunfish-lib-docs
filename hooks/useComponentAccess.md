### 📌 Helpers: useComponentAccess

#### Overview
- **Name**: `useOnFetch`  
- **Description**: standard hooks for access checking
- **Import path**: `lib/helpers/hooks/useComponentAccess'`

#### Usage
```jsx
import useComponentAccess from 'lib/helpers/hooks/useComponentAccess'
import { ForbiddenFallback } from 'lib/components/other/verify-access';

const ComponentAccessHooksExample = () => {
    const { hasAccess } = useComponentAccess('hrm.employee:read');

    useEffect(() => {
        getData()
    }, [])

    if(!hasAccess) {
        return <ForbiddenFallback>
    }

    return <WPListing datasource="employee-api" />
}

export default ComponentAccessHooksExample
```

---