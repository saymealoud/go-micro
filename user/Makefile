
GOPATH:=$(shell go env GOPATH)
.PHONY: proto
proto:
	sudo docker run --rm -v $(shell pwd):$(shell pwd) -w $(shell pwd) -e ICODE=CF388DF1EF1C5EBE cap1573/cap-protoc -I ./ --go_out=./ --micro_out=./  ./proto/user/*.proto
	
.PHONY: build
build:
	CGO_ENABLED=0 GOOS=linux GOARCH=arm64 go build -o user *.go

.PHONY: test
test:
	go test -v ./... -cover

.PHONY: dockerBuild
dockerBuild:
	sudo docker build -t user:latest .
