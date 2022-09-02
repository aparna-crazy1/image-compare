## Project setup
```
npm install
npm run serve
```
### axios

Used for consuming APIs
Limit is added to get API call - https://jsonplaceholder.typicode.com/photos
Limit can be changed

### cards

Cards contain the image related data and are displayed in grid format
On hover of the cards, compare or remove buttons are visible. Card UI also conveys whether image is added or not for comparison
### vuetify

Used for adding UI components

### `components`

The components directory contains your Vue.js components. Components make up the different parts of your page and can be reused and imported into your pages.


### pagination

We can also add pagination to the image data, since it's very large.
Attempted to replace grid view of cards with pagination of cards.
Pagination component folder contains related files.
The Pagination of cards can be tested by un-commenting Pagination component in App.vue and commenting our Compare component usage.
 