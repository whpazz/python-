

import os


class StudentT(object):

    def __init__(self):
        self.student_list=[]
        self.student_dict={}


    #学生管理系统界面
    @staticmethod
    def jiemian():
        print("---------------------------")
        print("      学生管理系统 V1.0")
        print("                           ")
        print("      1:添加学生"            )
        print("      2:删除学生"            )
        print("      3:修改学生"            )
        print("      4:查询学生"            )
        print("      5:显示所有学生"         )
        print("      6:保存数据"            )
        print("      7:退出系统"            )
        print("                           ")
        print("---------------------------")


    #添加学生
    def add(self):
        name=input("请输入录入学生姓名:")
        cls=input("请输入学生班级:")
        age=input("请输入录入学生年龄:")
        phone=input("请输入录入学生手机号:")
        addr=input("请输入录入学生家庭住址:")

        self.student_dict={"name":name,"class":cls,"age":age,"phone":phone,"address":addr}

        self.student_list.append(self.student_dict)
        print()
        print("-----添加学生信息界面-----")
        print()
        print("姓名\t\t","班级\t\t","年龄\t\t","电话号\t\t","家庭住址\t\t")
        for student_dict_1 in self.student_list:
            print("%s\t\t%s\t\t%s\t\t%s\t\t%s" %(student_dict_1["name"],
                                                 student_dict_1["class"],
                                                 student_dict_1["age"],
                                                 student_dict_1["phone"],
                                                 student_dict_1["address"]))
        print()
        print("录入成功!")
        print()

    #删除学生
    def dele(self):
        name_del=input("请输入想要删除的学生姓名:")
        for student_dict_1 in self.student_list:
            if name_del in student_dict_1["name"]:
                self.student_list.remove(student_dict_1)
                print()
                print("删除%s信息成功!" % name_del)
                print()
                break
        else:
            print()
            print("您输入的学生姓名错误，请重新输入")
            print()
    #修改学生
    def xiugai(self):
        name_xiugai=input("请输入想要修改的学生姓名:")


        for student_dict_1 in self.student_list:

            if name_xiugai == student_dict_1["name"]:
                print()
                print("-----修改界面-----")
                print()
                print("姓名\t\t", "班级\t\t", "年龄\t\t", "电话号\t\t", "家庭住址\t\t")
                print("%s\t\t%s\t\t%s\t\t%s\t\t%s" %(student_dict_1["name"],
                                                     student_dict_1["class"],
                                                     student_dict_1["age"],
                                                     student_dict_1["phone"],
                                                     student_dict_1["address"]))
                #回车不修改

                student_dict_1["name"]=self.new_input(student_dict_1["name"],"请输入修改后的学生姓名[回车不修改]:")
                student_dict_1["class"]=self.new_input(student_dict_1["class"],"请输入修改后的学生班级[回车不修改]:")
                student_dict_1["age"]=self.new_input(student_dict_1["age"],"请输入修改后的学生年龄[回车不修改]:")
                student_dict_1["phone"]=self.new_input(student_dict_1["phone"],"请输入修改后的学生手机号[回车不修改]:")
                student_dict_1["address"]=self.new_input(student_dict_1["address"],"请输入修改后的学生家庭地址[回车不修改]:")
                print()
                print("修改成功!")
                print()
                break
        else:
            print()
            print("您输入的学生姓名错误，请重新输入")
            print()

    #查找学生
    def find(self):
        find_name=input("请输入需要查找的学生姓名:")
        for student_dict_1 in self.student_list:

            if find_name == student_dict_1["name"]:
                print()
                print("-----查询结果界面-----")
                print()
                print("姓名\t\t", "班级\t\t", "年龄\t\t", "电话号\t\t", "家庭住址\t\t")
                print("%s\t\t%s\t\t%s\t\t%s\t\t%s" % (student_dict_1["name"],
                                                      student_dict_1["class"],
                                                      student_dict_1["age"],
                                                      student_dict_1["phone"],
                                                      student_dict_1["address"]))
            else:
                print()
                print("-----查询结果界面-----")
                print()
                print("无此学生信息")

    #显示所有学生信息
    def showall(self):

        if len(self.student_list)>0:
            print()
            print("-----显示所有学生信息-----")
            print()
            print("姓名\t\t", "班级\t\t", "年龄\t\t", "电话号\t\t", "家庭住址\t\t")
            for student_dict_1 in self.student_list:

                print("%s\t\t%s\t\t%s\t\t%s\t\t%s" % (student_dict_1["name"],
                                                      student_dict_1["class"],
                                                      student_dict_1["age"],
                                                      student_dict_1["phone"],
                                                      student_dict_1["address"]))
        else:
            print()
            print("暂无数据！")
            print()
    #设置用户不输入内容返回原值，输入内容返回新内容
    def new_input(self,yuanzhi,message):
        self.input_str=input(message)

        if len(self.input_str)>0:
            return self.input_str
        else:
            return yuanzhi


    #保存数据至文件中
    def save_file(self):

        f = open("student2.txt", 'w', encoding='utf-8')
        f.write(str(self.student_list))
        f.close()
        print("数据保存至student1.txt文件成功！")


    #将数据读取至变量中
    def read_file(self):

         if os.path.exists('student2.txt'):
            f = open('student2.txt', 'r', encoding='utf-8')
            ret = f.read()

            self.student_list=eval(ret)
            f.close()
            print("数据读取成功!")
            ____________________________________________________________________________________________
            import student_tools


class Student(student_tools.StudentT):

    def __init__(self):
        self.user=['wangtaotao']
        self.pwd=['123456']
        student_tools.StudentT.__init__(self)

    #登录
    def denglu(self):
        users = input("请输入您的用户名:")
        pwds = input("请输入您的密码:")
        if users in self.user and pwds in self.pwd:
            self.student()
        else:
            print("账号或密码不正确，请重新输入")

    #注册
    def zhuce(self):
        users=input("请输入您要注册的用户名:")
        pwds=input("请输入您要注册的密码:")
        self.user.append(users)
        self.pwd.append(pwds)
        print()
        print("注册成功!")
        print()

    #登录界面
    def dljiemian(self):

        while True:
            print("---------------------------")
            print("    学生管理系统登陆界面 V1.0  ")
            print("                           ")
            print("        1:登   录           ")
            print("        2:注   册           ")
            print("        3:退   出           ")
            print("                           ")
            print("---------------------------")
            xx=input("请输入您的选择:")
            #1.登录
            if xx=='1':
                self.denglu()
            elif xx=='2':
            #2.注册
                self.zhuce()
            elif xx=='3':
            #3.退出
                print()
                print("成功退出!")
                print()
                break
            else:
                print("输入错误，请重新输入")


    #学生管理系统
    def student(self):
        # 调用student_tools模块中的读取文件函数
        super().read_file()
        while True:
            #调用student_tools模块中的界面函数
            super().jiemian()

            x=input("请输入您的选择:")
            #添加学生
            if x=='1':
                super().add()
            #删除学生
            elif x=='2':
                super().dele()
            #修改学生
            elif x=='3':
                super().xiugai()
            #查询学生
            elif x=='4':
                super().find()
            #显示所有学生
            elif x=='5':
                super().showall()
            #保存数据至文件中
            elif x=='6':
                super().save_file()
            #退出学生管理系统,返回上一层登录界面系统
            elif x=='7':
                print()
                print("成功退出学生管理系统!")
                break
            else:
                print()
                print("输入错误，请重新输入")
                print()

    #调用最先执行的登录界面函数
if __name__=='__main__':
    wtt=Student()
    wtt.dljiemian()
