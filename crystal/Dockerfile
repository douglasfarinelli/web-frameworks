FROM jrei/crystal-alpine

WORKDIR /usr/src/app

COPY . ./

RUN shards install
RUN shards build --production --release --no-debug --static

FROM alpine    
COPY --from=0 /usr/src/app/bin/server /usr/bin/app
{{#files}}
COPY --from=0 /usr/src/app/{{.}} /usr/bin/{{{.}}}
{{/files}}
WORKDIR /usr/bin
CMD ./app
