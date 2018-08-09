.PHONY: help clean build build-cpu build-gpu container container-cpu container-gpu notebook
.DEFAULT_GOAL := help

export CONTAINER_IMAGE_NAME={{cookiecutter.container_name}}
export CONTAINER_NAME={{cookiecutter.project_name}}

help:
	@echo "help: commands (clean, build-{cpu/gpu}, docker-{cpu/gpu}, notebook)"

clean:	clean-container

clean-container:
	@docker image rm ${CONTAINER_IMAGE_NAME}

init:
	@pipenv install --dev

build:	build-cpu

build-cpu:
	@docker build -t ${CONTAINER_IMAGE_NAME} -f docker/Dockerfile .

build-gpu:
	@nvidia-docker build -t ${CONTAINER_IMAGE_NAME} -f docker/Dockerfile.gpu .

container:	container-cpu

container-cpu:
	@docker run -it --rm -v ${PWD}:/work --name ${CONTAINER_NAME} ${CONTAINER_IMAGE_NAME}

container-gpu:
	@nvidia-docker run -it --rm -v ${PWD}:/work --name ${CONTAINER_NAME} ${CONTAINER_IMAGE_NAME}

notebook:
	@pipenv run jupter notebook --notebook-dir notebooks
