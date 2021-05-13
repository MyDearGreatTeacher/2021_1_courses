```
from flask import Flask
app = Flask(__name__)

from flask import request, abort
from linebot import  LineBotApi, WebhookHandler
from linebot.exceptions import InvalidSignatureError
from linebot.models import MessageEvent, TextMessage, TextSendMessage

line_bot_api = LineBotApi('你的 CHANNEL_ACCESS_TOKEN')
handler = WebhookHandler('你的 CHANNEL_SECRET')

@app.route("/callback", methods=['POST'])
def callback():
    signature = request.headers['X-Line-Signature']
    body = request.get_data(as_text=True)
    try:
        handler.handle(body, signature)
    except InvalidSignatureError:
        abort(400)
    return 'OK'

@handler.add(MessageEvent, message=TextMessage)
def handle_message(event):
    line_bot_api.reply_message(event.reply_token,TextSendMessage(text=event.message.text))

if __name__ == '__main__':
    app.run()
```
```
from flask import Flask
app = Flask(__name__)

from flask import request, abort
from linebot import  LineBotApi, WebhookHandler
from linebot.exceptions import InvalidSignatureError
from linebot.models import MessageEvent, TextMessage,TextSendMessage, ImageSendMessage, StickerSendMessage, LocationSendMessage, QuickReply, QuickReplyButton, MessageAction

line_bot_api = LineBotApi('你的 CHANNEL_ACCESS_TOKEN')
handler = WebhookHandler('你的 CHANNEL_SECRET')

@app.route("/callback", methods=['POST'])
def callback():
    signature = request.headers['X-Line-Signature']
    body = request.get_data(as_text=True)
    try:
        handler.handle(body, signature)
    except InvalidSignatureError:
        abort(400)
    return 'OK'

@handler.add(MessageEvent, message=TextMessage)
def handle_message(event):
    mtext = event.message.text
    if mtext == '@傳送文字':
        try:
            message = TextSendMessage(  
                text = "我是 Linebot，\n您好！"
            )
            line_bot_api.reply_message(event.reply_token,message)
        except:
            line_bot_api.reply_message(event.reply_token,TextSendMessage(text='發生錯誤！'))
        
    elif mtext == '@傳送圖片':
        try:
            message = ImageSendMessage(
                original_content_url = "https://i.imgur.com/4QfKuz1.png",
                preview_image_url = "https://i.imgur.com/4QfKuz1.png"
            )
            line_bot_api.reply_message(event.reply_token,message)
        except:
            line_bot_api.reply_message(event.reply_token,TextSendMessage(text='發生錯誤！'))

    elif mtext == '@傳送貼圖':
        try:
            message = StickerSendMessage(  #貼圖兩個id需查表
                package_id='1',  
                sticker_id='2'
            )
            line_bot_api.reply_message(event.reply_token, message)
        except:
            line_bot_api.reply_message(event.reply_token,TextSendMessage(text='發生錯誤！'))

    elif mtext == '@多項傳送':
        try:
            message = [  #串列
                StickerSendMessage(  #傳送貼圖
                    package_id='1',  
                    sticker_id='2'
                ),
                TextSendMessage(  #傳送文字
                    text = "這是 Pizza 圖片！"
                ),
                ImageSendMessage(  #傳送圖片
                    original_content_url = "https://i.imgur.com/4QfKuz1.png",
                    preview_image_url = "https://i.imgur.com/4QfKuz1.png"
                )
            ]
            line_bot_api.reply_message(event.reply_token,message)
        except:
            line_bot_api.reply_message(event.reply_token,TextSendMessage(text='發生錯誤！'))

    elif mtext == '@傳送位置':
        try:
            message = LocationSendMessage(
                title='101大樓',
                address='台北市信義路五段7號',
                latitude=25.034207,  #緯度
                longitude=121.564590  #經度
            )
            line_bot_api.reply_message(event.reply_token, message)
        except:
            line_bot_api.reply_message(event.reply_token,TextSendMessage(text='發生錯誤！'))

    if mtext == '@快速選單':
        try:
            message = TextSendMessage(
                text='請選擇最喜歡的程式語言',
                quick_reply=QuickReply(
                    items=[
                        QuickReplyButton(
                            action=MessageAction(label="Python", text="Python")
                        ),
                        QuickReplyButton(
                            action=MessageAction(label="Java", text="Java")
                        ),
                        QuickReplyButton(
                            action=MessageAction(label="C#", text="C#")
                        ),
                        QuickReplyButton(
                            action=MessageAction(label="Basic", text="Basic")
                        ),
                    ]
                )
            )
            line_bot_api.reply_message(event.reply_token,message)
        except:
            line_bot_api.reply_message(event.reply_token,TextSendMessage(text='發生錯誤！'))

if __name__ == '__main__':
    app.run()
```
```
from flask import Flask
app = Flask(__name__)

from flask import request, abort
from linebot import  LineBotApi, WebhookHandler
from linebot.exceptions import InvalidSignatureError
from linebot.models import MessageEvent, TextMessage, TextSendMessage, AudioSendMessage, VideoSendMessage

line_bot_api = LineBotApi('你的 CHANNEL_ACCESS_TOKEN')
handler = WebhookHandler('你的 CHANNEL_SECRET')

@app.route("/callback", methods=['POST'])
def callback():
    signature = request.headers['X-Line-Signature']
    body = request.get_data(as_text=True)
    try:
        handler.handle(body, signature)
    except InvalidSignatureError:
        abort(400)
    return 'OK'

baseurl = '你的NGROK網址/static/'  #靜態檔案網址

@handler.add(MessageEvent, message=TextMessage)
def handle_message(event):
    mtext = event.message.text
    if mtext == '@傳送聲音':
        try:
            message = AudioSendMessage(
                original_content_url=baseurl + 'mario.m4a',  #聲音檔置於static資料夾
                duration=20000  #聲音長度20秒
            )
            line_bot_api.reply_message(event.reply_token, message)
        except:
            line_bot_api.reply_message(event.reply_token,TextSendMessage(text='發生錯誤！'))

    elif mtext == '@傳送影片':
        try:
            message = VideoSendMessage(
                original_content_url=baseurl + 'robot.mp4',  #影片檔置於static資料夾
                preview_image_url=baseurl + 'robot.jpg'
            )
            line_bot_api.reply_message(event.reply_token, message)
        except:
            line_bot_api.reply_message(event.reply_token,TextSendMessage(text='發生錯誤！'))

if __name__ == '__main__':
    app.run()
```