### 📌 Component: WPListing

#### Overview
- **Name**: `WPListing`  
- **Description**: A component to render table list, also contain the card list for mobile view
- **Import path**: `lib/components/wp-listing`
- **Origin Components**: AntDesign v4 table components

#### Props WPListing

| Prop Name         | Type                                                                          | Default                                                                                                  | Required | Description                                                                                                                                                                                                                                                                                                                                                                                                     |
| ----------------- | ----------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `accessCode`      | `string`                                                                      | —                                                                                                        | ✅        | this props required if `props.datasource` is provided. access code use by system to check if user is authorize to call the API or not                                                                                                                                                                                                                                                                           |
| `datasource`      | `string`                                                                      | —                                                                                                        | ❌        | for type lucee (lc), if qlid then you can put `datasource=employee._listing` or `datasource=ofid=employee.list`, by default it will always using `qlid`. for type `'hrm-go'` and `'go'`, you can specified the endpoint, `datasource="/general/id-card-generator/list" apiType="hrm-go"` by default it will always preppend v1 when call the api, if you have another version api, you specified `apiType="v2"` |
| `apiType`         | `'lc' \| 'hrm-go' \| 'go'`                                                    | `'lc'`                                                                                                   | ❌        | determine which endpoint will be used                                                                                                                                                                                                                                                                                                                                                                           |
| `apiVersion`      | `string`                                                                      | `'v1'`                                                                                                   | ❌        | determine which api version of endpoint will be used, default to `v1`                                                                                                                                                                                                                                                                                                                                           |
| `limitPage`       | `number`                                                                      | `ACCOUNT CONFIG`                                                                                         | ❌        | limit of the data from API result                                                                                                                                                                                                                                                                                                                                                                               |
| `ArrDatasource`   | `{[key: string]: any}[]`                                                      | —                                                                                                        | ❌        | when you want to control you API Calling by yourself, you can use this props to populate Listing data, if using lucee, please use helper `formatDataResponseLC()`                                                                                                                                                                                                                                               |
| `showToolbar`     | `boolean`                                                                     | `true`                                                                                                   | ❌        | show/hide listing built in toolbar, which contain buttons of "Filter" and "Manage Column"                                                                                                                                                                                                                                                                                                                       |
| `showFooter`      | `boolean`                                                                     | `true`                                                                                                   | ❌        | show/hide listing built in pagination                                                                                                                                                                                                                                                                                                                                                                           |
| `defaultView`     | `'card' \| 'list'`                                                            | `card` if `props.CardComponent` is provided and it's in mobile screen, if none will be default to `list` | ❌        | show/hide listing built in pagination                                                                                                                                                                                                                                                                                                                                                                           |
| `CardComponent`   | `React.ReactNode`                                                             | —                                                                                                        | ❌        | Card component to be shown in listing                                                                                                                                                                                                                                                                                                                                                                           |
| `cardRowHeight`   | `number`                                                                      | —                                                                                                        | ❌        | card height                                                                                                                                                                                                                                                                                                                                                                                                     |
| `cardGutterSize`  | `number`                                                                      | —                                                                                                        | ❌        | size of pixels range for each card vertically and horizontally                                                                                                                                                                                                                                                                                                                                                  |
| `cardColumnCount` | `{ xs: number, sm: number, md: number, lg: number, xl: number, xxl: number }` | —                                                                                                        | ❌        | card component to be shown in listing                                                                                                                                                                                                                                                                                                                                                                           |
| `customPayload`   | `{[key: string]: unknown}`                                                    | —                                                                                                        | ❌        | add some custom payload when system call the API                                                                                                                                                                                                                                                                                                                                                                |

