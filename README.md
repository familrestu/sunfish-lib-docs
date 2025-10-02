<img width="347" height="114" alt="image" src="https://github.com/user-attachments/assets/ec2d77a0-bfa0-4d5d-aa1a-6c67101bee51" />

# SunFish React Component Library

This repository contains documentation for all **SunFish React components**.  
Each component has its own markdown file with props, usage, and examples.  
We are using **Ant Design v4**, so some components combine AntD props.

---

## 📚 Components List

### 📌 Component: WPPage

#### Overview
- **Name**: `WPPage`  
- **Description**: A component for every page creation, must use this WPPage component, so all pages will have the same result or layout.  
- **Import path**: `lib/components/wp-page`

#### Props

| Prop Name | Type | Default | Required | Description |
|-----------|------|---------|----------|-------------|
| `accessCode`   | `string` | — | ❌ | access code to check if user authorize to view this page or not. when user have enough privilege, it will automatically show "Add" button to link to add page, with format `{currentpage}.Add` |
| `buttonAddURL`   | `string` | — | ❌ | update pagelink for button Add URL |
| `showAddButton`   | `boolean` | — | ❌ | show/hide button add, by default will set to true if `props.buttonAddURL` have value, but you can control this value from state |
| `showHeader`   | `boolean` | true | ❌ | show/hide page breadcrumb |
| `withContent` | `boolean` | false | ❌ | wrap content in white card |
| `extraButton` | `React.Node[]` | — | ❌ | add more buttons in breadcrumb |
| `staticBreadCrumb` | `string[]` | — | ❌ | update automatic breadcrumb generated based on current page URL |
| `children` | `React.Children` | — | ❌ | content of the WPPage |

#### Usage
```jsx

/* file pages/test/listing-page/ListingPage */
import { Row, Col, Card } from 'antd';
import WPPage from 'lib/components/wp-page';

const ListingPage = (props) => {
  return (
    <WPPage withContent>
      <Row>
        <Col span={24}>
          <Card>1</Card>
          <Card>2</Card>
          <Card>3</Card>
        </Col>
      </Row>
    </WPPage>
  )
}

export default ListingPage;
```

---

### 📌 Component: WPListing

#### Overview
- **Name**: `WPListing`  
- **Description**: A component to render table list, also contain the card list for mobile view
- **Import path**: `lib/components/wp-listing`
- **Origin Components**: AntDesign v4 table components

#### Props WPListing

| Prop Name | Type | Default | Required | Description |
|-----------|------|---------|----------|-------------|
| `accessCode`   | `string` | — | ✅ | this props required if `props.datasource` is provided. access code use by system to check if user is authorize to call the API or not |
| `datasource`   | `string` | — | ❌ | for type lucee (lc), if qlid then you can put `datasource=employee._listing` or `datasource=ofid=employee.list`, by default it will always using `qlid`. for type `'hrm-go'` and `'go'`, you can specified the endpoint, `datasource="/general/id-card-generator/list" apiType="hrm-go"` by default it will always preppend v1 when call the api, if you have another version api, you specified `apiType="v2"` |
| `apiType`   | `'lc' \| 'hrm-go' \| 'go'` | `'lc'` | ❌ | determine which endpoint will be used |
| `apiVersion`   | `string` | `'v1'` | ❌ | determine which api version of endpoint will be used, default to `v1` |
| `limitPage`   | `number` | `ACCOUNT CONFIG` | ❌ | limit of the data from API result |
| `ArrDatasource`   | `{[key: string]: any}[]` | — | ❌ | when you want to control you API Calling by yourself, you can use this props to populate Listing data, if using lucee, please use helper `formatDataResponseLC()` |
| `showToolbar` | `boolean` | `true` | ❌ | show/hide listing built in toolbar, which contain buttons of "Filter" and "Manage Column" |
| `showFooter` | `boolean` | `true` | ❌ | show/hide listing built in pagination |
| `defaultView` | `'card' \| 'list'` | `card` if `props.CardComponent` is provided and it's in mobile screen, if none will be default to `list` | ❌ | show/hide listing built in pagination |
| `CardComponent` | `React.ReactNode` | — | ❌ | Card component to be shown in listing | 
| `cardRowHeight` | `number` | — | ❌ | card height | 
| `cardGutterSize` | `number` | — | ❌ | size of pixels range for each card vertically and horizontally | 
| `cardColumnCount` | `{ xs: number, sm: number, md: number, lg: number, xl: number, xxl: number }` | — | ❌ | card component to be shown in listing | 
| `customPayload` | `{[key: string]: unknown}` | — | ❌ | add some custom payload when system call the API | 

