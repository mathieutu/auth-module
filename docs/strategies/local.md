# Local Scheme

`local` is the default, general purpose authentication scheme, supporting `Cookie` and `JWT` login flows.

By default `local` scheme is enabled and preconfigured.

> You can set `strategies.local` to `false` to disable it.

## Options

```js
auth: {
  strategies: {
    local: {
      endpoints: {
        login: { url: '/api/auth/login', method: 'post', propertyName: 'token' },
        logout: { url: '/api/auth/logout', method: 'post' },
        user: { url: '/api/auth/user', method: 'get', propertyName: 'user' }
      },
      // tokenRequired: true,
      // tokenType: 'bearer',
    }
  }
}
```

### `endpoints`

Each endpoint is used to make requests using axios. They are basically extending Axios [Request Config](https://github.com/axios/axios#request-config).

> To disable each endpoint, simply set it's value to `false`.

#### `propertyName`

`propertyName` can be used to specify which field of the response JSON to be used for value. It can be `undefined` to directly use API response or being more complicated like `auth.user`.

### `tokenRequired`

This option can be used to disable all token handling. Useful for Cookie only flows. \(Enabled by default\)

### `tokenType`

- Default: `Bearer`

 Authotization header type to be used in axios requests.

## Usage

To do a password based login by sending credentials in request body as a JSON object:

```js
this.$auth.loginWith('local', {
  data: {
    username: 'your_username',
    password: 'your_password'
  }
})
```

> 👉 There are more [common options](../options.md) available too.



