FROM node:18-alpine AS base

# Set the working directory in the container
WORKDIR /app

# Copy the package.json and package-lock.json files to the working directory
COPY package.json yarn.lock* package-lock.json* pnpm-lock.yaml* ./
# Install dependencies
RUN \
  if [ -f yarn.lock ]; then yarn --frozen-lockfile; \
  elif [ -f package-lock.json ]; then npm ci; \
  elif [ -f pnpm-lock.yaml ]; then corepack enable pnpm && pnpm i --frozen-lockfile; \
  else echo "Lockfile not found." && exit 1; \
  fi

# Copy the frontend files to the working directory
COPY . .

# Build the Next.js application
RUN npm run build

EXPOSE 3000

# Start the Next.js server
CMD ["npm", "start"]