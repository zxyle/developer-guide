## 介绍
https://www.gnu.org/software/make/manual/make.html

## Makefile示例
```
# Cross compilation
compile:
	echo "Compiling for every OS and Platform"
	CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -o bin/main-linux-amd64 main.go
	CGO_ENABLED=0 GOOS=windows GOARCH=amd64 go build -o bin/main-windows-amd64 main.go
	CGO_ENABLED=0 GOOS=darwin GOARCH=amd64 go build -o bin/main-darwin-amd64 main.go

compose:
	docker-compose up

down:
	docker-compose down -v --rmi all
```

使用:
- make compile
- make compose
- make down