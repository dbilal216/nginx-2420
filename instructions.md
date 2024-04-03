# How to setup Nginx Server Block on Arch Linux

## Step 1: Instal Software

1. Connect to Arch Linux Server

    ```bash
    ssh username@your_server_ip
    ```
    This connects to your droplet server 

3. Install Vim and Nginx:

    ```bash
    sudo pacman -S vim
    ```
    ```bash
    sudo pacman -S nginx
    ```
    This installs vim editor and nginx

## Step 2: Create Your Directory 

1. Create yoru directory to store the html file 

    ```bash
    sudo mkdir -p /web/html/nginx-2420
    ```
    This makes a new parent directory

## Step 3: Mkae Your Configuration File

1. Create a new configuration file for your server block

    ```bash
    sudo mkdir /etc/nginx/sites-available/nginx-2420
    ```
2. Open The COnfiguration File 
    
    ```bash
    sudo vim /etc/nginx/sites-available/nginx-2420
    ```
    This makes the directory and lets you edit the file in vim editor

3. Add configuration to the file:

    ```nginx
    server {
    listen 80;
    server_name _;

    root /web/html/nginx-2420;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
    ```

   For the server name, add in your Digital Ocean ssh key
   This makes the server in the file/directory specified 

## Step 4: Enable The Server Block

1. Make a symbolic link to your server block:

    ```bash
    sudo ln -s /etc/nginx/sites-available/nginx-2420
    ```
    This makes a symbolic link 

## Step 5: Test to make sure your file works 

1. Test your Nginx configuration:

    ```bash
    sudo nginx -t
    ```
    This tests it to see if it works

2. Reload your configuration file 

    ```bash
    sudo systemctl reload nginx
    ```
    This reloads the confiurgation file 

## Step 6: Make a Demo Document 

1. Create a demo HTML document inside the project directory:

    ```bash
    sudo mkdir /web/html/nginx-2420/index.html
    ```
    This creates a htl documnt 

2. Open your html file

    ```bash
    sudo mkdir /web/html/nginx-2420/index.html
    ```
    Press i for insert mode

    This opens a html file 

3. Add in yur html content

    <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>2420</title>
    <style>
        * {
            color: #db4b4b;
            background: #16161e;
        }
        body {
            display: flex;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
        }
        h1 {
            text-align: center;
            font-family: sans-serif;
        }
    </style>
</head>
<body>
    <h1>All your base are belong to us</h1>
</body>
</html>

## Step 8: Add to Git

1. Add it to your git repositry 

    ```bash
    sudo git init
    sudo git git add .
    sudo git commit 
    ```
    This adds it to your git repository 

## Step 9: Verify 

1. Access your server's IP address in a web browser to verify that the demo page is being served by Nginx.

## Finnished! 

Your done! You've setup nginx-2420" on your Arch Linux server!
