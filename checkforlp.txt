import json
import smtplib
import time
import urllib.request
import requests
import os
from twilio.rest import Client
from datetime import datetime
from bs4 import BeautifulSoup




url = 'https://www.iam8bit.com/collections/vinyl/products/outer-wilds-2xlp?_pos=2&_sid=14cec3801&_ss=r'
phrase = 'COMING SOON'
log = ""

account_sid = "ACa8972f3b74721ee5642d333984de4ec1"
auth_token = "763dcce08c06b535c5976523b57d6a56"
while True:
    def check_availability(url, phrase):
        try:
            page = requests.get(url)
            soup = BeautifulSoup(page.content, "html.parser")

            child_soup = soup.find_all('COMING SOON')

            if phrase in soup.text:
                return False
            return True
        except:
            print("Error parsing the website ")

    def main():
       
        print("Starting App")

        available = check_availability(url, phrase)
        
        clickMe = 'https://www.iam8bit.com/collections/vinyl/products/outer-wilds-2xlp?_pos=2&_sid=14cec3801&_ss=r'    
            
        if available:

            print("Sending Text")
            client = Client(account_sid, auth_token)
            message = client.messages.create(
            body="Check for LP!!!",
            from_="+18884955639",
            to="+17738700279"
            )

    main()     