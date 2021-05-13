```
from flask import Flask
app = Flask(__name__)

from flask import request, abort, render_template
from linebot import  LineBotApi, WebhookHandler
from linebot.exceptions import InvalidSignatureError
from linebot.models import MessageEvent, TextMessage, TextSendMessage, BubbleContainer, ImageComponent, BoxComponent, TextComponent, IconComponent, ButtonComponent, SeparatorComponent, FlexSendMessage, URIAction

line_bot_api = LineBotApi('你的 CHANNEL_ACCESS_TOKEN')
handler = WebhookHandler('你的 CHANNEL_SECRET')
liffid = '你的 LIFF ID'

#LIFF靜態頁面
@app.route('/page')
def page():
	return render_template('index.html', liffid = liffid)

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
    if mtext == '@彈性配置':
        sendFlex(event)

    elif mtext[:3] == '###' and len(mtext) > 3:
         manageForm(event, mtext)

def sendFlex(event):  #彈性配置
    try:
        bubble = BubbleContainer(
            direction='ltr',  #項目由左向右排列
            header=BoxComponent(  #標題
                layout='vertical',
                contents=[
                    TextComponent(text='冰火飲料', weight='bold', size='xxl'),
                ]
            ),
            hero=ImageComponent(  #主圖片
                url='https://i.imgur.com/3sBRh08.jpg',
                size='full',
                aspect_ratio='792:555',  #長寬比例
                aspect_mode='cover',
            ),
            body=BoxComponent(  #主要內容
                layout='vertical',
                contents=[
                    TextComponent(text='評價', size='md'),
                    BoxComponent(
                        layout='baseline',  #水平排列
                        margin='md',
                        contents=[
                            IconComponent(size='lg', url='https://i.imgur.com/GsWCrIx.png'),
                            TextComponent(text='25   ', size='sm', color='#999999', flex=0),
                            IconComponent(size='lg', url='https://i.imgur.com/sJPhtB3.png'),
                            TextComponent(text='14', size='sm', color='#999999', flex=0),
                        ]
                    ),
                    BoxComponent(
                        layout='vertical',
                        margin='lg',
                        contents=[
                            BoxComponent(
                                layout='baseline',
                                contents=[
                                    TextComponent(text='營業地址:', color='#aaaaaa', size='sm', flex=2),
                                    TextComponent(text='台北市信義路14號', color='#666666', size='sm', flex=5)
                                ],
                            ),
                            SeparatorComponent(color='#0000FF'),
                            BoxComponent(
                                layout='baseline',
                                contents=[
                                    TextComponent(text='營業時間:', color='#aaaaaa', size='sm', flex=2),
                                    TextComponent(text="10:00 - 23:00", color='#666666', size='sm', flex=5),
                                ],
                            ),
                        ],
                    ),
                    BoxComponent(  
                        layout='horizontal',
                        margin='xxl',
                        contents=[
                            ButtonComponent(
                                style='primary',
                                height='sm',
                                action=URIAction(label='電話聯絡', uri='tel:0987654321'),
                            ),
                            ButtonComponent(
                                style='secondary',
                                height='sm',
                                action=URIAction(label='查看網頁', uri="http://www.e-happy.com.tw")
                            )
                        ]
                    )
                ],
            ),
            footer=BoxComponent(  #底部版權宣告
                layout='vertical',
                contents=[
                    TextComponent(text='Copyright@ehappy studio 2019', color='#888888', size='sm', align='center'),
                ]
            ),
        )
        message = FlexSendMessage(alt_text="彈性配置範例", contents=bubble)
        line_bot_api.reply_message(event.reply_token,message)
    except:
        line_bot_api.reply_message(event.reply_token,TextSendMessage(text='發生錯誤！'))

def manageForm(event, mtext):
    try:
        flist = mtext[3:].split('/')
        text1 = '姓名：' + flist[0] + '\n'
        text1 += '日期：' + flist[1] + '\n'
        text1 += '包廂：' + flist[2]
        message = TextSendMessage(
            text = text1
        )
        line_bot_api.reply_message(event.reply_token,message)
    except:
        line_bot_api.reply_message(event.reply_token,TextSendMessage(text='發生錯誤！'))

if __name__ == '__main__':
    app.run(debug=True)
```
### templates\index.html
```
<!DOCTYPE html>
<html>
<head>
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>LIFF 表單測試</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.0.0/jquery.min.js"></script>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css">
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/js/bootstrap.min.js"></script>
</head>
<body>
    <div class="row" style="margin: 10px">
        <div class="col-12" style="margin: 10px">
            <label>姓名</label>
            <input type="text" id="name" class="form-control" />
            <br />
            <label>日期</label>
            <input type="date" id="datetime" value="" class="form-control" />
            <br />
            <label>包廂</label>
            <select id="sel_room" class="form-control">
                <option selected>生龍廳</option>
                <option>活虎廳</option>
                <option>美鳳廳</option>
                <option>帥凰廳</option>
                <option>不使用包廂</option>
            </select>
            <br />
            <button class="btn btn-success btn-block" id="sure">確定</button>
        </div>
    </div>

    <script src="https://static.line-scdn.net/liff/edge/2.1/sdk.js"></script>
    <script>
        function initializeLiff(myLiffId) {
            liff.init({liffId: myLiffId });
        }

	function pushMsg(pname, pdatatime, proom) {
		if (pname == '' || pdatatime == '' || proom == '') {  //資料檢查
			alert('每個項目都必須輸入！');
			return;
		}
		var msg = "###";  //回傳訊息字串
		msg = msg + pname + "/";
		msg = msg + pdatatime + "/";
		msg = msg + proom;
		liff.sendMessages([  //推播訊息
			{ type: 'text',
			  text: msg
			}
		])
			.then(() => {
				liff.closeWindow();  //關閉視窗
			});
	}

	$(document).ready(function () {
		initializeLiff('{{ liffid }}');  //接收傳遞的 liffid 參數
		$('#sure').click(function (e) {  //按下確定鈕
			pushMsg($('#name').val(), $('#datetime').val(), $('#sel_room').val());
		});
	});
    </script>
</body>
</html>
```