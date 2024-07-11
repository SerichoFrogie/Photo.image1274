pip install flask
from flask import Flask, request

app = Flask(__name__)

@app.route('/')
def home():
    # Získání IP adresy návštěvníka
    visitor_ip = request.remote_addr
    # Záznam IP adresy do konzole (nebo do souboru)
    print(f"Visitor IP: {visitor_ip}")
    return f"Your IP address is: {visitor_ip}"

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)

python app.py
from flask import Flask, request

app = Flask(__name__)

@app.route('/')
def home():
    # Získání IP adresy návštěvníka
    visitor_ip = request.remote_addr
    # Záznam IP adresy do souboru
    with open('ip_log.txt', 'a') as f:
        f.write(f"Visitor IP: {visitor_ip}\n")
    return f"Your IP address is: {visitor_ip}"

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
