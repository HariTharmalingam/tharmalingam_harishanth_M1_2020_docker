FROM mongo

COPY auth.json /auth.json

CMD mongoimport --host mongodb --db docker --collection users --drop --type json --file ./auth.json --jsonArray