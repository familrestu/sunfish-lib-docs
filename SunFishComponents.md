# 🌞 SunFish React Component Library

This document contains props, usage examples, and notes for all **SunFish React components**.  
Use it as a reference for development. we are using ant design version 4, so our components will have combined props with antd components

---

## 📌 Component: WPPage

### Overview
- **Name**: `WPPage`  
- **Description**: A component for every page creation, must use this WPPage component, so all pages will have the same result or layout.  
- Import path: `lib/components/wp-page`

### Props

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

### Usage
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
```
