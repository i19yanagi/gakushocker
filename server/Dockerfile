FROM rustlang/rust:nightly as build
WORKDIR /app
RUN apt-get update -y && apt-get upgrade -y

COPY ./server/Cargo.toml ./Cargo.toml
COPY ./server/Cargo.lock ./Cargo.lock
COPY ./server/src ./src

EXPOSE 8080
RUN cargo build --release

FROM gcr.io/distroless/cc

COPY --from=build /app/target/release/server .

CMD ["./server"]