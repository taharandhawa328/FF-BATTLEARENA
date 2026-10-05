# Free hosting on alwaysdata

FF Battle Arena is a Node.js/Express app with a SQLite database and uploaded payment-proof images. alwaysdata's free offer supports Node.js and persistent account storage, so the database and uploads can survive app restarts. The free offer is limited to personal, ad-free use and has limited resources; do not use it for real-money transactions unless that use is permitted by the provider.

## 1. Create a free account

Sign up for the alwaysdata Free offer: <https://www.alwaysdata.com/en/register/?p=2012>. It includes an `account.alwaysdata.net` site address. The current free offer has 1 GB SSD storage and 256 MB RAM; check the provider's terms and limits before using it.

## 2. Select Node.js 22

In the alwaysdata dashboard, set the Node.js version to **22** under **Environment > Node.js** before installing dependencies.

## 3. Copy the app to the account

Use the account's SSH/web terminal and run:

```sh
mkdir -p ~/www
cd ~/www
git clone --branch arena/01a10abe-ff-battlearena https://github.com/taharandhawa328/FF-BATTLEARENA.git
cd FF-BATTLEARENA
npm ci
```

Keep the app directory under the account's home directory so its SQLite database and uploads are on the account's persistent storage.

## 4. Set the admin credentials privately

Create a `.env` file in `~/www/FF-BATTLEARENA` with your own values:

```dotenv
NODE_ENV=production
ADMIN_USERNAME=choose-your-admin-name
ADMIN_PASSWORD=use-a-long-unique-password
```

Do not commit `.env` or send its values in chat. The repository's `.gitignore` excludes it.

## 5. Create the Node.js site

In the alwaysdata dashboard:

1. Go to **Web > Sites > Add a site**.
2. Use your `account.alwaysdata.net` address, select **Node.js**, set the site path to `www/FF-BATTLEARENA`, and start it with `npm start` (or `node /home/ACCOUNT/www/FF-BATTLEARENA/server.js`, replacing `ACCOUNT` with your account name).
3. The site provides its own `IP`/`HOST` and `PORT`; the server reads these automatically.

When the site starts, verify `<your-address>/api/status`. The admin page is at `<your-address>/admin.html`.
