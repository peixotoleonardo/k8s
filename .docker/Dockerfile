FROM golang:1.21-alpine as build

WORKDIR /app

COPY . .

RUN go build -o server ./cmd/server.go

FROM golang:1.21-alpine as production

WORKDIR /app

COPY --from=build /app/server .

CMD [ "./server" ]

