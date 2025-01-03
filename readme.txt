Defsecone Vulnerable web app: This web app simulates multiple vulnerabilities such as :
1. JWT Attacks
2. Account take over
3. Injection flaws
4. Malicious file uploads
5. Command injection
6. Parameter tampering
7. Client side validation, etc.,

Have fun. The objective is attack and defense. First identify vulnerability and then patch it and check.

Installation:
sudo docker pull girivvveera/html_db:latest
sudo docker pull girivvveera/html_web:latest
sudo docker network create webnet


Start the web server:
sudo docker run -d --name web-container \
  -e MYSQL_HOST=db \
  -e MYSQL_USER=wp_user \
  -e MYSQL_PASSWORD=your_password \
  -e MYSQL_DATABASE=webserver \
  -p 8080:80 \
  --network webnet \
  girivvveera/html_web:latest

Start the database:
udo docker run -d --name db \           
  -e MYSQL_ROOT_PASSWORD=root_password \
  -e MYSQL_DATABASE=webserver \
  -e MYSQL_USER=wp_user \
  -e MYSQL_PASSWORD=your_password \
  -p 3306:3306 \
  --network webnet \
  girivvveera/html_db:latest
