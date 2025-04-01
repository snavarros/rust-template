# Etapa 1: Build con Rust
FROM rust:1.85.0 AS builder
WORKDIR /app

# Instalar dependencias necesarias para todos los entornos
RUN apt-get update && apt-get install -y libssl-dev pkg-config

# Copiar archivos de dependencias y compilarlas para optimizar caché
COPY ../Cargo.toml ../Cargo.lock ./
RUN mkdir src && echo "fn main() {}" > src/main.rs && cargo build --release

# Copiar el código fuente
COPY ../ .

# Etapa 2: Producción (solo copia binario compilado)
FROM debian:bullseye-slim AS runtime
WORKDIR /app

# Crear usuario seguro para ejecutar la app
RUN addgroup --system appgroup && adduser --system --group appuser
USER appuser

# Copiar solo el binario desde la imagen de construcción
COPY --from=builder /app/target/release/rust-template .

# Exponer puerto
EXPOSE 8080
CMD ["./rust-template"]

# Etapa 3: Desarrollo (instalar cargo-watch)
FROM builder AS dev
RUN cargo install cargo-watch
CMD ["cargo", "watch", "-x", "run"]