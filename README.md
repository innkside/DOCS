[![Innkside Logo](https://innkside.now.sh/logo.png)](https://innkside.now.sh)


# Innkside JavaScript Library (preview)

This is a preview of how will work the innkside javascript library **this library is not publised on npm yet**

## Features

  * Easy to use
  * Fast
  * Secure
  * Cheap
  * Descentralized
  
 ## Philosophy

  This tool is born from a real problem all developers and founders has faced when they want to implement a payment system.

  We want to fulfill a mission. **To make a tool really easy to implement and at the same time it helps the business grow.**  
  

### Initialize Client
This method will initialize the environment of the library to work with the rest of the methods, will be needed to provide an api key. You will be able to get one on the innkside dashboard.

```js
import innksideClient from 'innkside'

const API_KEY = '..apikey'

const innkside = innksideClient(API_KEY)
```


### Create user
This method will create user's wallet and keys, it will allow you to get needed keys to use rest of methods
```js
const user = innkside.createUser()

//response
/*
{
  id: 1,
  access_key: 'kaj3kshdfa_he8d3',
  wallet_address: 'lakje4jalkdsKLDSF9Lksdjk3245',
  created: true,
}
*/
```
We recommend to use this method when a user signup to your platform so both accounts will be created the one in your platform and the one innkside to deal with payments

**Make sure to save in your database the user's id and returned by innkside**



### Get user credentials
This methond will return the user's credentials needed to use the rest of methods

```js 
innkside.getCredentials(userId)

//reponse
/*
{
  id: 1,
  access_key: 'kaj3kshdfa_he8d3'
  wallet_address: 'lakje4jalkdsKLDSF9Lksdjk3245',
}
*/
```


### Exchange Coins
This method will make your users able to exchange fiat currency into your internal coin (you can call it as you want in the dashboard)

```js
const fiat = 50
const innksideId = // get it from getCredentials method
const wallet_address = //get it from getCredentials method

innkside.exchage(id, fiat, wallet_address)

//response
/*
{
  exchanged: true,
  fiat: 50,
  currency: US,
  yourCoinName: 50
}
*/
```

### Execute a transaction
This method will allow your users to make transactions inside your app with the coins they have exchanged, You can implement this method in different ways, for example: Your users can purchase assets inside your business application.

More interesting, if your app is an shared economy application, you can programatically execute different values transactions, so a percentage of the coins go to the service provider and the other one is yours.

```js
innkside.transact(id, value, sender, addressee ) //yo'll be able to use async await with all methods

/*
{
  executed: true,
  value: 50,
  ...
}
*/
```

