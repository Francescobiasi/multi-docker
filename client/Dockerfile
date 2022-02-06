#lanciamo i comandi per far generare i file di produzione 
FROM node:16-alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

#passiamo la configurazione creata da noi al container e prendiamo il contenuto generato dal servizio sopra all interno della cartella di nginx che lui usa per eseguire il codice
FROM nginx
EXPOSE 3000
COPY ./nginx/defaul.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html 