#### Props WPColumn
childrens of WPColumn
| Prop Name | Type | Default | Required | Description |
|-----------|------|---------|----------|-------------|
| `title`   | `string` | — | ❌ | column name |
| `dataIndex`   | `string` | — | ❌ | render the column base on data provided from ArrDatasource / from API result. dataIndex is the key of the column you want to show, eg: if you want to show data of EMP_NAME |
| `render`   | `(value, record) => React.ReactNode)` | — | ❌ | `value` is the default value system will get based on `dataIndex` you provide, but if you want to combine some column, you can use render eg: `(_, record) => <Typography.Text>{record.EMP_NAME} ({record.EMP_NO})</Typography.Text>` |
| `showSorter`   | `boolean` | `true` | ❌ | show sorter in table header |
| `showSearch`   | `boolean` | `true` | ❌ | show search in table header |
| `type`   | `'date'\|'select'\|'link'\|'currency'\|'number'` | — | ❌ | the search type will be based on this type |
| `listOptions`   | `{[key: string]: unknown}[]` | — | ❌ | if you want to give selection when search, lets say for gender, you can put an array `const listOptions = [{value: 0, title: 'Female'}, {value: 1, title: 'Male'}]` |
| `width`   | `number` | 200 | ❌ | width of column |
| `mask`   | `string` | — | ❌ | when you want to mask the result of the api, lets say you want 0 is equal to no, and 1 is equal to yes, then you can put `mask=0=No\|1=Yes` |

#### Props WPColumnGroup
childrens of WPColumnGroup
| Prop Name | Type | Default | Required | Description |
|-----------|------|---------|----------|-------------|
| `title`   | `string` | — | ❌ | column name |
| `children`   | `React.ReactNode` | — | ❌ | column group children |
| `showSorter`   | `boolean` | `true` | ❌ | show sorter in table header |
| `showSearch`   | `boolean` | `true` | ❌ | show search in table header |

#### Usage
```jsx

/* file pages/test/listing-page/ListingComponent */
import { Row, Col, Card } from 'antd';
import WPListing, { WPColumn, WPColumnGroup } from 'lib/components/wp-listing'

const ListingComponent = (props) => {

  return (
    <WPListing datasource="Employee._Listing">
        <WPColumn title="Employee No" dataIndex="EMP_NO" />
        <WPColumn title="Employee Name" dataIndex="EMP_NAME" />
        <WPColumn title="Employee Position" dataIndex="POS_NAME" />
        <WPColumnGroup title="Personal Details">
            <WPColumn title="Gender" dataIndex="GENDER" />
            <WPColumn title="Date of Birth" dataIndex="BIRTHDAY" />
            <WPColumn title="Birthplace" dataIndex="BIRTHPLACE" />
        </WPColumnGroup>
    </WPListing>
  )
}

export default ListingComponent;
```
---
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

---

## 📚 Hooks List

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


---

## 📚 Utilities List

### 📌 Helpers: getDictionary

#### Overview
- **Name**: `getDictionary`  
- **Description**: to translate our words
- **Import path**: `lib/helpers/utils/getDictionary`

#### Parameters
childrens of ComponentName
| Param Name | Type | Description |
|-----------|------|-------------|
| `textID`   | `string` | text id used for translate |
| `defaultTranslations`   | `string` | default translations |

#### Usage
```jsx
import getDictionary from 'lib/helpers/utils/getDictionary'

const TranslateExample = () => {
    return getDictionary('Employee', 'Employee')
}

export default TranslateExample
```


---

### 📌 Helpers: formatDataResponseLC

#### Overview
- **Name**: `formatDataResponseLC`  
- **Description**: standard tools to update Lucee query response to array of object
- **Import path**: `lib/components/wp-form/wp-helpers/utilities`

