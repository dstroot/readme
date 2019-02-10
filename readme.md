# S3 and Cloudfront hosting

Hosting a Single Page App (SPA), built in a JavaScript framework such as Angular or React, is simple. For these apps, you don’t need a server  —  all you need is somewhere that will serve a set of static files, and all the website logic is done client-side by JavaScript. S3 buckets are perfect for this.

If you already have awscli installed and configured you are golden. If not that is a prerequisite.

Steps:

1. Open the `deploy.sh` file and make sure your project and bucket names make sense and are unique.
2. Run `deploy.sh`

Boom! You are done. You can update your SPA project's `package.json` file to perform the actual upload. See the **output** of the deploy script. Modify your scripts section like so:

```json
"scripts": {   
  "start": "react-scripts start",
  "build": "react-scripts build",
  "test": "react-scripts test",
  "eject": "react-scripts eject",
  "predeploy": "yarn build",
  "deploy": "aws s3 sync build/ s3://aws-s3-hosting-90278"
},
```

Then run `yarn deploy`. Pat yourself on the back. You just deployed your site.

### References

- [Single-Page Apps on AWS, Part 1](https://medium.com/@P_Lessing/single-page-apps-on-aws-part-1-hosting-a-website-on-s3-3c9871f126)
- [Single-Page Apps on AWS, Part 2](https://medium.com/@P_Lessing/single-page-apps-on-aws-part-2-deploying-a-compiled-frontend-33723e8f6814)
