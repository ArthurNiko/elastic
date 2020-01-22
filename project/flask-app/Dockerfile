FROM alpine AS Builder
WORKDIR /app
RUN apk add --update \
    nodejs \
    nodejs-npm
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

FROM alpine
WORKDIR /app
RUN apk add python \
    py-pip 
COPY --from=Builder /app .
COPY requirements.txt .
RUN pip install -r requirements.txt
ENTRYPOINT [ "python" ] 
CMD [ "app.py" ]