FROM node:16-alpine
WORKDIR /app

ARG APP_VERSION
ENV APP_VERSION $APP_VERSION

COPY package.json package-lock.json .
RUN npm ci
COPY . .
RUN npm run build

ENV NODE_ENV production
ENV NEXT_TELEMETRY_DISABLED 1
ENV PORT 3000

RUN addgroup --system --gid 10000 nodejs
RUN adduser --system --uid 10000 nextjs

USER nextjs

EXPOSE 3000

CMD ["npm", "run", "start"]