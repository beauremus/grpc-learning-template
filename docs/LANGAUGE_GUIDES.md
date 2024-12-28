## Go Guide

1.  Install Go inside the container: `apt-get install -y golang`
2.  Install the gRPC Go library: `go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@latest`
3. Install the protoc-gen-go plugin: `go install google.golang.org/protobuf/cmd/protoc-gen-go@latest`
4.  Generate Go code: `protoc --go_out=. --go-grpc_out=. proto/service.proto`
5.  Create `server/server.go` and `client/client.go` (see example below).
6.  Run the server: `go run server/server.go`
7.  Run the client: `go run client/client.go`

**Example Go Server (`server/server.go`):**

```go
// ... (Import statements)

type server struct {
    pb.UnimplementedGreeterServer
}

func (s *server) SayHello(ctx context.Context, req *pb.HelloRequest) (*pb.HelloReply, error) {
    return &pb.HelloReply{Message: "Hello " + req.GetName()}, nil
}

func main() {
        // ... (gRPC server setup)
}
