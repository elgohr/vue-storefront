# Redis cache

## Introduction

This package provides integration with [Redis](https://redis.io/). For more information about this topic, please refer to [SSR Cache](../performance/ssr-cache.md) page.

## Installation

Install required packages:

```sh
yarn add @vue-storefront/cache
yarn add @vue-storefront/redis-cache
```

Register `@vue-storefront/cache` module with following configuration:

```javascript
// nuxt.config.js

export default {
  modules: [
    ['@vue-storefront/cache/nuxt', {
      invalidation: {
        // Invalidation options
      },
      driver: [
        '@vue-storefront/redis-cache',
        {
          defaultTimeout: 86400,
          redis: {
            host: 'localhost',
            port: 6379,
            password: 'password'
          }
        }
      ]
    }]
  ]
};
```

We can break down package configuration into two pieces:

* `invalidation` - please refer to [SSR Cache configuration](../performance/ssr-cache.md) page.
* `driver` - object containing:
  * `defaultTimeout` - number of seconds until records expire, even if not invalidated;
  * `redis` - object directly passed to [ioredis](https://github.com/luin/ioredis/blob/master/API.md#new-redisport-host-options);