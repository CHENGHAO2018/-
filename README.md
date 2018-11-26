# -#include "stdafx.h"
#include "string.h"
#include "windows.h"
#include <string>
#include <fstream>
#include <iostream>
using namespace std;

const char *file = "C++4.txt";

class student {
public:
	int a;
	string name;
	double chinese;
	double math;
	double english;
	student *next;
	student(){};
	~student(){};

	void input(student *p) {
		cout << "请输入学生学号：" << endl;
		cin >> p->a;
		cout << "请输入学生姓名：" << endl;
		cin >> p->name;
		cout << "请输入语文成绩：" << endl;
		cin >> p->chinese;
		cout << "请输入数学成绩：" << endl;
		cin >> p->math;
		cout << "请输入英语成绩：" << endl;
		cin >> p->english;
		ofstream fout(file, ios::out | ios::app);
		fout << "学生学号：" << p->a << endl;
		fout << "学生姓名：" << p->name << endl;
		fout << "语文成绩：" << p->chinese << endl;
		fout << "数学成绩：" << p->math << endl;
		fout << "英语成绩：" << p->english << endl;
	}

	student *create() {
		int b, m = 0;
		student *head;
		student *p1, *p2;
		head = p1 = p2 = new student;
		cout << "请输入要输入学生信息的个数：" << endl;
		cin >> b;
		for (; b > 0; b--) {
			input(p1);
			p1 = new student;
			p2->next = p1;
			p2 = p1;
		}
		p2->next = NULL;
		return head;
	}

	student *del(student *p) {
		int b;
		student *p1, *p2, *p3;
		cout << "请输入要删除的学生学号：" << endl;
		cin >> b;
		p1 = p2 = p3 = p;
		if (p1->a==b) {
			p2 = p1->next;
			p = p2;
			delete p1;
		}
		else {
			for (; p1->a != b;) {
				p3 = p1;
				p1 = p2->next;
				p2 = p1;
			}
			p3->next = p1->next;
			delete p1, p2;
		}
		return p;
	}

	student *change(student *p) {
		int b;
		student *p1, *p2;
		p1 = p2 = p;
		cout << "请输入要更改的学生学号：" << endl;
		cin >> b;
		if(p->a==b){
			input(p);
			p->next = p1;
		}else{
			for (; p1->a != b;) {
				p1 = p2->next;
				p2 = p1;
			}
			input(p1);
			p1 = p2->next;
		}
		return p;
	}

	void xmcx(student *p) {
		string n;
		cout << "请输入要查询的学生姓名：" << endl;
		cin >> n;
		student *p1, *p2;
		p1 = p2 = p;
		if (p->next == NULL) {
			if (n == p->name) {
				cout << "学生学号：" << p->a << endl;
				cout << "学生姓名：" << p->name << endl;
				cout << "语文成绩：" << p->chinese << endl;
				cout << "数学成绩：" << p->math << endl;
				cout << "英语成绩：" << p->english << endl;
			}else {
				cout << "查无此人" << endl;
			}
		}else {
			for (; p1->next != NULL;) {
				if (n == p1->name) {
					cout << "学生学号：" << p1->a << endl;
					cout << "学生姓名：" << p1->name << endl;
					cout << "语文成绩：" << p1->chinese << endl;
					cout << "数学成绩：" << p1->math << endl;
					cout << "英语成绩：" << p1->english << endl;
				}
				p1 = p2->next;
				p2 = p1;
			}
			if (n == p1->name) {
				cout << "学生学号：" << p1->a << endl;
				cout << "学生姓名：" << p1->name << endl;
				cout << "语文成绩：" << p1->chinese << endl;
				cout << "数学成绩：" << p1->math << endl;
				cout << "英语成绩：" << p1->english << endl;
			}else {
				cout << "查无此人" << endl;
			}
		}
	}

