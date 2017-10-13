# bridgewell docker makefile template

workdir = $(shell pwd)

project = fen_web
tag = ${project}
name = ${project}

flag = -p 5000:5000 -v /etc/localtime:/etc/localtime
repo = 192.168.65.149:5000

dev_dir = /${project}
bashflag = -v ${workdir}/app:${dev_dir} -w ${dev_dir}


all: build

build:
	docker build -t ${tag} -t ${repo}/${tag} .

# http://stackoverflow.com/questions/6273608/how-to-pass-argument-to-makefile-from-command-line
# http://stackoverflow.com/questions/2214575/passing-arguments-to-make-run
run: kill
	docker run -d ${flag} --name ${name} ${tag} ${ARGS}

enter:
	docker exec -it ${name} /bin/bash

runbash:
	docker run ${bashflag} ${flag} --rm --name ${name} --entrypoint="/bin/bash" -it ${tag}

kill:
	docker rm -f ${name}

pull:
	docker pull ${repo}/${tag}

push:
	docker push ${repo}/${tag}
