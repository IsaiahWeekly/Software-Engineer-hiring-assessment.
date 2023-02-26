# Software-Engineer-hiring-assessment.
Software Engineer hiring assessment.
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<stdbool.h>

/* only used in string related operations */
typedef struct String string;
struct String
{
    char *str;
};

char *input(FILE *fp, int size, int has_space)
{
    int actual_size = 0;
    char *str = (char *)malloc(sizeof(char)*(size+actual_size));
    char ch;
    if(has_space == 1)
    {
        while(EOF != (ch=fgetc(fp)) && ch != '\n')
        {
            str[actual_size] = ch;
            actual_size++;
            if(actual_size >= size)
            {
                str = realloc(str,sizeof(char)*actual_size);
            }
        }
    }
    else
    {
        while(EOF != (ch=fgetc(fp)) && ch != '\n' && ch != ' ')
        {
            str[actual_size] = ch;
            actual_size++;
            if(actual_size >= size)
            {
                str = realloc(str,sizeof(char)*actual_size);
            }
        }
    }
    actual_size++;
    str = realloc(str,sizeof(char)*actual_size);
    str[actual_size-1] = '\0';
    return str;
}
/* only used in string related operations */


/*
 * the function  sameGroupStudent takes particularGroup & studentGroup as its argument, where:
particularGroup: represents the activity group whose total students the principal wants to know.
studentGroup: represents the group which are selected by the students.
 */
void  sameGroupStudent(int particularGroup, int studentGroup)
{
    // Initialize variables
    int numStudents = 0;
    int currGroup;
    
    // Read input from user and count the number of students in the particular activity group
    for(int i = 0; i < studentGroup; i++){
        scanf("%d", &currGroup);
        if(currGroup == particularGroup){
            numStudents++;
        }
    }
    
    // Print the number of students in the particular activity group
    printf("%d", numStudents);

}

int main()
{
    int particularGroup;
    int studentGroup;
    
    //input for particularGroup
    scanf("%d", &particularGroup);
    
    //input for studentGroup
    scanf("%d", &studentGroup);
    
    sameGroupStudent(particularGroup, studentGroup);
    return 0;
} 

