```
from flask import Flask
from flask_sqlalchemy import SQLAlchemy

app = Flask(__name__)
app.config['SQLALCHEMY_DATABASE_URI'] = 'postgresql://admin:123456@127.0.0.1:5432/testdb'
db = SQLAlchemy(app)

class students(db.Model):
   __tablename__ = 'students'
   sid = db.Column(db.Integer, primary_key = True)
   name = db.Column(db.String(50), nullable = False)
   tel = db.Column(db.String(50))
   addr = db.Column(db.String(200))
   email = db.Column(db.String(100))

   def __init__(self, name, tel, addr, email):
       self.name = name
       self.tel = tel
       self.addr = addr
       self.email = email

@app.route('/')
def index():
    db.create_all()
    return "資料庫連線成功！"

if __name__ == '__main__':
   app.run()
```
```
from flask import Flask
from flask_sqlalchemy import SQLAlchemy

app = Flask(__name__)
app.config['SQLALCHEMY_DATABASE_URI'] = 'postgresql://admin:123456@127.0.0.1:5432/testdb'
db = SQLAlchemy(app)

class students(db.Model):
   __tablename__ = 'students'
   sid = db.Column(db.Integer, primary_key = True)
   name = db.Column(db.String(50), nullable = False)
   tel = db.Column(db.String(50))
   addr = db.Column(db.String(200))
   email = db.Column(db.String(100))

   def __init__(self, name, tel, addr, email):
       self.name = name
       self.tel = tel
       self.addr = addr
       self.email = email

@app.route('/')
def index():
    db.create_all()
    return "資料庫連線成功！"

@app.route('/insert')
def insert():
    student = students('炭治郎','0911111111', '台北市信義路101號', 'tjl@test.com')
    db.session.add(student)
    db.session.commit()
    return "資料新增成功！"

@app.route('/insertall')
def insertall():
    datas = [students('彌豆子','0922222222','台北市南京東路50號','mdj@test.com'),
             students('伊之助','0933333333', '台北市北門路20號', 'yjj@test.com')]
    db.session.add_all(datas)
    db.session.commit()
    return "資料批次新增成功！"

if __name__ == '__main__':
   app.run(debug=True)
```
```
from flask import Flask
from flask_sqlalchemy import SQLAlchemy

app = Flask(__name__)
app.config['SQLALCHEMY_DATABASE_URI'] = 'postgresql://admin:123456@127.0.0.1:5432/testdb'
db = SQLAlchemy(app)

class students(db.Model):
   __tablename__ = 'students'
   sid = db.Column(db.Integer, primary_key = True)
   name = db.Column(db.String(50), nullable = False)
   tel = db.Column(db.String(50))
   addr = db.Column(db.String(200))
   email = db.Column(db.String(100))

   def __init__(self, name, tel, addr, email):
       self.name = name
       self.tel = tel
       self.addr = addr
       self.email = email

@app.route('/')
def index():
    db.create_all()
    return "資料庫連線成功！"

@app.route('/queryall')
def queryall():
    datas = students.query.all()
    msg = ""
    for student in datas:
        msg += f"{student.name}, {student.tel}, {student.addr}, {student.email}<br>"
    return msg

@app.route('/queryusr/<int:uid>')
def queryusr(uid):
    student = students.query.get(uid)
    return f"{student.name}<br>{student.tel}<br>{student.addr}<br>{student.email}"

@app.route('/queryname/<string:name>')
def queryfilter(name):
    student = students.query.filter_by(name=name).first()
    return f"{student.name}<br>{student.tel}<br>{student.addr}<br>{student.email}"

if __name__ == '__main__':
   app.run()
```
```
from flask import Flask
from flask_sqlalchemy import SQLAlchemy

app = Flask(__name__)
app.config['SQLALCHEMY_DATABASE_URI'] = 'postgresql://admin:123456@127.0.0.1:5432/testdb'
db = SQLAlchemy(app)

class students(db.Model):
   __tablename__ = 'students'
   sid = db.Column(db.Integer, primary_key = True)
   name = db.Column(db.String(50), nullable = False)
   tel = db.Column(db.String(50))
   addr = db.Column(db.String(200))
   email = db.Column(db.String(100))

   def __init__(self, name, tel, addr, email):
       self.name = name
       self.tel = tel
       self.addr = addr
       self.email = email

@app.route('/')
def index():
    db.create_all()
    return "資料庫連線成功！"

@app.route('/updateusr/<int:uid>')
def updateusr(uid):
    student = students.query.get(uid)
    student.name = student.name + "(已修改)"
    db.session.commit()
    return "資料修改成功！"

@app.route('/deleusr/<int:uid>')
def deleusr(uid):
    student = students.query.get(uid)
    db.session.delete(student)
    db.session.commit()
    return "資料刪除成功！"

if __name__ == '__main__':
   app.run()
```
```
from flask import Flask
from flask_sqlalchemy import SQLAlchemy

app = Flask(__name__)
app.config['SQLALCHEMY_DATABASE_URI'] = 'postgresql://admin:123456@127.0.0.1:5432/testdb'
db = SQLAlchemy(app)

@app.route('/')
def index():
    return "資料庫連線成功！"

@app.route('/setup')
def setup():
    sql = """
    CREATE TABLE students2 (
    sid serial NOT NULL,
    name character varying(50) NOT NULL,
    tel character varying(50),
    addr character varying(200),
    email character varying(100),
    PRIMARY KEY (sid))
    """
    db.engine.execute(sql)
    return "資料表建立成功！"

@app.route('/insert')
def insert():
    sql = """
    INSERT INTO students2 (name, tel, addr, email) VALUES('炭治郎', '0911111111', '台北市信義路101號', 'tjl@test.com');
    INSERT INTO students2 (name, tel, addr, email) VALUES('彌豆子', '0922222222', '台北市南京東路50號', 'mdj@test.com');
    INSERT INTO students2 (name, tel, addr, email) VALUES('伊之助', '0933333333', '台北市北門路20號', 'yjj@test.com');
    """
    db.engine.execute(sql)
    return "資料新增成功！"

@app.route('/query')
def query():
    sql = "SELECT * FROM students2 ORDER BY sid"
    students = db.engine.execute(sql)
    msg = ""
    for student in students:
        msg += f"{student['name']}, {student['tel']}, {student['addr']}, {student['email']}<br>"
    return msg

@app.route('/updateusr/<int:uid>')
def updateusr(uid):
    sql = "UPDATE students2 SET name = '炭之郎' WHERE sid = " + str(uid)
    db.engine.execute(sql)
    return "資料修改成功！"

@app.route('/deleusr/<int:uid>')
def deleusr(uid):
    sql = "DELETE FROM students2 WHERE sid = " + str(uid)
    db.engine.execute(sql)
    return "資料刪除成功！"

if __name__ == '__main__':
   app.run(debug=True)
```