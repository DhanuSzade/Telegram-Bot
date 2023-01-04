# Telegram-Bot
# INSTRUCTIONS
STEP 1: Telegram Group In which you will send messages
STEP 2: Telegram BOT & Add Bot in this Group 
STEP 3: Chat ID : <Chat_ID> (used the message on bhot group - /my_id @*********)
STEP 4: TOKEN - <Token>       
STEP 5: https://api.telegram.org/bot<TOKEN>/getUpdates 
STEP 6: https://api.telegram.org/bot<Token>/sendMessage?chat_id=<Chat_ID>&text="*******"
 
 # FOR MESSAGE
 import telegram.ext

# with open ("C:\Users\HP\Documents\TOKEN.txt",'r') as f:
#  TOKEN = f.read()
    
def start(update, context):
    update.message.reply_text("Hello! Welcome To Hixaa_Bot!")
    
def help(update, context):
    update.message.reply_text("""
    The following commands are available:
    
    /start -> Welcome Message
    /help -> This Message
    /content -> We Provide Internships
    /contact -> Information About Contact
    """)
    
    
def content(update, context):
    update.message.reply_text("We are Provided Internships!")
    
def contact(update, context):
    update.message.reply_text("You can Contact with us!")
    
def handler_message(update, context):
    update.message.reply_text(f"You said {update.message.text}")
    
updater = telegram.ext.Updater('<TOKEN>', use_context=True)
disp = updater.dispatcher

disp.add_handler(telegram.ext.CommandHandler("start", start))
disp.add_handler(telegram.ext.CommandHandler("help", help))
disp.add_handler(telegram.ext.CommandHandler("content", content))
disp.add_handler(telegram.ext.CommandHandler("contact", contact))

disp.add_handler(telegram.ext.MessageHandler(telegram.ext.Filters.text, handler_message))

updater.start_polling()
updater.idle()

# FOR SENDING MESSAGE
import requests 
import time

companies = ['Hixaa is a custom Indusrial technology',
             'Headquarter is in Nagpur',
             '20+ employee in last year',
             'Best company for Freshers',
             'Work on AI/ML',
             'Work on Web Development']
for company in companies:

    base_url ='https://api.telegram.org/bot<TOKEN>/sendMessage?chat_id=<CHAT_ID>&text="{}"'.format(company)
    requests.get(base_url)
    time.sleep(2)
    
# FOR SINGLE IMAGE
import requests

files ={'photo':open('D:\Person without jacket.jpg','rb')}

resp = requests.post('https://api.telegram.org/bot<TOKEN>/sendPhoto?chat_id=<CHAT_ID>&caption=This Worker without Jacket ',files=files)
print(resp.status_code)

# FOR MULTIPLE IMAGE
import requests
import time

base_url = "https://api.telegram.org/bot<TOKEN>/sendPhoto"

urls = [
        "https://unsplash.com/photos/tZw3fcjUIpM/download?ixid=MnwxMjA3fDB8MXxzZWFyY2h8Mnx8d29ya2VyfGVufDB8fHx8MTY3Mjc0ODkyMg&force=true",
        "https://unsplash.com/photos/wpvEMgFV4w0/download?ixid=MnwxMjA3fDB8MXxzZWFyY2h8MTR8fHdvcmtlcnxlbnwwfHx8fDE2NzI3NDg5MjI&force=true",
        "https://unsplash.com/photos/_2AlIm-F6pw/download?ixid=MnwxMjA3fDB8MXxzZWFyY2h8MjB8fHdvcmtlcnxlbnwwfHx8fDE2NzI3NDg5MjI&force=true"
        
]

for url in urls:
    time.sleep(5)  
    parameters = {
      "chat_id" : "<CHAT_ID>",
      "photo" : url,
      "caption" : "These Worker work without Safety Jacket"
  }
    resp = requests.get(base_url, data = parameters)
    print(resp.text)
