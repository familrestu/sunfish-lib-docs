### 📌 Helpers: useOnFetch

#### Overview
- **Name**: `useOnFetch`  
- **Description**: standard fetch hooks
- **Import path**: `lib/helpers/utils/useOnFetch`
- - **Origin functions**: axios version 1.6.5

#### Usage
```jsx
import { useEffect } from 'react'
import useOnFetch from 'lib/helpers/utils/useOnFetch'
import { formatDataResponseLC } from 'lib/components/wp-form/wp-helpers/utilities';

const FetchExample = () => {
    const [loading, setLoading] = useState(false);
    const [arrData, setArrData] = useState([]);

    const fetch = useOnFetch();

    const getData = () => {
        setLoading(true);
        fetch({
            params: {
                qlid: "address._listing"
            },
            data: {
                emp_id: "EMPID_123456"
            }
        }).then((res) => {
            if(res.data) {
                const ArrData = setArrData(formatDataResponseLC(res.data.DATA));

            }
        }).finally(() => {
            setLoading(false);
        })
    }

    useEffect(() => {
        getData()
    }, [])

    return loading ? 'loading...' : JSON.stringify(arrData)
}

export default FetchExample
```
