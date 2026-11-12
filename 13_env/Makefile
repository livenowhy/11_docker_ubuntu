all: push

TAG = jammy-env
PREFIX = crpi-8kvyt6flnal17nk5.cn-beijing.personal.cr.aliyuncs.com
IMAGE_NAME = liveno/ubuntu

container:
	docker build -t ${PREFIX}/${IMAGE_NAME}:${TAG} .

push: container
	docker push ${PREFIX}/${IMAGE_NAME}:${TAG}

clean:
	docker rmi -f $(PREFIX):$(TAG) || true
