FROM sharkone/cross-compiler:base
MAINTAINER Thomas Texier "sharkone@en-mousse.org"

ENV CROSS_TRIPLE x86_64-linux-gnu
ENV CROSS_ROOT /usr/${CROSS_TRIPLE}
ENV PATH ${PATH}:${CROSS_ROOT}/bin
ENV LD_LIBRARY_PATH ${CROSS_ROOT}/lib:${LD_LIBRARY_PATH}
ENV PKG_CONFIG_PATH ${CROSS_ROOT}/lib/pkgconfig:${PKG_CONFIG_PATH}

RUN mkdir -p ${CROSS_ROOT} && \
    cd /usr/bin && \
    ln -s ${CROSS_TRIPLE}-gcc ${CROSS_TRIPLE}-cc && \
    ln -s ${CROSS_TRIPLE}-g++ ${CROSS_TRIPLE}-c++ && \
    for i in strip objdump; do \
        ln -s ${i} ${CROSS_TRIPLE}-${i} ; \
    done && \
    for i in ranlib nm ar; do \
        ln -s ${CROSS_TRIPLE}-gcc-${i}-4.7 ${CROSS_TRIPLE}-${i} ; \
    done
