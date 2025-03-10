
## Session 18: Deploying React App with CI/CD

### Topics Covered:
- Deploying a React app on Vercel / Netlify
- CI/CD pipeline setup using GitHub Actions
- Performance optimization techniques
- Security best practices

### Steps to Deploy React App:

1. **Build the React App**
   ```sh
   npm run build
   ```

2. **Deploy on Vercel**
   - Install Vercel CLI:
     ```sh
     npm install -g vercel
     ```
   - Deploy:
     ```sh
     vercel
     ```

3. **Deploy on Netlify**
   - Install Netlify CLI:
     ```sh
     npm install -g netlify-cli
     ```
   - Deploy:
     ```sh
     netlify deploy --prod
     ```

4. **Setting Up GitHub Actions for CI/CD**
   - Add `.github/workflows/deploy.yml` with the following content:
     ```yml
     name: Deploy React App
     on:
       push:
         branches:
           - main
     jobs:
       build-and-deploy:
         runs-on: ubuntu-latest
         steps:
           - name: Checkout code
             uses: actions/checkout@v2
           - name: Install dependencies
             run: npm install
           - name: Build project
             run: npm run build
           - name: Deploy to Vercel
             run: vercel --prod
     ```
   - Push to GitHub and the deployment will be triggered automatically.

5. **Performance Optimization Tips**
   - Use lazy loading for images and components.
   - Optimize bundle size using Webpack.
   - Enable gzip compression.

6. **Security Best Practices**
   - Use HTTPS for secure communication.
   - Store environment variables securely.
   - Validate user inputs to prevent XSS and SQL Injection.

---