	void xhcx(student *p) {
		int b;
		cout << "请输入要查询的学生学号：" << endl;
		cin >> b;
		student *p1, *p2;
		p1 = p2 = p;
		if (p->next == NULL) {
			if (b == p->a) {
				cout << "学生学号：" << p->a << endl;
				cout << "学生姓名：" << p->name << endl;
				cout << "语文成绩：" << p->chinese << endl;
				cout << "数学成绩：" << p->math << endl;
				cout << "英语成绩：" << p->english << endl;
			}else {
				cout << "查无此人" << endl;
			}
		}else {
			for (; p1->next != NULL;) {
				if (b == p1->a) {
					cout << "学生学号：" << p1->a << endl;
					cout << "学生姓名：" << p1->name << endl;
					cout << "语文成绩：" << p1->chinese << endl;
					cout << "数学成绩：" << p1->math << endl;
					cout << "英语成绩：" << p1->english << endl;
				}
				p1 = p2->next;
				p2 = p1;
			}
			if (b == p1->a) {
				cout << "学生学号：" << p1->a << endl;
				cout << "学生姓名：" << p1->name << endl;
				cout << "语文成绩：" << p1->chinese << endl;
				cout << "数学成绩：" << p1->math << endl;
				cout << "英语成绩：" << p1->english << endl;
			}else {
				cout << "查无此人" << endl;
			}
		}
	}

	void fsdcx(student *p) {
		cout << "请输入要查询的科目：" << endl;
		cout << "1：语文；2：数学；3：英语" << endl;
		int b;
		int m=0, n=0, q=0, x=0, y=0;
		student *p1, *p2;
		p1 = p2 = p;
		cin >> b;
		switch (b) {
		case 1:for (;p1!=NULL;) {
			if (p1->chinese < 60) {
				m++;
			}
			else if (p1->chinese >= 60 && p1->chinese < 70) {
				n++;
			}
			else if (p1->chinese >= 70 && p1->chinese < 80) {
				q++;
			   }else if(p1->chinese>=80&&p1->chinese<90){
				   x++;
			   }
			   else if (p1->chinese >= 90 && p1->chinese <= 100) {
				   y++;
			   }
			   else {
				   cout << "error" << endl;
			   }
			   p1 = p2->next;
			   p2 = p1;
		}
			   cout << "语文成绩分数段：" << endl;
			   cout << "60分以下的人数：" << m-1 << endl;
			   cout << "60-70分的人数：" << n << endl;
			   cout << "70-80分的人数：" << q << endl;
			   cout << "80-90分的人数：" << x << endl;
			   cout << "90-100分的人数：" << y << endl;
			   break;
		case 2:for (; p1 != NULL;) {
			if (p1->math < 60) {
				m++;
			}
			else if (p1->math >= 60 && p1->math < 70) {
				n++;
			}
			else if (p1->math >= 70 && p1->math < 80) {
				q++;
			}
			else if (p1->math >= 80 && p1->math<90) {
				x++;
			}
			else if (p1->math >= 90 && p1->math <= 100) {
				y++;
			}
			else {
				cout << "error" << endl;
			}
			p1 = p2->next;
			p2 = p1;
		}
			   cout << "数学成绩分数段：" << endl;
			   cout << "60分以下的人数：" << m-1 << endl;
			   cout << "60-70分的人数：" << n << endl;
			   cout << "70-80分的人数：" << q << endl;
			   cout << "80-90分的人数：" << x << endl;
			   cout << "90-100分的人数：" << y << endl;
			   break;
		case 3:for (; p1 != NULL;) {
			if (p1->english < 60) {
				m++;
			}
			else if (p1->english >= 60 && p1->english < 70) {
				n++;
			}
			else if (p1->english >= 70 && p1->english < 80) {
				q++;
			}
			else if (p1->english >= 80 && p1->english<90) {
				x++;
			}
			else if (p1->english >= 90 && p1->english <= 100) {
				y++;
			}
			else {
				cout << "error" << endl;
			}
			p1 = p2->next;
			p2 = p1;
		}
			   cout << "英语成绩分数段：" << endl;
			   cout << "60分以下的人数：" << m-1 << endl;
			   cout << "60-70分的人数：" << n << endl;
			   cout << "70-80分的人数：" << q << endl;
			   cout << "80-90分的人数：" << x << endl;
			   cout << "90-100分的人数：" << y << endl;
			   break;
		default:cout << "error" << endl; break;
		}
	}

