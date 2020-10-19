# gitea-hydra-integration

go to master branch,

relevant files are hydrastart.yml , hydrastart-postgres.yml and following commands need to be run


    
    docker-compose -f hydrastart.yml \
    -f hydrastart-postgres.yml \
    up --build 
    
    hydra clients create \
    --endpoint http://127.0.0.1:4445 \
    --id gitea-client \
    --secret secret \
    --grant-types authorization_code,refresh_token \
    --response-types code,id_token \
    --scope openid,offline \
    --callbacks http://127.0.0.1:8000/user/oauth2/ORY_Hydra/callback \
    --token-endpoint-auth-method client_secret_post
    
    docker-compose -f hydrastart.yml exec hydra \
    hydra clients create \
    --endpoint http://127.0.0.1:4445 \
    --id gitea-client \
    --secret secret \
    --grant-types authorization_code,refresh_token \
    --response-types code,id_token \
    --scope openid,offline \
    --callbacks http://127.0.0.1:8000/user/oauth2/ORY_Hydra/callback \
    --token-endpoint-auth-method client_secret_post
    
also you can find detailed doc in /doc/doc/guides/gitea-hydra-integration.mdx
