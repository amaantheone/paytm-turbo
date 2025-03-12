- Clone the repo

```jsx
https://github.com/amaantheone/paytm-turbo.git
```

- npm install
- Run postgres either locally or on the cloud

```jsx
docker run  -e POSTGRES_PASSWORD=mysecretpassword -d -p 5432:5432 postgres
```

- Copy over all .env.example files to .env
- Update .env files everywhere with the right db url
- Go to `packages/db`
    - npx prisma migrate dev
    - npx prisma db seed
- Go to `apps/user-app` , run `npm run dev`
- Try logging in using phone - 1111111111 , password - alice (See `seed.ts`)
- after logging in, try transfering some amount from a bank(hdfc)
  
- Open a new terminal
- Go to `packages/db`
  - npx prisma studio
  - go to onRampTransactions table, see the token, userId, and amount. Keep this tab open

- Open a new terminal
- Go to apps/bank-webhook
    - npm run dev
- to update it on the UI, do a post request to `http://localhost:3003/hdfcWebhook`
  - also send the body with the token, user_identifier, and amount you got from prisma studio
