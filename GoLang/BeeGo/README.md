# Installing Beego
    go mod init
    go get github.com/beego/beego/v2@v2.0.0

Create file, exapmle "index.go" with: 

    package main

    import "github.com/beego/beego/v2/server/web"

    func main() {
        web.Run()
    }

Build and run

    go build index.go
    ./index

# Installing BeeTool
    go get github.com/beego/bee

Write <b>bee</b> in you console

Command <b>bee</b> has:

    new         create an application base on beego framework
    run         run the app which can hot compile
    pack        compress an beego project
    api         create an api application base on beego framework
    router      auto-generate routers for the app controllers
    bale        packs non-Go files to Go source files

Command for start project:

    bee run

or 

    go build index.go
    ./index

Полезности

	gorilla / mux — мощный URL-маршрутизатор и диспетчер. Мы будем использовать этот пакет для сопоставления путей URL с их обработчиками.
	jinzhu / gorm — отличная ORM-библиотека для Golang. Мы используем этот пакет, чтобы взаимодействовать с базой данных.
	dgrijalva / jwt-go — используется для подписи и проверки токенов JWT.
	joho / godotenv — используется для загрузки файлов .env в проект.
