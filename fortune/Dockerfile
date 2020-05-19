FROM node:latest

ENV APP_ROOT=/app APP_PORT=3000

# Creae APP_ROOT and cd in
WORKDIR ${APP_ROOT}

# Copy the files and directory into image
ADD main.js .
ADD package.json .
ADD package-lock.json .

ADD public public
ADD views views

# Install the dependecies
RUN npm install

# Health check
HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \
    CMD curl -s -f http://localhost:${APP_PORT}/health || exit 1

# Tell what port to use
EXPOSE ${APP_PORT}

ENTRYPOINT ["node", "main.js"]

# CMD ["${APP_PORT}"]