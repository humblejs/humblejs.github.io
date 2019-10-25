# Shopping Cart
Utilities specifically for adding shopping cart to your website.

[Demo](https://humble.js.org/pkg/shopping-cart/demo)

## Install

```
yarn add @humblejs/shopping-cart
```

## Usage

```
import { withShoppingCart, ShoppingCartProvider } from '@humblejs/shopping-cart';
```

```
...

const AddToCartButton = withShoppingCart(props => (
  <button onClick={() => { props.shoppingCart.add(props.product); }}>Add</button>
));

...

<ShoppingCartProvider>
  <AddToCartButton />
</ShoppingCartProvider>
```

## Context Props
All the functions are available via global context under `shoppingCart` object. Following are the list of functions available:

| Key | Description |
|----------|-------------|
| `list()` | Return all the items in the cart in RAW format |
| `add(item, quantity)` | Add `item` to the cart with specified `quantity` |
| `changeQuantity(item, newQuantity)` | Change number of `item`s to specified quantity. `0` quantity will remove item from the cart. |
| `remove({ id })` | Remove item with specified ID |
| `has({ id })` | Determine whether item with specified ID is in the cart or not |
| `get({ id })` | Get item with specified ID from the cart if available. Otherwise NULL |
| `getQuantity()` | Count quantity of items with specified ID in the cart |
| `total()` | Calculate total cost for the items in the cart based on their unit prices |

## Wishlist
Shopping cart component also comes with wishlist provider, the provider points to same base component which helps in maintaining the code but some functions may be unnecessary and some are unavailable (e.g, `getQuantity` does not apply to wishlist), so usage of it is to be done with care.

```
import { withShoppingCart, withWishlist, ShoppingCartProvider, WishlistProvider } from '@humblejs/shopping-cart';

// ....

const PageWrapper = flow(
  withShoppingCart,
  withWishlist,
)(Page);

// ....

<ShoppingCartProvider {...props.cart}>
  <WishlistProvider {...props.wishlist}>
    <PageWrapper />
  </WishlistProvider>
</ShoppingCartProvider>
```

where `props.cart` is props specific to shopping cart and `props.wishlist` is specific to wishlist.

## Item
All the functions take `item` as first parameter. Each item must at least contain `id` field.

General `Item` model must have following properties for it to properly work
 * `id`
 * `unitPrice`

All the rest of the fields are considered `product`

The shopping cart uses `localStorage` for client side. Validations on the server side are done separately.
