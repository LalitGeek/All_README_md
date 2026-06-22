# Check Node.js and npm
node -v
npm -v

# Create React App using Vite
npm create vite@latest my-react-app -- --template react

# Navigate to project
cd my-react-app

# Install dependencies
npm install

# Start development server
npm run dev

# Install React Router
npm install react-router-dom

# Install Axios
npm install axios

# Install Bootstrap
npm install bootstrap

# Install Tailwind CSS (Vite)
npm install tailwindcss @tailwindcss/vite

# Build for production
npm run build

# Preview production build
npm run preview

# Remove node_modules and reinstall dependencies
rm -rf node_modules package-lock.json
npm install

# Create React App (Alternative)
npx create-react-app my-app
cd my-app
npm start
