<template lang="html">
    <div class="ps-form__orders ps-block--checkout-order">
        <h3 v-if="shipping === false">Votre commande</h3>
        <div class="ps-block--checkout-order">
            <div class="ps-block__content">
                <figure>
                    <figcaption>
                        <strong>Produits</strong>
                        <strong>total</strong>
                    </figcaption>
                </figure>
                <figure class="ps-block__items">
                    <nuxt-link
                        v-for="(product, index) in cartProducts"
                        :to="`/product/${product.id}`"
                        :key="product.id"
                        class="ps-product__title"
                    >
                        {{ product.title }}
                        <br />
                        {{ cartItems[index].quantity }} x ${{
                            product.price.toFixed(2)
                        }}
                    </nuxt-link>
                </figure>
                <figure>
                    <figcaption>
                        <strong>Sous-total</strong>
                        <small>{{ amount }} FCFA</small>
                    </figcaption>
                </figure>
                <figure v-if="shipping === true">
                    <figcaption>
                        <strong>Livraison</strong>
                        <small>$ 20.00</small>
                    </figcaption>
                </figure>
                <figure v-else class="ps-block__shipping">
                    <h3>Livraison</h3>
                    <p>Calculé à l'étape suivante</p>
                </figure>
            </div>
        </div>
    </div>
</template>

<script>
import { mapState } from 'vuex';

export default {
    name: 'ModuleOrderSummary',
    props: {
        shipping: {
            type: Boolean,
            default: () => false
        }
    },
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