#### Usage
```jsx
import { formatDataResponseLC } from 'lib/components/wp-form/wp-helpers/utilities';

const FormatDataResponseLCExample = () => {
    const sampleOfLuceeQueryResponse = {
        "DATA": [
            [
                "220093",
                4513,
                "Aashka Guritno Rahnada",
                "DO220701",
                "Project Implementation",
                "Manager",
                "Assistant Project Manager",
                "syfa1@dataon.com",
                "202504/4fefe0a17a7ce658d73d51f25c10278dd3bf004a.png",
                1,
                "-6.2835667554818295, 106.72552066741791",
                "0",
                "0012",
                "September, 01 2016 00:00:00 +0700",
                "",
                1,
                "DIRECT",
                "KONGHUCU",
                "4",
                "Assistant Project Manager",
                "Manager",
                "Project Implementation",
                "DO220701",
                4516,
                "1031",
                "PERMANENT",
                "February, 03 1993 00:00:00 +0700",
                "SO",
                "08595959595",
                "March, 30 2022 14:15:22 +0700",
                12415,
                1,
                "September, 01 2016 00:00:00 +0700",
                "Male",
                "anakbaru1991",
                "202504/4fefe0a17a7ce658d73d51f25c10278dd3bf004a.png",
                1708,
                "PROASS",
                "",
                "Jln Simprug",
                "Permanent",
                "Aashka",
                "",
                1,
                "4",
                "Rahnada",
                4513,
                "September, 01 2016 00:00:00 +0700",
                "jabar",
                "Guritno",
                "Aashka Guritno Rahnada (220093)  Aashka  Guritno  Rahnada ",
                "",
                "Aashka Guritno Rahnada (220093)",
                "Simprug Office",
                "123451234565435"
            ]
        ],
        "COLUMNS": [
            "EMP_NO",
            "DEPT",
            "EMP_NAME",
            "EMP_ID",
            "DEPT_NAME",
            "GRADE_NAME",
            "POS_NAME",
            "EMAIL",
            "VPHOTO",
            "GENDER",
            "WORKLOCATION_LATLNG",
            "MARITALSTATUS",
            "PHONE_EXT",
            "JOIN_DATE",
            "TERMINATE_DATE",
            "EMPLOYEE_STATUS",
            "JOB_STATUS_CODE",
            "RELIGION_CODE",
            "JOB_GRADE",
            "EMP_POS",
            "JOB_GRADE_NAME",
            "DEPT_ID_LOOKUP",
            "OPTVALUE",
            "POSITION_ID",
            "COST_CODE",
            "EMP_STATUS_CODE",
            "BIRTHDATE",
            "WORK_LOCATION_CODE",
            "PHONE",
            "CREATED_DATE",
            "USER_ID",
            "IS_MAIN",
            "START_DATE",
            "GENDER_LOOKUP",
            "USER_NAME",
            "PHOTO",
            "COMPANY_ID",
            "POS_CODE",
            "SUPERVISOR",
            "WORKLOCATION_ADDRESS",
            "EMP_STATUS",
            "FIRST_NAME",
            "END_DATE",
            "STATUS",
            "GRADE",
            "LAST_NAME",
            "DEPT_ID",
            "PERMANENT_DATE",
            "BIRTHPLACE",
            "MIDDLE_NAME",
            "ALL_NAME",
            "MANAGER",
            "OPTTEXT",
            "WORKLOCATION_NAME",
            "TAXNO"
        ],
    }

    /* example response */
    /* 
        console.log(formatDataResponseLC(sampleOfLuceeQueryResponse))
        
        [
            {
                "EMP_NO": "220093",
                "DEPT": 4513,
                "EMP_NAME": "Aashka Guritno Rahnada",
                "EMP_ID": "DO220701",
                "DEPT_NAME": "Project Implementation",
                "GRADE_NAME": "Manager",
                "POS_NAME": "Assistant Project Manager",
                "EMAIL": "syfa1@dataon.com",
                "VPHOTO": "202504/4fefe0a17a7ce658d73d51f25c10278dd3bf004a.png",
                "GENDER": 1,
                "WORKLOCATION_LATLNG": "-6.2835667554818295, 106.72552066741791",
                "MARITALSTATUS": "0",
                "PHONE_EXT": "0012",
                "JOIN_DATE": "September, 01 2016 00:00:00 ",
                "TERMINATE_DATE": "",
                "EMPLOYEE_STATUS": 1,
                "JOB_STATUS_CODE": "DIRECT",
                "RELIGION_CODE": "KONGHUCU",
                "JOB_GRADE": "4",
                "EMP_POS": "Assistant Project Manager",
                "JOB_GRADE_NAME": "Manager",
                "DEPT_ID_LOOKUP": "Project Implementation",
                "OPTVALUE": "DO220701",
                "POSITION_ID": 4516,
                "COST_CODE": "1031",
                "EMP_STATUS_CODE": "PERMANENT",
                "BIRTHDATE": "February, 03 1993 00:00:00 ",
                "WORK_LOCATION_CODE": "SO",
                "PHONE": "08595959595",
                "CREATED_DATE": "March, 30 2022 14:15:22 ",
                "USER_ID": 12415,
                "IS_MAIN": 1,
                "START_DATE": "September, 01 2016 00:00:00 ",
                "GENDER_LOOKUP": "Male",
                "USER_NAME": "anakbaru1991",
                "PHOTO": "202504/4fefe0a17a7ce658d73d51f25c10278dd3bf004a.png",
                "COMPANY_ID": 1708,
                "POS_CODE": "PROASS",
                "SUPERVISOR": "",
                "WORKLOCATION_ADDRESS": "Jln Simprug",
                "EMP_STATUS": "Permanent",
                "FIRST_NAME": "Aashka",
                "END_DATE": "",
                "STATUS": 1,
                "GRADE": "4",
                "LAST_NAME": "Rahnada",
                "DEPT_ID": 4513,
                "PERMANENT_DATE": "September, 01 2016 00:00:00 ",
                "BIRTHPLACE": "jabar",
                "MIDDLE_NAME": "Guritno",
                "ALL_NAME": "Aashka Guritno Rahnada (220093)  Aashka  Guritno  Rahnada ",
                "MANAGER": "",
                "OPTTEXT": "Aashka Guritno Rahnada (220093)",
                "WORKLOCATION_NAME": "Simprug Office",
                "TAXNO": "123451234565435"
            }
        ]
    */

    return JSON.stringify(formatDataResponseLC(sampleOfLuceeQueryResponse))
}

export default FormatDataResponseLCExample
```


---
