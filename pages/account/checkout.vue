<template lang="html">
    <v-app>
        <v-main>
            <header-default />
            <header-mobile />
            <section class="ps-page--my-account">
                <bread-crumb :breadcrumb="breadCrumb" />
                <checkout />
            </section>
            <newsletters />
            <footer-default />
        </v-main>
    </v-app>
</template>
<script>
import BreadCrumb from '~/components/elements/BreadCrumb';
import HeaderDefault from '~/components/shared/headers/HeaderDefault';
import FooterDefault from '~/components/shared/footers/FooterDefault';
import Newsletters from '~/components/partials/commons/Newsletters';
import EditAddress from '~/components/partials/account/EditAddress';
import Checkout from '~/components/partials/account/Checkout';
import HeaderMobile from '~/components/shared/mobile/HeaderMobile';

export default {
    /*middleware: 'authentication',*/
    components: {
        HeaderMobile,
        Checkout,
        EditAddress,
        Newsletters,
        FooterDefault,
        HeaderDefault,
        BreadCrumb
    },
    transition: 'zoom',
    data: () => {
        return {
            breadCrumb: [
                {
                    text: 'Accueil',
                    url: '/'
                },
                {
                    text: 'Panier',
                    url: '/account/shopping-cart'
                },
                {
                    text: 'Informations de paiement'
                }
            ]
        };
    }
};
</script>

<style lang="scss" scoped></style>
