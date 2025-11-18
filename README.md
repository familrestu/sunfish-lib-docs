<img width="347" height="114" alt="image" src="https://github.com/user-attachments/assets/ec2d77a0-bfa0-4d5d-aa1a-6c67101bee51" />

# SunFish React Component Library

This repository contains documentation for all **SunFish React components**.  
Each component has its own markdown file with props, usage, and examples.  
We are using **Ant Design v4**, so some components combine AntD props.

---

## 📚 Components List

- [WPPage](./components/WPPage.md)
- [WPForm](./components/WPForm.md)
- [WPListing](./components/WPListing.md)
- [WPControl](./components/WPControl.md)
- [ComponentAccess](./components/ComponentAccess.md)

---

## 📚 Hooks List

- [useOnFetch](./hooks/useOnFetch.md)
- [useComponentAccess](./hooks/useComponentAccess.md)

---

## 📚 Utilities List

- [getDictionary](./helpers/getDictionary.md)
- [formatDataResponseLC](./helpers/formatDataResponseLC.md)

---

## Coding Structure
```
.
├── src/
│   ├── pages/
│   │   ├── menu-page/
│   │   │   ├── components/
│   │   │   │   ├── SpecificComponentA.js
│   │   │   │   └── SpecificComponentB.js
│   │   │   ├── contexts/
│   │   │   │   ├── ContextMenuPageProvider.js
│   │   │   │   └── ContextMenuPage.js
│   │   │   ├── MenuPage.js
│   │   │   └── index.js
```