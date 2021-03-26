# test
This is a description.
#include<stdio.h>  
#include<stdlib.h>
#include<string.h>
#define BUFLEN 100
#define LEN 15 
#define N 100 
struct record 
{
char code[LEN+1]; 
char name[LEN+1]; 
int age; 
char sex[3]; 
char time[LEN+1]; 
char add[30]; 
char tel[LEN+1]; 
char mail[30]; 
}stu[N];
int k=1,n,m; 
void readfile();
void seek();
void modify();
void insert();
void del();
void display();
void save();
void menu(); 
int main()
{  
while(k)
menu();
system("pause");
return 0;
} 
void help()
{ 
printf("\n0.欢迎使用系统帮助！\n");
printf("\n1.进入系统后,先刷新学生信息,再查询;\n");
printf("\n2.按照菜单提示键入数字代号;\n");
printf("\n3.增加学生信息后,切记保存按;\n");
printf("\n4.谢谢您的使用！\n");
} 
void readfile()
{
char *p="C:\\student.txt";
FILE *fp;
int i=0;
if ((fp=fopen("C:\\student.txt","r"))==NULL)
{  
printf("打开文件失败！\n");
}
while(fscanf(fp,"%s %s%d%s %s %s %s %s",stu[i].code,stu[i].name,&stu[i].age,
stu[i].sex,stu[i].time,stu[i].add,stu[i].tel,stu[i].mail)==8)
{
i++;
i=i;
}
fclose(fp);
n=i;
printf("刷新成功！\n");
} 

