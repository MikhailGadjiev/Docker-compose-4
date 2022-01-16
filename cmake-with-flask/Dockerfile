FROM alpine:3.6

RUN apk add --no-cache -q -f git cmake make g++ python3 py3-pip
 

RUN pip3 install --upgrade pip
 

RUN git clone -q https://github.com/google/googletest.git /googletest \

  && mkdir -p /googletest/build \

  && cd /googletest/build \

  && cmake .. && make && make install \

  && cd / && rm -rf /googletest\

  && pip install --upgrade pip


RUN adduser -S techproguser -G root -h /home/techproguser
 

USER techproguser
 

WORKDIR /home/techproguser/cmake_with_flask


COPY . .
 

USER root


RUN cmake ../cmake_with_flask && \

    cmake --build . && \

    pip3 install Flask


USER techproguser


EXPOSE 5000

CMD ./bin/C && python3 app.py --host=0.0.0.0 --port=5000
