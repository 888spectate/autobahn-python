.PHONY: build

build:
	docker build \
		--build-arg BUILD_DATE=${BUILD_DATE} \
		--build-arg AUTOBAHN_PYTHON_VCS_REF=${AUTOBAHN_PYTHON_VCS_REF} \
		--build-arg AUTOBAHN_PYTHON_VERSION=${AUTOBAHN_PYTHON_VERSION} \
		-t crossbario/autobahn-python-aarch64:latest \
		-t crossbario/autobahn-python-aarch64:cpy3 \
		-t crossbario/autobahn-python-aarch64:cpy3-${AUTOBAHN_PYTHON_VERSION} \
		-f Dockerfile.cpy3 .

	docker build \
		--build-arg BUILD_DATE=${BUILD_DATE} \
		--build-arg AUTOBAHN_PYTHON_VCS_REF=${AUTOBAHN_PYTHON_VCS_REF} \
		--build-arg AUTOBAHN_PYTHON_VERSION=${AUTOBAHN_PYTHON_VERSION} \
		-t crossbario/autobahn-python-aarch64:pypy3 \
		-t crossbario/autobahn-python-aarch64:pypy3-${AUTOBAHN_PYTHON_VERSION} \
		-f Dockerfile.pypy3 .

	# docker build \
	# 	--build-arg BUILD_DATE=${BUILD_DATE} \
	# 	--build-arg AUTOBAHN_PYTHON_VCS_REF=${AUTOBAHN_PYTHON_VCS_REF} \
	# 	--build-arg AUTOBAHN_PYTHON_VERSION=${AUTOBAHN_PYTHON_VERSION} \
	# 	-t crossbario/autobahn-python-aarch64:latest \
	# 	-t crossbario/autobahn-python-aarch64:cpy3-alpine \
	# 	-t crossbario/autobahn-python-aarch64:cpy3-alpine-${AUTOBAHN_PYTHON_VERSION} \
	# 	-f Dockerfile.cpy3-alpine .

	# docker build \
	# 	--build-arg BUILD_DATE=${BUILD_DATE} \
	# 	--build-arg AUTOBAHN_PYTHON_VCS_REF=${AUTOBAHN_PYTHON_VCS_REF} \
	# 	--build-arg AUTOBAHN_PYTHON_VERSION=${AUTOBAHN_PYTHON_VERSION} \
	# 	-t crossbario/autobahn-python-aarch64:cpy3-minimal-aio \
	# 	-t crossbario/autobahn-python-aarch64:cpy3-minimal-aio-${AUTOBAHN_PYTHON_VERSION} \
	# 	-f Dockerfile.cpy3-minimal-aio .

	# docker build \
	# 	--build-arg BUILD_DATE=${BUILD_DATE} \
	# 	--build-arg AUTOBAHN_PYTHON_VCS_REF=${AUTOBAHN_PYTHON_VCS_REF} \
	# 	--build-arg AUTOBAHN_PYTHON_VERSION=${AUTOBAHN_PYTHON_VERSION} \
	# 	-t crossbario/autobahn-python-aarch64:cpy3-minimal-tx \
	# 	-t crossbario/autobahn-python-aarch64:cpy3-minimal-tx-${AUTOBAHN_PYTHON_VERSION} \
	# 	-f Dockerfile.cpy3-minimal-tx .

version: os_version python_version autobahn_version

os_version:
	docker run -it --rm crossbario/autobahn-python-aarch64:cpy3 uname -a
	docker run -it --rm crossbario/autobahn-python-aarch64:pypy3 uname -a
	#docker run -it --rm crossbario/autobahn-python-aarch64:cpy3-alpine uname -a
	#docker run -it --rm crossbario/autobahn-python-aarch64:cpy3-minimal-aio uname -a
	#docker run -it --rm crossbario/autobahn-python-aarch64:cpy3-minimal-tx uname -a

python_version:
	docker run -it --rm crossbario/autobahn-python-aarch64:cpy3 python -V
	docker run -it --rm crossbario/autobahn-python-aarch64:pypy3 pypy3 -V
	#docker run -it --rm crossbario/autobahn-python-aarch64:cpy3-alpine python -V
	#docker run -it --rm crossbario/autobahn-python-aarch64:cpy3-minimal-aio python -V
	#docker run -it --rm crossbario/autobahn-python-aarch64:cpy3-minimal-tx python -V

autobahn_version:
	docker run -it --rm crossbario/autobahn-python-aarch64:cpy3 python -c "import autobahn; print('running autobahn-{}'.format(autobahn.__version__))"
	docker run -it --rm crossbario/autobahn-python-aarch64:pypy3 pypy3 -c "import autobahn; print('running autobahn-{}'.format(autobahn.__version__))"
	#docker run -it --rm crossbario/autobahn-python-aarch64:cpy3-alpine python -c "import autobahn; print('running autobahn-{}'.format(autobahn.__version__))"
	#docker run -it --rm crossbario/autobahn-python-aarch64:cpy3-minimal-aio python -c "import autobahn; print('running autobahn-{}'.format(autobahn.__version__))"
	#docker run -it --rm crossbario/autobahn-python-aarch64:cpy3-minimal-tx python -c "import autobahn; print('running autobahn-{}'.format(autobahn.__version__))"

test: test_cpy3 test_pypy3 test_cpy3_alpine test_cpy3_minimal_aio test_cpy3_minimal_tx

test_cpy3:
	docker run -it --rm --link crossbar crossbario/autobahn-python-aarch64:cpy3

test_pypy3:
	docker run -it --rm --link crossbar crossbario/autobahn-python-aarch64:pypy3

test_cpy3_alpine:
	docker run -it --rm --link crossbar crossbario/autobahn-python-aarch64:cpy3-alpine

test_cpy3_minimal_aio:
	docker run -it --rm --link crossbar crossbario/autobahn-python-aarch64:cpy3-minimal-aio

test_cpy3_minimal_tx:
	docker run -it --rm --link crossbar crossbario/autobahn-python-aarch64:cpy3-minimal-tx

publish:
	docker push crossbario/autobahn-python-aarch64:latest
	docker push crossbario/autobahn-python-aarch64:cpy3
	docker push crossbario/autobahn-python-aarch64:cpy3-${AUTOBAHN_PYTHON_VERSION}
	docker push crossbario/autobahn-python-aarch64:pypy3
	docker push crossbario/autobahn-python-aarch64:pypy3-${AUTOBAHN_PYTHON_VERSION}
	#docker push crossbario/autobahn-python-aarch64:cpy3-alpine
	#docker push crossbario/autobahn-python-aarch64:cpy3-alpine-${AUTOBAHN_PYTHON_VERSION}
#	docker push crossbario/autobahn-python-aarch64:cpy3-minimal-aio
#	docker push crossbario/autobahn-python-aarch64:cpy3-minimal-aio-${AUTOBAHN_PYTHON_VERSION}
#	docker push crossbario/autobahn-python-aarch64:cpy3-minimal-tx
#	docker push crossbario/autobahn-python-aarch64:cpy3-minimal-tx-${AUTOBAHN_PYTHON_VERSION}

list:
	-docker images crossbario/autobahn-python-aarch64:*

clean:
	./removeall.sh

qemu_deps:
	mkdir -p ./.qemu
	cp /usr/bin/qemu-aarch64-static ./.qemu