void seek() 
{
int i,item,flag;
char s1[21]; 
printf("------------------\n");
printf("-----1.按学号查询-----\n");
printf("-----2.按姓名查询-----\n");
printf("-----3.退出本菜单-----\n");
printf("------------------\n");
while(1)
{
printf("请选择子菜单编号:");
scanf("%d",&item);
flag=0;
switch(item)
{
case 1:
printf("请输入要查询的学生的学号:\n");
scanf("%s",s1);
for(i=0;i<n;i++)
if(strcmp(stu[i].code,s1)==0)
{
flag=1;
printf("学生学号 学生姓名 年龄 性别  出生年月  地址    电话      E-mail\n");
printf("--------------------------------------------------------------------\n");
printf("%6s %7s %6d %5s %9s %8s %10s %14s\n",stu[i].code,stu[i].name,stu[i].age,
stu[i].sex,stu[i].time,stu[i].add,stu[i].tel,stu[i].mail);
}
if(flag==0)
printf("该学号不存在！\n"); break;
case 2:
printf("请输入要查询的学生的姓名:\n");
scanf("%s",s1);
for(i=0;i<n;i++)
if(strcmp(stu[i].name,s1)==0)
{
flag=1;
printf("学生学号 学生姓名 年龄 性别  出生年月  地址    电话    E-mail\n");
printf("--------------------------------------------------------------------\n");
printf("%6s %7s %6d %5s %9s %8s %10s %14s\n",stu[i].code,stu[i].name,stu[i].age,
stu[i].sex,stu[i].time,stu[i].add,stu[i].tel,stu[i].mail);
}
if(flag==0)
printf("该姓名不存在！\n"); break;
case 3:return;
default:printf("请在-3之间选择\n");
}
}
} 
void modify() 
{
int i,item,num;
char sex1[3],s1[LEN+1],s2[LEN+1]; 
printf("请输入要要修改的学生的学号:\n");
scanf("%s",s1);
for(i=0;i<n;i++)
if(strcmp(stu[i].code,s1)==0) 
num=i;
printf("------------------\n");
printf("1.修改姓名\n");
printf("2.修改年龄\n");
printf("3.修改性别\n");
printf("4.修改出生年月\n");
printf("5.修改地址\n");
printf("6.修改电话号码\n");
printf("7.修改E-mail地址\n");
printf("8.退出本菜单\n");
printf("------------------\n");
while(1)
{
printf("请选择子菜单编号:");
scanf("%d",&item);
switch(item)
{
case 1:
printf("请输入新的姓名:\n");
scanf("%s",s2);
strcpy(stu[num].name,s2); break;
case 2:
printf("请输入新的年龄:\n");
scanf("%d",&stu[num].age);break;
case 3:
printf("请输入新的性别:\n");
scanf("%s",sex1);
strcpy(stu[num].sex,sex1); break;
case 4:
printf("请输入新的出生年月:\n");
scanf("%s",s2);
strcpy(stu[num].time,s2); break;
case 5:
printf("请输入新的地址:\n");
scanf("%s",s2);
strcpy(stu[num].add,s2); break;
case 6:
printf("请输入新的电话号码:\n");
scanf("%s",s2);
strcpy(stu[num].tel,s2); break;
case 7:
printf("请输入新的E-mail地址:\n");
scanf("%s",s2);
strcpy(stu[num].mail,s2); break;
case 8:return;
default:printf("请在-8之间选择\n");
}
}
} 
 void sort()
{
int i,j,*p,*q,s;
  char temp[10];
for(i=0;i<n-1;i++)
{
for(j=n-1;j>i;j--)
if(strcmp(stu[j-1].code,stu[j].code)>0)
{
strcpy(temp,stu[j-1].code);
strcpy(stu[j-1].code,stu[j].code);
strcpy(stu[j].code,temp);
strcpy(temp,stu[j-1].name);
strcpy(stu[j-1].name,stu[j].name);
strcpy(stu[j].name,temp);
strcpy(temp,stu[j-1].sex);
strcpy(stu[j-1].sex,stu[j].sex);
strcpy(stu[j].sex,temp);
strcpy(temp,stu[j-1].time);
strcpy(stu[j-1].time,stu[j].time);
strcpy(stu[j].time,temp);
strcpy(temp,stu[j-1].add);
strcpy(stu[j-1].add,stu[j].add);
strcpy(stu[j].add,temp);
strcpy(temp,stu[j-1].tel);
strcpy(stu[j-1].tel,stu[j].tel);
strcpy(stu[j].tel,temp);
strcpy(temp,stu[j-1].mail);
strcpy(stu[j-1].mail,stu[j].mail);
strcpy(stu[j].mail,temp);
 p=&stu[j-1].age;
 q=&stu[j].age;
 s=*q;
 *q=*p;
 *p=s;
}
}
} 
void insert()
{
 int i=n,j,flag;
printf("请输入待增加的学生数:\n");
scanf("%d",&m);
do
{
 flag=1;
while(flag)
{
flag=0;
printf("请输入第%d 个学生的学号:\n",i+1);
scanf("%s",stu[i].code);
for(j=0;j<i;j++)
if(strcmp(stu[i].code,stu[j].code)==0)
{
printf("已有该学号,请检查后重新录入!\n");
flag=1;
break; 
}
}
printf("请输入第%d 个学生的姓名:\n",i+1);
scanf("%s",stu[i].name);
printf("请输入第%d 个学生的年龄:\n",i+1);
scanf("%d",&stu[i].age);
printf("请输入第%d 个学生的性别:\n",i+1);
scanf("%s",stu[i].sex);
printf("请输入第%d 个学生的出生年月:(格式:年.月)\n",i+1);
scanf("%s",stu[i].time);
printf("请输入第%d 个学生的地址:\n",i+1);
scanf("%s",stu[i].add);
printf("请输入第%d 个学生的电话:\n",i+1);
scanf("%s",stu[i].tel);
printf("请输入第%d 个学生的E-mail:\n",i+1);
scanf("%s",stu[i].mail);
if(flag==0)
{
 i=i;
i++;
}
}
while(i<n+m);
n+=m;
printf("录入完毕！\n\n");
sort();
} 
void del()
{
int i,j,flag=0;
char s1[LEN+1];
printf("请输入要删除学生的学号:\n");
scanf("%s",s1);
for(i=0;i<n;i++)
if(strcmp(stu[i].code,s1)==0)
{
 flag=1;
for(j=i;j<n-1;j++)
stu[j]=stu[j+1];
}
if(flag==0)
printf("该学号不存在！\n");
if(flag==1)
{
printf("删除成功,显示结果请选择菜单\n");
n--;
}
} 
void display()
{
 int i;
printf("所有学生的信息为:\n");
printf("学生学号 学生姓名 年龄 性别  出生年月  地址    电话    E-mail\n");
printf("--------------------------------------------------------------------\n");
for(i=0;i<n;i++)
{ 
printf("%6s %7s %5d %5s %9s %8s %10s %14s\n",stu[i].code,stu[i].name,stu[i].age,
stu[i].sex,stu[i].time,stu[i].add,stu[i].tel,stu[i].mail);
}
} 
void save()
{
int i;
FILE *fp;
fp=fopen("C:\\student.txt","w"); 
for(i=0;i<n;i++)
{
fprintf(fp,"%s %s %d %s %s %s %s %s\n",stu[i].code,stu[i].name,stu[i].age,
stu[i].sex,stu[i].time,stu[i].add,stu[i].tel,stu[i].mail);
}
fclose(fp);
} 
void menu()
{
int num;
printf(" \n\n                学生信息管理系统    \n\n");

printf("*********************系统功能菜单************************       \n");
printf("友情提示：查询前请先刷新系统！\n");
printf("     ----------------------   ----------------------   \n");
printf("     *********************************************     \n");
printf("     * 0.系统帮助及说明  * *  1.刷新学生信息   *     \n");
printf("     *********************************************     \n"); 
printf("     * 2.查询学生信息    * *  3.修改学生信息   *     \n");
printf("     *********************************************     \n");
printf("     * 4.增加学生信息    * *  5.按学号删除信息 *     \n");
printf("     *********************************************     \n");
printf("     * 6.显示当前信息    * *  7.保存当前学生信息*     \n");
printf("     ********************** **********************     \n");
printf("     * 8.退出系统        *                            \n");
printf("     **********************                            \n");
printf("     ----------------------   ----------------------                           \n");
printf("请选择菜单编号:");
scanf("%d",&num);
switch(num)
{ 
case 0:help();break;
case 1:readfile();break;
case 2:seek();break;
case 3:modify();break;
case 4:insert();break;
case 5:del();break;
case 6:display();break;
case 7:save();break;
case 8:k=0;break;
default:printf("请在-8之间选择\n");
}
}
