FROM golang:1.20

# Define o diretório de trabalho
WORKDIR /go/src

# Configura variáveis de ambiente
ENV PATH="/go/bin:${PATH}"
ENV GO111MODULE=on
ENV CGO_ENABLED=1

# Instala dependências necessárias
RUN apt-get update && \
    apt-get install -y build-essential protobuf-compiler librdkafka-dev wget && \
    rm -rf /var/lib/apt/lists/*

# Instala as ferramentas Go necessárias
RUN go install google.golang.org/protobuf/cmd/protoc-gen-go@v1.27.1 && \
    go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@v1.1.0 && \
    go install github.com/spf13/cobra/cobra@v1.2.1

# Baixa e instala Evans
RUN wget https://github.com/ktr0731/evans/releases/download/0.9.1/evans_linux_amd64.tar.gz && \
    tar -xzvf evans_linux_amd64.tar.gz && \
    mv evans /usr/local/bin/ && rm -f evans_linux_amd64.tar.gz

# Mantém o contêiner em execução (ou substitua pelo comando da sua aplicação)
CMD ["tail", "-f", "/dev/null"]
