# Vue Storefront Next x Commercetools Module
## How to install
1. Open `nuxt.config.js`
2. Inside `buildModules`, line before `@vue-storefront/nuxt` add:
```js
['@vue-storefront/commercetools/nuxt', {
    api: {
        uri: 'https://api.commercetools.com/<your-api>/graphql',
        authHost: 'https://auth.sphere.io',
        projectKey: 'vsf-ct-dev',
        clientId: '<id>',
        clientSecret: '<secret>',
        scopes: [
          'create_anonymous_token:vsf-ct-dev',
          'manage_my_orders:vsf-ct-dev',
          'manage_my_profile:vsf-ct-dev',
          'manage_my_shopping_lists:vsf-ct-dev',
          'manage_my_payments:vsf-ct-dev',
          'view_products:vsf-ct-dev',
          'view_published_products:vsf-ct-dev'
        ]
      },
      locale: 'en',
      currency: 'USD',
      country: 'US',
      acceptLanguage: ['en', 'de'],
      countries: [
        { name: 'US',
          label: 'United States' },
        { name: 'AT',
          label: 'Austria' },
        { name: 'DE',
          label: 'Germany' },
        { name: 'NL',
          label: 'Netherlands' }
      ],
      currencies: [
        { name: 'EUR',
          label: 'Euro' },
        { name: 'USD',
          label: 'Dollar' }
      ],
      locales: [
        { name: 'en',
          label: 'English' },
        { name: 'de',
          label: 'German' }
      ]
    }]
}]
```

## Generate token middleware
Commercetools nuxt module injects [middleware](https://github.com/DivanteLtd/vue-storefront/blob/next/packages/commercetools/composables/nuxt/token-middleware.js) that is responsible for createing/refreshing token if needed - when user refreshes page. In some rare case, you might want to disable [this middleware](https://github.com/DivanteLtd/vue-storefront/blob/next/packages/commercetools/composables/nuxt/token-middleware.js). If so, add `disableGenerateTokenMiddleware` to the `@vue-storefront/commercetools/nuxt`'s options module in `buildModules`:
```js
['@vue-storefront/commercetools/nuxt', {
  // ...
  disableGenerateTokenMiddleware: true
  // ...
}]
```

## Example config
```js
export const config = {
  api: {
    uri: 'https://mysite.com/vsf-ct-dev/graphql',
    authHost: 'https://auth.com',
    projectKey: 'vsf-ct-dev',
    clientId: 'yourClientId',
    clientSecret: 'yourClientSecret',
    scopes: [
      'create_anonymous_token:vsf-ct-dev',
      'manage_my_orders:vsf-ct-dev',
      'manage_my_profile:vsf-ct-dev',
      'manage_my_shopping_lists:vsf-ct-dev',
      'manage_my_payments:vsf-ct-dev',
      'view_products:vsf-ct-dev',
      'view_published_products:vsf-ct-dev'
    ]
  },
  locale: 'en',
  acceptLanguage: ['en', 'de'],
  currency: 'USD',
  country: 'US',
  store: 'luxury-brand',
  countries: [
    { name: 'US',
      label: 'United States' },
    { name: 'AT',
      label: 'Austria' },
    { name: 'DE',
      label: 'Germany' },
    { name: 'NL',
      label: 'Netherlands' }
  ],
  currencies: [
    { name: 'EUR',
      label: 'Euro' },
    { name: 'USD',
      label: 'Dollar' }
  ],
  locales: [
    { name: 'en',
      label: 'English' },
    { name: 'de',
      label: 'German' }
  ],
  cookies: {
    currencyCookieName: 'vsf-currency',
    countryCookieName: 'vsf-country',
    localeCookieName: 'vsf-locale',
    storeCookieName: 'vsf-store'
  }
};
```
