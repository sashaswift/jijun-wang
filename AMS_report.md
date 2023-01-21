# 计费系统开发记录

一，实验难点：

* 如何在一个源文件中调用另一个源文件中的函数？
  
  -创建一个与被调函数源文件相同名称的头文件，在头文件中声明该被调函数，在需要调用该函数的源文件中，声明该头文件，则可以对被调函数进行调用；

* 如何防止重复编译？
  
  -通过#ifndef...#endif,若程序块未被#define定义为一定标识符，则定义。在重复引用时则可避免重复编译；
  
  如下：
  
  ```c
  #ifndef TOOL
  #define TOOL//标识符
  #include <time.h>
  #include <string.h>
  #include "model.h"
  #include <conio.h>
  time_t stringToTime(char *s);
  void stringfortime(time_t tt);
  void invisiblePn();
  void invisiblePnForManager();
  #endif // TO0l
  ```

* 添加卡时如何记录开始时间和截止时间
  
  -使用<time.h>中的time函数可以得出1970年0时0分0秒到当前时间的秒数，返回值为time_t型，用localtime函数可将time_t型数据转成struct tm的结构体中数据，使用strftime函数可将struct tm结构体中数据转化成一定格式的时间字符串。
  
  ```c
  struct tm {
            int tm_sec;       //秒 – 取值区间为[0,59] 
            int tm_min;       // 分 - 取值区间为[0,59] 
            int tm_hour;      // 时 - 取值区间为[0,23] 
            int tm_mday;      // 一个月中的日期 - 取值区间为[1,31] 
            int tm_mon;       // 月份（从一月开始，0代表一月） - 取值区间为[0,11] 
            int tm_year;      // 年份，其值等于实际年份减去1900 
            int tm_wday;      //星期 – 取值区间为[0,6]，其中0代表星期天，1代表星期一
            int tm_yday;      //从每年的1月1日开始的天数 – 取值区间为[0,365]，其中0代表1月1日
            int tm_isdst;     // 夏令时标识符，实行夏令时的时候，tm_isdst为正。不实行夏令时的进候，tm_isdst为0；不了解情况时，tm_isdst()为负。
            };
  ```
  
  ```c
  //将time_t类型数据转换为年-月-日 时-分-秒
  void stringfortime(time_t tt){
      struct tm *TT;
      char string[50];
      TT=localtime(&tt);
      strftime(string,sizeof(string),"%Y-%m-%d %H:%M:%S",localtime(&tt));//Y-tm_year,m-tm_mon,d-tm_mday,H-tm_hour,M-tm_min,S-tm_sec
      printf("%s",string);
  
  }
  ```

* 如何以“卡号##密码##余额##……”的格式保存卡信息到文件中，并将文件中的数据读出？
  
  -通过fprintf函数，将数据做成字符串读入，用strtok将字符串中的数据字符串，使用atoi,atof函数将数据字符串转化为数据储存在结构体中。
  
  -PS:也可使用fwrite(void *ptr,size_t size,size_t nmemb,FILE *fp),可将结构体数据以数据块的形式写入，用fread(void *ptr,size_t size,size_t nmemb,FILE *fp)从文件中读取。

* 如何将字符串转换成time_t类型数据？
  
  -使用atoi函数，将时间字符串转换为数据，年份数据减去1900，月减去1，储存到struct tm函数中。再通过mktime函数转换成time_t型数据。
  
  ```c
  time_t stringToTime(char *s){
     struct tm date1;
      time_t tresult;
      char *date;
      date=strtok(s,"-");
      date1.tm_year=atoi(date)-1900;
      date=strtok(NULL,"-");
      date1.tm_mon=atoi(date)-1;
      date=strtok(NULL,"-");
      date1.tm_mday=atoi(date);
      date1.tm_hour=0;
      date1.tm_min=0;
      date1.tm_sec=0;
      date1.tm_isdst=0;
      tresult=mktime(&date1);
      return tresult;
   }
  ```

* 如何进行模糊查询？
  
  -使用strstr函数，将链表中卡号与输入卡号用strstr函数处理后返回值不为NULL的节点的数据打印。

* 如何在输入时对密码进行保密？
  
  -使用getch函数可以将使输入的字符不显示在屏幕上。
  
  ```c
  void invisiblePnForManager(){
      printf("请输入密码（长度为1~19）：");
      int i=0;
      while((Pn[i]=getch())!='\r'){//‘\r'为回车
          putchar('*');
          i++;
      }
      Pn[i]='\0';
      printf("\n");
  }
  ```

* 如何更新文件中的信息？
  
  读取文件时，读到要更改的数据块时，使用ftell函数得出要更改的数据位置，在使用fseek函数时指针指向一定位置，再使用fwrite函数将更改后的数据块写入。

二，实验中的一些错误：

* time_t是指1970年一月一日0时0分0秒后到指定时间时的秒数，而在将字符串转换为struct tm结构体中的tm_year时需要在字符串转换为数字时减去1900，不小心记成了1970；

* 在将数据读入链表时，将动态分布放在循环之外，导致分配的动态存储空间不足；

* 在将数据读入链表前，未对链表进行初始化；

* 遍历链表时，应令设指针，指向链表的初始节点，通过该指针对链表进行遍历，指向初始节点的语句下不小心写在将文件信息复制到链表的函数之前，导致错误；

* 读取卡信息时，存储卡信息的字符数组不够大导致错误

* 在写入卡信息字符串时，字符串末尾加换行符，但在读取文件时程序会出错，应在读取文件时加上判断句
  
  ```c
  int readcard(){
      listp card1;
      struct Card a;
      char s[1000];
      initCardList();
     if((fp=fopen("card_service.txt","r"))==NULL){
      return 0;
     }
     while(!feof(fp)){
        if((fscanf(fp,"%s",s))==0){
            return 0;
        }
  
              else{
                  if(feof(fp)){
                      break;
                  }//防止读取换行时出现错误
          a=parsecard(s);
          card1=malloc(sizeof(List));
          card1->t=a;
          card1->next=NULL;
          if(head==NULL){
              head=card1;
              cardlist=card1;
          }
          else{
              cardlist->next=card1;
              cardlist=cardlist->next;
          }
         }
     }
     fclose(fp);
     return 1;
  }
  ```

* 在更新文件中信息时，使用ftell判断位置时，令pos=ftell(fp);导致更新时的位置有误，应为pos=ftell(fp)-size_t size;

* 在更新卡信息时，使用strlen函数读取更新字符串前的字符串长度，未考虑'\n'和首字符导致更改位置有误；

* 在更新文件，文件打开方式有误，写成了”rb",应该为”rb+";


