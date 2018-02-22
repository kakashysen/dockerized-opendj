## Setup

To setup opendj you need to follow the next steps:

1. Clone the repo `git clone <github-repo>`
2. Go to directory `dockerized-opendj` 
3. Run `docker-compose build`
4. Run 
```
docker run --rm -it \
    -v $PWD/ldap/db:/opt/opendj/db:rw \
    -v $PWD/ldap/logs:/opt/opendj/logs:rw \
    -v $PWD/ldap/config:/opt/opendj/config:rw \
    --entrypoint bash \
    oberthur/docker-opendj:2.6.2 /opt/opendj/setup --cli \
    --ldapPort 389 --ldapsPort 636 --adminConnectorPort 4444 \
    --enableStartTLS --generateSelfSignedCertificate \
    --baseDN dc=example,dc=com \
    -h hostname \
    --rootUserPassword "password" \
    --acceptLicense --no-prompt
```
5. Run `docker-compose up`