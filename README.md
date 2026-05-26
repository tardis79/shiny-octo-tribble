# Vercel Connection Test

This is a tiny static project for confirming that your Vercel deployment and
domain connection are working.

## Files

- `index.html` is the page Vercel will serve.
- `vercel.json` keeps URLs clean and simple.
- `server.mjs` provides an optional local preview server with no dependencies.
- `package.json` adds optional local preview and Vercel CLI scripts.

## Import To Vercel

1. Put this folder in a Git repository.
2. Push it to GitHub, GitLab, or Bitbucket.
3. In Vercel, choose **Add New... > Project**.
4. Import the repository.
5. Keep the framework preset as **Other**.
6. Leave the build command empty.
7. Leave the output directory empty.
8. Deploy.

After deployment, open your `*.vercel.app` domain. You should see
`Connection OK`.

## HTTP On Vercel

Vercel does not serve production deployments over plain insecure HTTP. If you
visit:

```text
http://your-project.vercel.app
```

Vercel will automatically redirect it to:

```text
https://your-project.vercel.app
```

That means the site still opens when someone types `http://`, but the final URL
in the browser will be secure HTTPS.

You can test that redirect after deployment with:

```sh
curl -I http://your-project.vercel.app
```

You should see a redirect status such as `308` and a `Location` header pointing
to the HTTPS URL.

## Optional CLI Deploy

```sh
npm run deploy
```

For production:

```sh
npm run deploy:prod
```

## Local Preview

You can open `index.html` directly in a browser. If you prefer a local web
server, use:

```sh
npm start
```

Then visit:

```text
http://127.0.0.1:4173
```
