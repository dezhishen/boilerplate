FROM --platform=$BUILDPLATFORM alpine
ARG LINK
ARG TARGETPLATFORM
COPY ./setup.sh /setup.sh
RUN /setup.sh

FROM node:lts-alpine
RUN useradd -m koishi
USER koishi
COPY --from=0 /boilerplate.zip /boilerplate.zip
COPY ./entrypoint.sh /
RUN apk add --no-cache chromium nss freetype harfbuzz ca-certificates ttf-freefont font-noto-cjk
VOLUME ["/koishi"]
WORKDIR "/koishi"
ENTRYPOINT ["/entrypoint.sh"]
CMD ["yarn", "start"]
