FROM node:20-alpine
WORKDIR /app
RUN apk add --no-cache openssl
COPY package*.json ./
RUN npm install --omit=dev

COPY . .
RUN npx prisma generate 
EXPOSE 3000
CMD ["sh", "-c", "npx prisma db push && npm start"]
