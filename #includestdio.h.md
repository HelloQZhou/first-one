\#include<stdio.h>

\#include<stdlib.h>

\#include<string.h>

typedef struct myscore

{  int math;

​	int english;

​	int clanguage;

​	int modian;

​	int shudian;

}st;

typedef struct student

{

​	char name[20];

​	int id; //学号

​	int grand;//班级

​	char department[20];//学部

​	char major[20];//专业

​	st score;

​	

}stu;

typedef struct node

{

​	stu data;

​	struct node* next;//指针域

}*Linklist,Listnode;

 

int main(void) {

​	void examnopass(Linklist L);

​	void classpass(Linklist L);

​	void average(Linklist L);

​	int deletestu(Linklist L, int en);

​	int search(Linklist L, int e);

​	void output(Linklist L);

​	void insert(Linklist L);

​	int op;

 

​	//Linklist L=NULL; 不能设为空，必须给L分配空间/初始化

  Linklist L= (Linklist)malloc(sizeof(Listnode));

​	L->next = NULL;

​	while (1) {

​		system("cls"); printf("\n\n");

​		printf("*************************************************\n");

​		printf("*\t  欢迎使用学生成绩管理系统\t\t*\n");

​		printf("*************************************************\n");

​		printf("*\t请选择功能列表  \t\t\t*\n");

​		printf("*\t1.插入学生信息  \t\t\t*\n");

​		printf("*\t2.查询学生信息  \t\t\t*\n");

​		printf("*\t3.删除学生信息  \t\t\t*\n");

​		printf("*\t4.输出学生信息  \t\t\t*\n");

​		printf("*\t5.每名学生的平均分  \t\t\t*\n");

​		printf("*\t6.每门课程的及格率和每门课程及格人数   *\n");

​		printf("*\t7.每门课程的补考名单  \t\t\t*\n");

​		printf("*\t0.退出系统  \t\t\t\t*\n");

​		printf("*************************************************\n");

​		printf("   请选择你的操作[0~7]:");

 

 

​		scanf_s("%d", &op);

​		switch (op)

​		{

​		case 0:

​			break;

​		case 1:

​			//输入学生信息

​			insert(L );

​			printf("输入成功\n");

​			system("pause");

​			break;

​		case 2:

​			int e;

​			if (L->next == NULL)printf("暂无信息！\n");

​			else {

​				printf("请输入要查找的学生学号:");

​				scanf_s("%d", &e);

​				if (search(L, e) == 1) {

​				}

​				else

​					printf("未找到该学生!\n");

​			}

​			system("pause");

​			break;

​		case 3:

​			int en;

​			if (L->next == NULL)printf("暂无信息！\n");

​			else {

​				printf("请输入要删除的学生学号:");

​				scanf_s("%d", &en);

​				if (deletestu(L, en) == 1)

​				{

​					printf("删除成功");

​				}

​				else 

​					printf("操作失败");

​			}

​			system("pause");

​			break;

​		case 4:

​			if (L->next == NULL)printf("暂无消息！\n");

​			else {

​				output(L);

​			}

​			system("pause");

​			break;

​		case 5:

​			if (L->next == NULL)printf("暂无消息！\n");

​			else {

​				average(L);

​			}

​			 system("pause");

​			 break;

​		case 6:

​			if (L->next == NULL)printf("暂无消息！\n");

​			else {

​				classpass(L);

​			}

​			system("pause");

​			break;

​		case 7:

​			if (L->next == NULL)printf("暂无消息！\n");

​			else {

​				examnopass(L);

​			}

​			 system("pause");

​			 break;

​		}

​	}

​	printf("欢迎下次再使用本系统！\n");

}

//1.插入学生信息

void insert(Linklist L) {

​	Linklist P;

​	P= (Linklist)malloc(sizeof(Listnode));

​	//老王88 3 信息 软件 100 100 100 99 98

​	//张三 87 4 信息 软件 100 20 30 40 50

​	//李四 85 3 信息 软件 100 20 70 50 80

​	//王五 84 3 信息 自动化 100 90 30 40 59

​	//老李 80 6 信息 光电  59 59 60 77 44

​	printf("姓名，学号，班级，学部，专业，c，数学,英语，模电，数电\n");

​	scanf_s("%s",P->data.name,sizeof(P->data.name));

​	scanf_s("%d",&P->data.id,sizeof(P->data.id));

​	scanf_s("%d", &P->data.grand, sizeof(P->data.grand));

​	scanf_s("%s",P->data.department,sizeof(P->data.department));

​	scanf_s("%s",P->data.major,sizeof(P->data.major));

​	scanf_s("%d",&P->data.score.clanguage);

​	scanf_s("%d",&P->data.score.math);

​	scanf_s("%d",&P->data.score.english);

​	scanf_s("%d",&P->data.score.modian);

​	scanf_s("%d",&P->data.score.shudian);

​	P->next = L->next;

​	L->next = P;

}

