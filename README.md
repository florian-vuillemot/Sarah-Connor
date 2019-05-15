# Sarah Connor

## Objectifs

Provide multiples services based on docker and docker-compose. Services have to be open source.

## Services

- Website
- ERP
- Private Cloud for data sharing
- Email server
- System d'authentication like Active Directory
- File sharing

## Services providers

- Website: Wordpress. Well documented and 1 CMS around the word.
- ERP: Dolibarr. Active community.
- Private Cloud: Owncloud. Same that ERP.
- Email server: Postfix. Well documented and simple.
- AD: Openldap. Reference around the word.
- File sharing: Samba. Reference around the word.

## Docker-Compose

'Simple is better than complex'. A mandatory of excercice is to used open source component. So, we didn't rebuild the whell and used docker found on docker registry.

## Architecture

We choosed to create multiples docker-compose standalones. Each docker-compose can turn on different server and have to be configure on run time.
So each docker-compose has it's owned network totally segregade (by docker) from other networks. This is better for security and standalone living.

We add SSL on Wordpress thanks to a reverse proxy based on Nginx. Note: Certificated is auto signed.

## How to run

- Copy `.env.example` in .env
- Replace `.env` value by your values
- Run `docker-compose -f docker-compose-service up` (you can add multiple `-f docker-compose-service` before the `up`)
  - Ex: docker-compose -f docker-compose-dolibar.yml -f docker-compose-ldap.yml -f docker-compose-owncloud.yml -f docker-compose-samba.yml -f docker-compose-smtp.yml -f docker-compose-wordpress.yml up

