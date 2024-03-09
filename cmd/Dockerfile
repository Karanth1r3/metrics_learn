 #not optimal

FROM golang:1.21.5


WORKDIR /app

COPY go.mod ./
COPY go.sum ./

RUN go mod download && go mod verify

COPY main.go ./

RUN go build -o /cmd

FROM gcr.io/distroless/base-debian11

COPY --from=build /cmd /cmd

ENTRYPOINT [ "/cmd" ]