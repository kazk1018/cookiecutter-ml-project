FROM tensorflow/tensorflow:latest-py3

ENV LC_ALL=C.UTF-8 \
    LANG=C.UTF-8 \
    WORKON_HOME=/venvs

WORKDIR /work

COPY Pipfile Pipfile.lock /work/

RUN pip install pipenv && pipenv install

ENTRYPOINT ["/bin/bash"]
