# Project: LAMP stack

Hosting Multiple Websites (LAMP) on Apache2 in an AWS EC2 Machine.

![Site 1](https://github.com/smartstore/SmartStoreNET/assets/49460005/cbbc41de-3c7b-464c-8081-e5d883a08cc0)

![Site 2](https://github.com/smartstore/SmartStoreNET/assets/49460005/7c543290-51de-4258-b8a5-ca38e60c808f)

**Setup Steps:**

1. **EC2 Login:**
   - Log in to your EC2 instance.

2. **Install Apache2:**
   ```bash
   sudo apt update
   sudo apt install apache2
3. **Modify the `ports.conf` File:**
   - Add the following line, add your desired port ( adding `8080` in this example):
     ```bash
     Listen 8080
     ```
   - Restart Apache2.
     ```bash
     sudo systemctl restart apache2
     ```

4. **Complete the Setup:**
   - Run the following commands to enable site configurations and restart Apache2:
     ```bash
     sudo a2ensite site1.conf
     sudo a2ensite site2.conf
     sudo systemctl restart apache2
     ```
5. **Apache server configuration files**
   - Move site1.conf and site2.conf files at "/etc/apache2/sites-available/"

6. **Web configuration files**
   - Place your mult-web configuration files in custom repository at "/var/www/html/"
     ```bash
     sudo mkdir site1 site2
     ```
     ```html
     <!-- /var/www/html/site1/index.html -->
               <!DOCTYPE html>
          <html lang="en">
          <head>
              <meta charset="UTF-8">
              <meta name="viewport" content="width=device-width, initial-scale=1.0">
              <title>Apache Hosted Server - Website 1</title>
              <style>
                  body {
                      font-family: 'Arial', sans-serif;
                      background-color: #f0f0f0;
                      margin: 0;
                      padding: 0;
                      display: flex;
                      flex-direction: column;
                      align-items: center;
                      justify-content: center;
                      height: 100vh;
                  }
          
                  h1 {
                      color: #333;
                      text-align: center;
                      margin-bottom: 20px;
                      animation: fadeIn 2s ease-in-out;
                  }
          
                  p {
                      color: #555;
                      text-align: center;
                      font-size: 18px;
                      margin-bottom: 40px;
                      animation: slideIn 2s ease-in-out;
                  }
          
                  @keyframes fadeIn {
                      from {
                          opacity: 0;
                      }
                      to {
                          opacity: 1;
                      }
                  }
          
                  @keyframes slideIn {
                      from {
                          transform: translateY(-20px);
                      }
                      to {
                          transform: translateY(0);
                      }
                  }
              </style>
          </head>
          <body>
              <h1>Welcome to Apache Hosted Server</h1>
              <p>This is Website Number 1</p>
          </body>
          </html>

     ```

     ```bash
     <!-- /var/www/html/site2/index.html -->
               <!DOCTYPE html>
          <html lang="en">
          <head>
              <meta charset="UTF-8">
              <meta name="viewport" content="width=device-width, initial-scale=1.0">
              <title>Apache Hosted Server - Website 2</title>
              <style>
                  body {
                      font-family: 'Verdana', sans-serif;
                      background-color: #e0e0e0;
                      margin: 0;
                      padding: 0;
                      display: flex;
                      flex-direction: column;
                      align-items: center;
                      justify-content: center;
                      height: 100vh;
                  }
          
                  h1 {
                      color: #0066cc;
                      text-align: center;
                      margin-bottom: 20px;
                      animation: fadeIn 2s ease-in-out;
                  }
          
                  p {
                      color: #009933;
                      text-align: center;
                      font-size: 18px;
                      margin-bottom: 40px;
                      animation: slideIn 2s ease-in-out;
                  }
          
                  @keyframes fadeIn {
                      from {
                          opacity: 0;
                      }
                      to {
                          opacity: 1;
                      }
                  }
          
                  @keyframes slideIn {
                      from {
                          transform: translateY(-20px);
                      }
                      to {
                          transform: translateY(0);
                      }
                  }
              </style>
          </head>
          <body>
              <h1>Welcome to Apache Hosted Server</h1>
              <p>This is Website Number 2</p>
          </body>
          </html>

     ```

7. **Disable Default Configuration:**
   - Run the following commands to enable site configurations and restart Apache2:
     ```bash
     sudo a2dissite 000-default.conf
     sudo systemctl reload apache2
     sudo a2ensite site1.conf
     sudo a2ensite site2.conf
     sudo systemctl reload apache2
     ```
8. **Permit necessary Permissions**
   - Run the following commands to enable permissions:
     ```bash
     sudo chown -R www-data:www-data /var/www/html/site1
     sudo chown -R www-data:www-data /var/www/html/site2
     ```
9. **Check outputs**
   - Run the following commands to check output on terminal or access your EC2 public IP combined with your dedicated port on web browser:
     ```bash
     curl http://127.0.0.1:80
     curl http://127.0.0.1:8080
     ```
     

     