	void kmaver(student *p) {
		cout << "请输入要查询的科目：" <<  endl;
		cout << "1：语文；2：数学；3：英语" << endl;
		student *p1, *p2;
		p1 = p2 = p;
		int  b, c = 0, sum = 0;
		double aver;
		cin >> b;
		switch (b) {
		case 1:for (;p1!=NULL;c++) {
			sum += p1->chinese;
			p1 = p2->next;
			p2 = p1;
		}
			   aver = sum / c;
			   cout << "语文的平均成绩为：" << aver << endl;
			   break;
		case 2:for (; p1 != NULL; c++) {
			sum += p1->math;
			p1 = p2->next;
			p2 = p1;
		}
			   aver = sum / c;
			   cout << "数学的平均成绩为：" << aver << endl;
			   break;
		case 3:for (; p1 != NULL; c++) {
			sum += p1->english;
			p1 = p2->next;
			p2 = p1;
		}
			   aver = sum / c;
			   cout << "英语的平均成绩为：" << aver << endl;
			   break;
		default:cout << "error" << endl;
		}
	}

	void xmaver(student *p) {
		string n;
		student *p1, *p2;
		p1 = p2 = p;
		int sum = 0;
		double aver;
		cout << "请输入要查询的学生姓名：" << endl;
		cin >> n;
		if (n != p1->name) {
			for (; n != p1->name;) {
				p1 = p2->next;
				p2 = p1;
			}
		}
		sum = p1->chinese + p1->math + p1->english;
		aver = sum / 3;
		cout << "该学生平均成绩为：" << aver << endl;
	}

	void sxpl(student *p) {
		cout << "请输入要排序的科目：" << endl;
		cout << "1：语文；2：数学；3：英语" << endl;
		int b;
		cin >> b;
		student *p1, *p2, *p3, *p4;
		p1 = p2 = p3 = p4 = p;
		student *m;
		m = new student;
		switch (b) {
		case 1:for (; p1 != NULL;) {
			for (p3=p2=p1->next;p2!=NULL;) {
				if (p1->chinese > p2->chinese) {
					m->name = p1->name;
					m->a = p1->a;
					m->chinese = p1->chinese;
					m->math = p1->math;
					m->english = p1->english;
					p1->name = p2->name;
					p1->a = p2->a;
					p1->chinese = p2->chinese;
					p1->math = p2->math;
					p1->english = p2->english;
					p2->name = m->name;
					p2->a = m->a;
					p2->chinese = m->chinese;
					p2->math = m->math;
					p2->english = m->english;
				}
				p3 = p2->next;
				p2 = p3;
				}
			p4 = p1->next;
			p1 = p4;
			}
			break;
		case 2:for (; p1 != NULL;) {
			for (p2 = p1->next; p2 != NULL;) {
				if (p1->math > p2->math) {
					m->name = p1->name;
					m->a = p1->a;
					m->chinese = p1->chinese;
					m->math = p1->math;
					m->english = p1->english;
					p1->name = p2->name;
					p1->a = p2->a;
					p1->chinese = p2->chinese;
					p1->math = p2->math;
					p1->english = p2->english;
					p2->name = m->name;
					p2->a = m->a;
					p2->chinese = m->chinese;
					p2->math = m->math;
					p2->english = m->english;
				}
				p3 = p2->next;
				p2 = p3;
				}
			p4 = p1->next;
			p1 = p4;
			}
			break;
		case 3:for (; p1 != NULL;) {
			for (p2 = p1->next; p2 != NULL;) {
				if (p1->english > p2->english) {
					m->name = p1->name;
					m->a = p1->a;
					m->chinese = p1->chinese;
					m->math = p1->math;
					m->english = p1->english;
					p1->name = p2->name;
					p1->a = p2->a;
					p1->chinese = p2->chinese;
					p1->math = p2->math;
					p1->english = p2->english;
					p2->name = m->name;
					p2->a = m->a;
					p2->chinese = m->chinese;
					p2->math = m->math;
					p2->english = m->english;
				}
				p3 = p2->next;
				p2 = p3;
			}
			p4 = p1->next;
			p1 = p4;
		}
			   break;
		default:cout << "error" << endl; break;
		}
		}
	
