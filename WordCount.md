# WordCount

#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
int main(int argc, char *argv[])
{
    if( argc == 3 ){
        char data;
        FILE *fp = fopen(argv[2],"r");
         
         if(!fp){
            printf("错误：文件读取失败\n");
			        return -1;
         }     
		    
        //对参数进行判断
        //对字符数的统计 
        if( !strcmp(argv[1],"-c") ){
            char temp;
            int num = 0;
            temp = fgetc(fp);
            while( temp != EOF ){
                //putchar(temp);
                temp = fgetc(fp);
                num++;
            }
            printf("字符数：%d\n",num);
             
        }
        //对单词数的统计 
        else if( !strcmp(argv[1],"-w") ){
            int w = 0;
            char a = fgetc(fp);
            while( a != EOF){
                if( (a >='a' && a <='z') || ( a >='A' && a <='Z') || ( a >='0' && a <='9') ){
                    while( (a >='a' && a <='z') || ( a >='A' && a <='Z') || ( a >='0' && a <='9') )
                        a =fgetc(fp);
                    w++;
                    a =fgetc(fp);
                    
                }
                else
                    a =fgetc(fp);
            }
            printf("单词数：%d\n",w);
            
        }
        else{
           printf("错误：参数超出范围！\n");
           printf("允许参数：-c，-w，-l\n");
        }
        int n=fclose(fp);
    }
    system("pause");
    return 0;
}
