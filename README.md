# Hello Rust

Sample Rust application with Hello world endpoint on root path.

## Podman / Docker

Could be build via Containerfile:

```
FROM rust:1.65 AS builder
COPY . .
RUN cargo build --release

FROM debian:buster-slim
COPY --from=builder ./target/release/hello-rust ./app/hello-rust

EXPOSE 8080

CMD ["/app/hello-rust"]
```