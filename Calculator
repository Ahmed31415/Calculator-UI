from PyQt5.QtWidgets import *
import sys

class Win(QWidget):
    def __init__(self):
        super(Win,self).__init__()
        self.makeUI()
        self.Val=''
        self.operator = ''
        self.Ans=''

        self.textEdit = QLineEdit(self)
        self.textEdit.setText("")
        self.textEdit.setReadOnly(True)
        self.textEdit.setGeometry(50, 50, 400, 50)

        Count=0
        width = 80
        height = 60
        x = 50
        y = 100
        Nums=[1,2,3,4,5,6,7,8,9]
        for c in range(0, 3):
            for r in range(0, 3):
                Button = QPushButton(str(Nums[Count]), self)
                Button.setObjectName(str(Nums[Count]))
                Button.setGeometry(x, y, width, height)
                Button.clicked.connect(self.Click)
                x += width
                Count = Count + 1
            y += height
            x = 50

        self.Zero = QPushButton('0', self)
        self.Zero.clicked.connect(self.Click)
        self.Zero.setGeometry(130, 280, 80, 60)

        self.Dot = QPushButton('.', self)
        self.Dot.clicked.connect(self.Point)
        self.Dot.setGeometry(210, 280, 80, 60)

        self.Equals = QPushButton('=', self)
        self.Equals.clicked.connect(self.Equal)
        self.Equals.setGeometry(370,220,80,60)

        self.C= QPushButton('C', self)
        self.C.clicked.connect(self.Back)
        self.C.setGeometry(370, 160, 80, 60)

        # self.Neg = QPushButton('+/-', self)
        # # self.Neg.clicked.connect(self.Minus)
        # self.Neg.setGeometry(50, 280, 80, 60)

        self.AC = QPushButton('AC', self)
        self.AC.clicked.connect(self.Clear)
        self.AC.setGeometry(370, 100, 80, 60)

        x1=290
        y1=100
        count=0
        Operators=['/','-','+','*']
        for m in range(0,4):
            OpVar=QPushButton(Operators[count],self)
            OpVar.setObjectName(Operators[count])
            OpVar.setGeometry(x1,y1,width,height)
            OpVar.clicked.connect(self.Operator)
            OpVar.clicked.connect(self.Click)
            y1 += height
            count=count+1

    def Click(self):
            self.Button=self.sender().objectName()
            self.Val=self.Val+(self.Button)
            self.textEdit.setText(self.Val)

    def makeUI(self):
        self.setWindowTitle('Calculator')
        self.setGeometry(200, 50, 500, 400)

    def Point(self):
        self.Val=self.Val+'.'
        self.textEdit.setText(self.Val)

    def Clear(self):
        self.Val=''
        self.textEdit.setText(self.Val)

    def Back(self):
        self.Val = self.Val[:-1]
        self.textEdit.setText(self.Val)

    def Operator(self):
        self.operator = self.sender().objectName()
        self.textEdit.setText(self.Val)

    def Equal(self):
        self.Operator()

        Ops = []
        Numb=[]
        a = ""
        length = len(self.Val)
        CounT = 0
        for char in self.Val:
            if (char == "+") or (char == "-") or (char == "*") or (char == "/"):
                Ops.append(char)
                if a!='':
                    Numb.append(a)
                a = ""
            else:
                a = a + char
            CounT += 1
        if (CounT == length) and a!= "":
            Numb.append(a)

        print (Numb)
        print (Ops)
        if (len(Ops))>=(len(Numb)):
            print ("Syntax Error")
            self.textEdit.setText("Syntax Error")
            return


        Cnt=0
        TempOp=[]
        for z in Ops:
            try:
                if z == "/":
                    self.Ans=float(Numb[Cnt])/float(Numb[Cnt+1])
                    Numb[Cnt] = self.Ans
                    Numb.remove(Numb[Cnt + 1])
                    Cnt-=1
                elif z== "*":
                    self.Ans=float(Numb[Cnt])*float(Numb[Cnt+1])
                    Numb[Cnt] = self.Ans
                    Numb.remove(Numb[Cnt + 1])
                    Cnt-=1
                else:
                    TempOp.append(z)
            except:
                self.textEdit.setText("Syntax Error")

            Cnt+=1
        Ops=TempOp
        TempOp=[]
        print (Ops)
        for r in Ops:
            try:
                if r=="+":
                    self.Ans=float(Numb[0])+float(Numb[1])
                elif r=="-":
                    self.Ans=float(Numb[0])-float(Numb[1])
            except:
                self.textEdit.setText("Syntax Error")
            Numb[0]= self.Ans
            Numb.remove(Numb[1])

        self.textEdit.setText(str(Numb[0]))
        print (Numb)
        print (Ops)

app=QApplication(sys.argv)
calc=Win()
calc.show()
sys.exit(app.exec_())

