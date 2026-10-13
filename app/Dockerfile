# Stage 1: Build & Prune
FROM node:22-alpine AS builder
WORKDIR /app

COPY package*.json ./
RUN npm ci

COPY . .
# package.json に build コマンドがあれば実行、なければスキップ
RUN if npm run | grep -q " build$"; then npm run build; fi
RUN npm prune --production
RUN mkdir -p /app/node_modules

# Stage 2: Production Runner
FROM node:22-alpine AS runner
WORKDIR /app

ENV NODE_ENV=production
USER node

COPY --chown=node:node --from=builder /app/node_modules ./node_modules
COPY --chown=node:node --from=builder /app/package.json ./package.json
COPY --chown=node:node --from=builder /app ./

EXPOSE 3000
CMD ["npm", "start"]
