# Step 1: Install Node.js (if not already installed)
node -v  
npm -v   

# Step 2: Create a new React app using CRA
npx create-react-app my-react-app

# Step 3: Navigate into the project folder
cd my-react-app

# Step 4: Start the development server
npm start

# Step 5: Open the project in VS Code (optional)
code .

# Step 6: Install additional dependencies (if needed)
npm install react-router-dom  
npm install @mui/material @emotion/react @emotion/styled  

# Step 7: Build the project for production
npm run build

# Step 8: Deploy the React app (optional)
## Deploy to GitHub Pages
npm install gh-pages --save-dev
npm run deploy

## Deploy to Vercel
npm install -g vercel
vercel

## Deploy to Netlify
npm install -g netlify-cli
netlify deploy
