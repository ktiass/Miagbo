<template lang="html">
    <div class="ps-section--shopping ps-shopping-cart">
        <div class="container">
            <div class="ps-section__header">
                <h1>Panier</h1>
            </div>
            <div class="ps-section__content">
                <table-shopping-cart v-if="cartProducts !== null" />
                <p v-else>Panier vide</p>
                <div class="ps-section__cart-actions">
                    <nuxt-link to="/shop" class="ps-btn">
                        <i class="icon-arrow-left mr-2"></i>
                        Retour à la boutique
                    </nuxt-link>
                </div>
            </div>
            <div class="ps-section__footer">
                <div class="row justify-content-end">
                    <div class="col-xl-4 col-lg-4 col-md-12 col-sm-12 col-12 ">
                        <figure>
                            <figcaption>Coupon de remise</figcaption>
                            <div class="form-group">
                                <input
                                    class="form-control"
                                    type="text"
                                    placeholder=""
                                />
                            </div>
                            <div class="form-group">
                                <button class="ps-btn ps-btn--outline">
                                    Appliquer
                                </button>
                            </div>
                        </figure>
                    </div>
                    <div
                        class="col-xl-4 col-lg-4 col-md-12 col-sm-12 col-12 "
                    ></div>
                    <div class="col-xl-4 col-lg-4 col-md-12 col-sm-12 col-12 ">
                        <div class="ps-block--shopping-total">
                            <div class="ps-block__header">
                                <p>
                                    Sous-total <span> ${{ total }}</span>
                                </p>
                            </div>
                            <div class="ps-block__content">
                                <ul class="ps-block__product">
                                    <li
                                        v-for="(product, index) in cartProducts"
                                    >
                                        <span class="ps-block__estimate">
                                            <nuxt-link
                                                :to="`/product/${product.id}`"
                                                class="ps-product__title"
                                            >
                                                {{ product.title }}
                                                <br />
                                                x
                                                {{ cartItems[index].quantity }}
                                            </nuxt-link>
                                        </span>
                                    </li>
                                </ul>
                                <h3>
                                    Total <span>${{ amount }}</span>
                                </h3>
                            </div>
                        </div>
                        <nuxt-link
                            to="/account/checkout"
                            class="ps-btn ps-btn--fullwidth"
                        >
                            Passer à la caisse
                        </nuxt-link>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import { mapState } from 'vuex';
import ProductShoppingCart from '~/components/elements/product/ProductShoppingCart';
import TableShoppingCart from '~/components/partials/account/modules/TableShoppingCart';

export default {
    name: 'ShoppingCart',
    components: { TableShoppingCart, ProductShoppingCart },
    computed: {
        ...mapState({
            cartItems: state => state.cart.cartItems,
            total: state => state.cart.total,
            amount: state => state.cart.amount,
            cartProducts: state => state.product.cartProducts
        })
    }
};
</script>

<style lang="scss" scoped></style>