#### Props WPColumn
childrens of WPColumn
| Prop Name      | Type                                             | Default | Required | Description                                                                                                                                                                                                                           |
| -------------- | ------------------------------------------------ | ------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `title`        | `string`                                         | —       | ❌        | column name                                                                                                                                                                                                                           |
| `dataIndex`    | `string`                                         | —       | ❌        | render the column base on data provided from ArrDatasource / from API result. dataIndex is the key of the column you want to show, eg: if you want to show data of EMP_NAME                                                           |
| `render`       | `(value, record) => React.ReactNode)`            | —       | ❌        | `value` is the default value system will get based on `dataIndex` you provide, but if you want to combine some column, you can use render eg: `(_, record) => <Typography.Text>{record.EMP_NAME} ({record.EMP_NO})</Typography.Text>` |
| `showSorter`   | `boolean`                                        | `true`  | ❌        | show sorter in table header                                                                                                                                                                                                           |
| `showSearch`   | `boolean`                                        | `true`  | ❌        | show search in table header                                                                                                                                                                                                           |
| `type`         | `'date'\|'select'\|'link'\|'currency'\|'number'` | —       | ❌        | the search type will be based on this type                                                                                                                                                                                            |
| `listOptions`  | `{[key: string]: unknown}[]`                     | —       | ❌        | if you want to give selection when search, lets say for gender, you can put an array `const listOptions = [{value: 0, title: 'Female'}, {value: 1, title: 'Male'}]`                                                                   |
| `width`        | `number`                                         | 200     | ❌        | width of column                                                                                                                                                                                                                       |
| `mask`         | `string`                                         | —       | ❌        | when you want to mask the result of the api, lets say you want 0 is equal to no, and 1 is equal to yes, then you can put `mask=0=No\|1=Yes`                                                                                           |
| `linkto`       | `string`                                         | —       | ❌        | this will automatically render the column value as link `/somelink/::EMP_NO` notice the EMP_NO is the value you got from back-end, this will automatically encrypt the `EMP_NO` value                                                 |
| `hiddenColumn` | `boolean`                                        | `false` | ❌        | when set to true then will be hidden in table column, but still able to be managed from show / manage column                                                                                                                          |
| `primaryKey`   | `boolean`                                        | `false` | ❌        | when set to true then cannot be managed in manage column drawer                                                                                                                                                                       |



#### Props WPColumnGroup
childrens of WPColumnGroup
| Prop Name    | Type              | Default | Required | Description                 |
| ------------ | ----------------- | ------- | -------- | --------------------------- |
| `title`      | `string`          | —       | ❌        | column name                 |
| `children`   | `React.ReactNode` | —       | ❌        | column group children       |
| `showSorter` | `boolean`         | `true`  | ❌        | show sorter in table header |
| `showSearch` | `boolean`         | `true`  | ❌        | show search in table header |


---


#### Usage

Simple Listing page

```jsx

/* file pages/test/listing-page/ListingComponent */
import { Link } from 'react-router-dom';
import WPListing, { WPColumn, WPColumnGroup } from 'lib/components/wp-listing'
import { paramsEncrypt, encrypt } from 'lib/helpers/paramsCrypto';

const ListingComponent = (props) => {

  return (
    <WPListing datasource="Employee._Listing">
        <WPColumn title="Employee No" dataIndex="EMP_NO" type="link" linkto="/standard/employee/employee-information/::EMP_ID" />
        <WPColumn title="Employee No" dataIndex="EMP_NO" render={(_, record) => <Link to={paramsEncrypt(`/standard/employee/employee-information/:${record?.EMP_ID}`)}>{`${record?.EMP_NAME} (${record?.EMP_NO})`}</Link>} />
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

in this example, you can see 2 type of link, first one is generated from listing, the second one is the one you create by yourself
recommended to use the first one if you don't have to render custom value in the table

---

Simple Listing page with mobile view

```jsx

/* file pages/test/listing-page/ListingComponentMobile */
import { Link } from 'react-router-dom';
import { Card } from 'antd';
import WPListing, { WPColumn, WPColumnGroup } from 'lib/components/wp-listing'
import { paramsEncrypt, encrypt } from 'lib/helpers/paramsCrypto';

const ListingComponentMobile = (props) => {
  return (
    <WPListing
      datasource="Employee._Listing"
      cardRowHeight={158} // adjust this base on your card height
      cardColumnCount={{ xs: 1, sm: 1, md: 1, lg: 2, xl: 3, xxl: 4 }}
      CardComponent={(record) => (
        <Link to={paramsEncrypt(`/standard/employee/employee-information/:${record?.EMP_ID}`)}>
          <Card>
            /* your card details here */
            {record?.EMP_NAME} /* example */
          </Card>
        </Link>
      )}
    >
        <WPColumn title="Employee No" dataIndex="EMP_NO" type="link" linkto="/standard/employee/employee-information/::EMP_ID" />
        <WPColumn title="Employee No" dataIndex="EMP_NO" render={(_, record) => <Link to={paramsEncrypt(`/standard/employee/employee-information/:${record?.EMP_ID}`)}>{`${record?.EMP_NAME} (${record?.EMP_NO})`}</Link>} />
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

export default ListingComponentMobile;
```