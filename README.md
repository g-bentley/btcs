# btcs

## Docker Compose for BrewTroller Command Center (btcs)

### Software

- Nginx 1.11
- PHP 5.6-FPM
  - libraries used are a work in progress
  - Composer
- MySQL 5.6
- Nodejs + NPM

### Install

1. Install [Docker](https://www.docker.com/). Native versions are recommended.

2. Get the source
   ```
   git clone https://github.com/g-bentley/btcs/btcs.git
   cd btcs
   ```

3. Shut down any local web server bound to localhost port 80.

4. Download web applications to app/ and set docker-compose volumes to map to desired locations.

5. Create and start containers

   ```
   docker-compose up -d
   ```


6. Open [http://localhost/main/](http://localhost/main/)