//2.查询学生信息 

int search(Linklist L, int e) { 

​	Linklist P=L->next;

​		while (P != NULL)

​		{

​			if (P->data.id == e)

​			{

​				printf("姓名\t学号\t班级\t学部\t专业\tc语言\t数学\t英语\t模电\t数电\n");

​				printf("%s\t%d\t%d\t%s\t%s\t%d\t%d\t%d\t%d\t%d",

​					P->data.name, P->data.id, P->data.grand, P->data.department, P->data.major,

​					P->data.score.clanguage, P->data.score.math, P->data.score.english, P->data.score.modian, P->data.score.shudian);

​				printf("\n");

​				return 1;

​			}

​			P = P->next;

​		}

​		return 0;

}

 

//3.删除学生信息

int deletestu(Linklist L,int en)

{

​	Linklist P=L->next;

​	Linklist Q=L;

​		while (P != NULL)

​		{

​			if (P->data.id == en)

​			{

​				Q->next = P->next;

​				free(P);

​				return 1;

​			}

​			Q = P;

​			P = P->next;

​		}

​		return 0;

}

 

//4.输出学生信息

void output(Linklist L) {

​	Linklist P;

​	P = L->next;

​		printf("姓名\t学号\t班级\t学部\t专业\tc语言\t数学\t英语\t模电\t数电\n");

​		while (P != NULL)

​		{

​			printf("%s\t%d\t%d\t%s\t%s\t%d\t%d\t%d\t%d\t%d", 

​				P->data.name,P->data.id, P->data.grand, P->data.department, P->data.major, 

​				P->data.score.clanguage,P->data.score.math, P->data.score.english, P->data.score.modian, P->data.score.shudian);

​			printf("\n");

​			P = P->next;

​		}

​		printf("\n");

}

//5.计算每名学生的平均分并输出

void average(Linklist L) {

​	Linklist P=L->next;

​	int ave;

​		printf("姓名\t\t平均分\n");

​		while (P != NULL) {

​			ave = (P->data.score.clanguage + P->data.score.english + P->data.score.math + P->data.score.modian + P->data.score.shudian) / 5;

​			printf("%s\t\t%d\n", P->data.name, ave);

​			P = P->next;

​		}

}

//6.统计每门课程的及格率并且输出，找到每门课程及格同学的个数 

void classpass(Linklist L) {

​	Linklist P=L->next;

​	double c=0, mat=0, e=0, mo=0, s=0,count=0;

​		while (P != NULL) {

​			count++;

​			if (P->data.score.clanguage >= 60) {

​				c++;

​			}

​			if (P->data.score.math >= 60) {

​				mat++;

​			}

​			if (P->data.score.modian >= 60) {

​				mo++;

​			}

​			if (P->data.score.english >= 60) {

​				e++;

​			}

​			if (P->data.score.shudian >= 60) {

​				s++;

​			}

​			P = P->next;

​		}

​		printf("c语言及格人数:%d  及格率：%.2f %%\n", (int)c, (c / count) * 100);

​		printf("数学及格人数：%d  及格率：%.2f %%\n", (int)mat, (mat / count) * 100);

​		printf("英语及格人数：%d  及格率：%.2f %%\n", (int)e, (e / count) * 100);

​		printf("模电及格人数：%d  及格率：%.2f %%\n", (int)mo, (mo / count) * 100);

​		printf("数电及格人数：%d  及格率：%.2f %%\n", (int)s, (s / count) * 100);

​	}

//7.输出每门课程的补考名单，按照课程来分别进行输出

void examnopass(Linklist L) {

​	Linklist P = L->next;

​	

​		printf("c语言补考名单:");

​		while (P != NULL) {

​			if (P->data.score.clanguage < 60) {

​				printf("%s  ", P->data.name);

​			}

​			P = P->next;

​		}

​		printf("\n");

​		P = L->next;

​		printf("数学补考名单:");

​		while (P != NULL) {

​			if (P->data.score.math < 60) {

​				printf("%s  ", P->data.name);

​			}

​			P = P->next;

​		}

​		printf("\n");

​		P = L->next;

​		printf("英语补考名单:");

​		while (P != NULL) {

​			if (P->data.score.english < 60) {

​				printf("%s  ", P->data.name);

​			}

​			P = P->next;

​		}

​		printf("\n");

​		P = L->next;

​		printf("模电补考名单:");

​		while (P != NULL) {

​			if (P->data.score.modian < 60) {

​				printf("%s  ", P->data.name);

​			}

​			P = P->next;

​		}

​		printf("\n");

​		P = L->next;

​		printf("数电补考名单:");

​		while (P != NULL) {

​			if (P->data.score.shudian < 60) {

​				printf("%s  ", P->data.name);

​			}

​			P = P->next;

​		}

​		printf("\n");

​	}

 