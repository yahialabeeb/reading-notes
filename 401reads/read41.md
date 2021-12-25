# Deploying Your Next.js App
## Deploy to Vercel
* The easiest way to deploy Next.js to production is to use the Vercel platform developed by the creators of Next.js.
### what is Vercel
Vercel is a serverless platform for static and hybrid applications built to integrate with your headless content, commerce, or database. We make it easy for frontend teams to develop, preview, and ship

### 1 Create a Vercel Account
First, go to https://vercel.com/signup to create a Vercel account. 

### 3 Import your nextjs-blog repository
1. import your nextjs-blog repository on Vercel.

2. You’ll need to Install Vercel for GitHub. You can give it access to All Repositories.
3. import nextjs-blog.

4. When it’s done, you’ll get deployment URLs. Click on one of the URLs and you should see the Next.js starter page live.

## Next.js and Vercel
When you deploy your Next.js app to Vercel, the following happens by default:

1. Pages that use Static Generation and assets (JS, CSS, images, fonts, etc) will automatically be served from the Vercel Edge Network, which is blazingly fast.
2. Pages that use Server-Side Rendering and API routes will automatically become isolated Serverless Functions. This allows page rendering and API requests to scale infinitely.

## Vercel has many more features, such as:

- Custom Domains: Once deployed on Vercel, you can assign a custom domain to your Next.js app. Take a look at our documentation here.
- Environment Variables: You can also set environment variables on Vercel. Take a look at our documentation here. You can then use those environment variables in your Next.js app.
- Automatic HTTPS: HTTPS is enabled by default (including custom domains) and doesn't require extra configuration. We auto-renew SSL certificates.

## Preview Deployment for Every Push
* You will see a comment by the vercel bot on the pull request page.


* When you have a pull request open, Vercel automatically creates a preview deployment for that branch on every push. The preview URL will always point to the latest preview deployment.

## Develop, Preview, Ship
We’ve just gone through the workflow we call DPS: Develop, Preview, and Ship.

1. Develop: We’ve written code in Next.js and used the Next.js development server running to take advantage of its hot reloading feature.
2. Preview: We’ve pushed changes to a branch on GitHub, and Vercel created a preview deployment that’s available via a URL. We can share this preview URL with others for feedback. In addition to doing code reviews, you can do deployment previews.
3. Ship: We’ve merged the pull request to main to ship to production.

## Other Hosting Options
In your own hosting provider, run the build script once, which builds the production application in the .next folder.
```bash
npm run build
```
After building, the start script starts a Node.js server that supports hybrid pages, serving both statically generated and server-side rendered pages, and API Routes.
```bash
npm run start
```
Tip: You can customize the start script in package.json to accept a PORT parameter by updating it as: 
```js
"start": "next start -p $PORT".```