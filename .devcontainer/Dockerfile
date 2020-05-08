FROM ocaml/opam2:4.09

ENV SATYSFI_VERSION=0.0.4+dev2020.04.05
ENV SATYROGRAPHOS_VERSION=0.0.2.4

ENV DEBIAN_FRONTEND=noninteractive

RUN sudo apt-get update \
    && sudo apt-get install -y --no-install-recommends apt-utils 2>&1 \
    && sudo apt-get install -qq -yy m4 \
    && opam repository add satysfi-external https://github.com/gfngfn/satysfi-external-repo.git \
    && opam repository add satyrographos-repo https://github.com/na4zagin3/satyrographos-repo.git \
    && opam install satysfi.${SATYSFI_VERSION} satysfi-dist.${SATYSFI_VERSION} satyrographos.${SATYROGRAPHOS_VERSION} \
    && eval $(opam env) \
    && satyrographos install \
    && sudo apt-get autoremove -y \
    && sudo apt-get clean -y 

ENV HOME=/home/opam
ENV DEBIAN_FRONTEND=dialog