 #not optimal

FROM golang:1.21.5 AS build-stage


WORKDIR /app

COPY go.mod ./
COPY go.sum ./

RUN go mod download && go mod verify

COPY main.go ./

RUN CGO_ENABLED=0 GOOS=linux go build -o /cmd

FROM gcr.io/distroless/base-debian11 AS build-release-stage

WORKDIR /

COPY --from=build-stage /cmd /cmd

ENTRYPOINT [ "/cmd" ]