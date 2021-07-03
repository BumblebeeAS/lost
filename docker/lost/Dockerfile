ARG base_image=l3pcv/lost-base:latest
FROM $base_image
# Add Code  
ADD /docker/lost/entrypoint.sh /
ADD /docker/lost/pytest.sh /
ADD /docker/lost/nginx/ /code/docker/lost/nginx
ADD /backend/ /code/backend
ADD /frontend/ /code/frontend
ADD /docs/ /code/docs
WORKDIR /code/frontend/lost/src/components/pipeline
RUN npm ci
WORKDIR /code/frontend/lost
RUN npm ci
RUN npm run build
RUN echo "export PATH=$PATH:/code/backend/lost/cli" >> ~/.bashrc
RUN echo "conda activate lost" >> ~/.bashrc
