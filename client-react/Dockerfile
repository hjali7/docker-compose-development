# syntax=docker/dockerfile:1.5
# escape= \

#build stage

ARG BASE_IMG_TAG=19.4-bullseye

FROM node:${BASE_IMG_TAG} AS build

WORKDIR /usr/src/app

COPY package*.json ./

RUN --mount=type=cache,target=/usr/src/app/.npm \
    npm set cache /usr/src/app/.npm && \
    npm ci

COPY . .

RUN npm run build

#release stage

FROM nginxinc/nginx-unprivileged:1.23-alpine-perl

COPY nginx.conf /etc/nginx/conf.d/default.conf

COPY --from=build usr/src/app/dist/ /user/share/nginx/html

EXPOSE 8080

LABEL author="alihaji"