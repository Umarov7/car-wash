CURRENT_DIR=$(shell pwd)
DBURL := postgres://postgres:root@localhost:5432/car_wash_auth?sslmode=disable

run:
	go run cmd/main.go
swag-gen:
	~/go/bin/swag init -g ./api/router.go -o api/docs
proto-gen:
	./scripts/gen-proto.sh ${CURRENT_DIR}

mig-up:
	migrate -path migrations -database '${DBURL}' -verbose up

mig-down:
	migrate -path migrations -database '${DBURL}' -verbose down

mig-force:
	migrate -path migrations -database '${DBURL}' -verbose force 2

mig-cr:
	migrate create -ext sql -dir migrations -seq ${1}_${2}_${3}