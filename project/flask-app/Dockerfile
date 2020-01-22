FROM alpine
WORKDIR /app
RUN apk add --update \
    python \
    py-pip \
    nodejs \
    nodejs-npm
COPY package.json .
RUN npm install
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
RUN npm run build
ENTRYPOINT [ "python" ] 
CMD [ "app.py" ]