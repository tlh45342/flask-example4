# INTRODUCTION

flask-example4 is a simple example flask app that uses authentication.  This is not designed to be pretty, or clever per-se.  This is not nearly finished. 

- learning Flask.
- kicking off your new project.
## PRESUMPTION

-- python is installed
- pip is instsalled
- guinicorn is installed

## INSTALLATION

```bash
cd /opt
git clone https://github.com/tlh45342/flask-example4.git
cd flask-example4
pip install -r requirements.txt
python server.py
```

## SIDEBAR: Notes for creating a service for Linux based distributions

I am putting my notes here now - because I will use them.  Consider these random notes used to implement the Flask APP as a service.

To create a service entry cd /etc/systemd/system
Create a file that looks something like is found in the following block.
As much as I hate assumptions - you will need to edit this to your tastes and for your environment.

```bash
cat <<EOF | sudo tee /etc/systemd/system/flask-example4.service
[Unit]
Description=flask-example4

[Service]
WorkingDirectory=/mnt/opt/flask-example4/
ExecStart=/usr/local/bin/gunicorn -b 0.0.0.0:8080 -w 4 server:app

[Install]
WantedBy=multi-user.target
EOF
```

The key commands for reference are: 

```bash
sudo systemctl daemon-reload
sudo systemctl start flask4.service
sudo systemctl restart flask4.service
sudo systemctl stop flask4.service
```

## STRUCTURE

    ├── README.md                   This document
    ├── requirements.txt            3rd libraries
    ├── server.py                   Wsgi app
    └── app
       ├── __init__.py
       ├── app.py                   Main App
       ├── user
       ├── api
       ├── static                   Static files
       │   ├── css
       └── templates                Jinja2 templates
           ├── errors
           ├── frontend
           └── index.html
 
## Version

(09/26/2021) - Not this is a shell template 

## LICENSE

flask-example4 is licensed under the Apache License, Version 2.0. See LICENSE for the full license text.

## ACKNOWLEDGEMENTS

Many thanks to Python, Flask and other good stacks.
Please note that this does include http://getskeleton.com/ skeleton.css and normal.css