     void jxpl(student *p) {
		cout << "请输入要排序的科目：" << endl;
		cout << "1：语文；2：数学；3：英语" << endl;
		int b;
		cin >> b;
		student *p1, *p2, *p3, *p4;
		p1 = p2 = p3 = p4 = p;
		student *m;
		m = new student;
		switch (b) {
		case 1:for (; p1 != NULL;) {
			for (p3 = p2 = p1->next; p2 != NULL;) {
				if (p1->chinese < p2->chinese) {
					m->name = p1->name;
					m->a = p1->a;
					m->chinese = p1->chinese;
					m->math = p1->math;
					m->english = p1->english;
					p1->name = p2->name;
					p1->a = p2->a;
					p1->chinese = p2->chinese;
					p1->math = p2->math;
					p1->english = p2->english;
					p2->name = m->name;
					p2->a = m->a;
					p2->chinese = m->chinese;
					p2->math = m->math;
					p2->english = m->english;
				}
				p3 = p2->next;
				p2 = p3;
			}
			p4 = p1->next;
			p1 = p4;
		}
			   break;
		case 2:for (; p1 != NULL;) {
			for (p2 = p1->next; p2 != NULL;) {
				if (p1->math < p2->math) {
					m->name = p1->name;
					m->a = p1->a;
					m->chinese = p1->chinese;
					m->math = p1->math;
					m->english = p1->english;
					p1->name = p2->name;
					p1->a = p2->a;
					p1->chinese = p2->chinese;
					p1->math = p2->math;
					p1->english = p2->english;
					p2->name = m->name;
					p2->a = m->a;
					p2->chinese = m->chinese;
					p2->math = m->math;
					p2->english = m->english;
				}
				p3 = p2->next;
				p2 = p3;
			}
			p4 = p1->next;
			p1 = p4;
		}
			   break;
		case 3:for (; p1 != NULL;) {
			for (p2 = p1->next; p2 != NULL;) {
				if (p1->english < p2->english) {
					m->name = p1->name;
					m->a = p1->a;
					m->chinese = p1->chinese;
					m->math = p1->math;
					m->english = p1->english;
					p1->name = p2->name;
					p1->a = p2->a;
					p1->chinese = p2->chinese;
					p1->math = p2->math;
					p1->english = p2->english;
					p2->name = m->name;
					p2->a = m->a;
					p2->chinese = m->chinese;
					p2->math = m->math;
					p2->english = m->english;
				}
				p3 = p2->next;
				p2 = p3;
			}
			p4 = p1->next;
			p1 = p4;
		}
			   break;
		default:cout << "error" << endl; break;
		}
	}

	student *insert(student *p) {
		cout << "请输入要插入的位置编号：" << endl;
		int b;
		cin >> b;
		student *p1, *p2, *p3;
		p1 = p2 = p3 = p;
		if (b == 1) {
			p = new student;
			cout << "请输入要插入的学生信息：" << endl;
			input(p);
			p->next = p1;
		}else{
			for (b -= 1; b > 0; --b) {
				p1 = p2->next;
				p2 = p1;
				p3 = p1;
			}
			p1 = p2->next;
			p2 = new student;
			p3->next = p2;
			p2->next = p1;
			input(p2);
		}
		return p;
	}

	void output(student *p) {
		for (;p != NULL;) {
			cout << "学生学号：" << p->a << endl;
			cout << "学生姓名：" << p->name << endl;
			cout << "语文成绩：" << p->chinese << endl;
			cout << "数学成绩：" << p->math << endl;
			cout << "英语成绩：" << p->english << endl;
			p = p->next;
		}
	}
	};

int main()
{
	int a, b = 0;
	student *l;
	student m;
	l = m.create();
	while (b <= 100) {
		cout << "1：结束" << endl;
		cout << "2：删除学生成绩" << endl;
		cout << "3：修改学生成绩" << endl;
		cout << "4：按姓名查询" << endl;
		cout << "5：按学号查询" << endl;
		cout << "6：分数段查询" << endl;
		cout << "7：输入科目查询平均成绩" << endl;
		cout << "8：输入姓名查询平均成绩" << endl;
		cout << "9：升序排列" << endl;
		cout << "10：降序排列" << endl;
		cout << "11：插入一个学生信息" << endl;
		cout << "12：输出学生信息" << endl;
		cout << "请输入选择" << endl;
		cin >> a;
		switch (a) {
		case 1:exit(0); break;
		case 2:l=m.del(l); break;
		case 3:l=m.change(l); break;
		case 4:m.xmcx(l); break;
		case 5:m.xhcx(l); break;
		case 6:m.fsdcx(l); break;
		case 7:m.kmaver(l); break;
		case 8:m.xmaver(l); break;
		case 9:m.sxpl(l); break;
		case 10:m.jxpl(l); break;
		case 11:l = m.insert(l); break;
		case 12:m.output(l); break;
		default:cout << "无效" << endl; break;
		}
	}
	return 0;
}
