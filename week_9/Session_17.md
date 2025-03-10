# Week 9: Deployment & Optimization

## Session 17: Deploying Node.js App on VPS

### Topics Covered:
- Deploying a Node.js application on a VPS (Hostinger, DigitalOcean, etc.)
- Using PM2 for process management
- Setting up Nginx as a reverse proxy
- Connecting MongoDB Atlas to a deployed Node.js app

### Steps to Deploy Node.js on VPS:
1. **Set Up VPS**
   - Choose a VPS provider (Hostinger, DigitalOcean, AWS, etc.)
   - Set up SSH access to the server

2. **Install Node.js and NPM**
   - Run:
     ```sh
     sudo apt update
     sudo apt install nodejs npm
     ```
   - Verify installation:
     ```sh
     node -v
     npm -v
     ```

3. **Clone Your Project & Install Dependencies**
   - Copy your project to the server:
     ```sh
     git clone https://github.com/your-repo.git
     cd your-repo
     npm install
     ```

4. **Run the Application with PM2**
   - Install PM2 globally:
     ```sh
     npm install -g pm2
     ```
   - Start the server:
     ```sh
     pm2 start server.js --name my-app
     ```
   - Save process list:
     ```sh
     pm2 save
     pm2 startup
     ```

5. **Set Up Nginx as a Reverse Proxy**
   - Install Nginx:
     ```sh
     sudo apt install nginx
     ```
   - Configure Nginx:
     ```sh
     sudo nano /etc/nginx/sites-available/default
     ```
   - Add the following configuration:
     ```nginx
     server {
         listen 80;
         server_name yourdomain.com;

         location / {
             proxy_pass http://localhost:3000;
             proxy_http_version 1.1;
             proxy_set_header Upgrade $http_upgrade;
             proxy_set_header Connection 'upgrade';
             proxy_set_header Host $host;
             proxy_cache_bypass $http_upgrade;
         }
     }
     ```
   - Restart Nginx:
     ```sh
     sudo systemctl restart nginx
     ```

---
