# queen-s-attack
i had solved this but only one testcase is showing error


#include<iostream>
#include<algorithm>
#include<vector>
using namespace std;
 
int main()
{
   long long int k,n;
   cin>>n>>k; 
  long long int Q_ps = n*2-2;  /*Q_ps = total no.of boxes that the queen could move (verticaly and Horizontaly)*/

   int q_r,q_c;  cin>>q_r>>q_c;  //Queen's position
  
     long long int obstacle[k][2];
     for(long long int i=0; i<k; i++)
     {
       for(int j=0; j<2; j++)  
       { cin>>obstacle[i][j]; }       
     }
    
   for(long long int i=0; i<k; i++)
     {
       if(obstacle[i][0]==q_r)
             {  
               if(obstacle[i][1]<q_c)
                 Q_ps = Q_ps-obstacle[i][1];
               else 
                 Q_ps = Q_ps-(n-obstacle[i][1])-1;
             }
           
       if(obstacle[i][1]==q_c)
            {  if(obstacle[i][0]<q_r)
                 Q_ps = Q_ps-obstacle[i][0];
               else 
                 Q_ps = Q_ps-(n-obstacle[i][0])-1;
            }
    }
  
       long long int l,i,j;
        for(i=q_r+1,j=q_c-1; i<=n; i++)   // 1 - top left block
         { if(j>0)
           {
             int flag = 0;
            for(l=0; l<k; l++)
             {
               if(obstacle[l][0]==i && obstacle[l][1]==j)
                { flag = 1; break; }
             }
           if(flag==0)
             Q_ps++; 
           if(flag==1)
             break; 
             j--;
           }   
         }  
    
    for(i=q_r+1,j=q_c+1; i<=n; i++)  //2 - top right block
     { if(j<=n)
       {
          int flag = 0;
        for(l=0; l<k; l++)
         {
           if(obstacle[l][0]==i && obstacle[l][1]==j)
             { flag = 1; break; }
         }
         if(flag==0)
          Q_ps++;
         if(flag==1)
          break; 
           j++;
       }    
    }  
   
   
     for(i=q_r-1,j=q_c-1; j>=1; j--)  //3 - bottom left block
      { if(i>0)
        {
           int flag = 0;
        for( l=0; l<k; l++)
         {
             if(obstacle[l][0]==i && obstacle[l][1]==j)
             {  flag = 1; break; }
         }   
           if(flag==0)
            Q_ps++; 
           if(flag==1)
            break;
             i--; 
        }     
      }  
    
     for(j=q_c+1,i=q_r-1; j<=n; j++)  //4 - bottom right block
      { if(i>0)
        { 
           int flag = 0;
        for(l=0; l<k; l++)
         {
           if(obstacle[l][0]==i && obstacle[l][1]==j)
             { flag = 1; break; }
         }
         if(flag==0)
          Q_ps++;
         if(flag==1)
           break; i--;  
        }
       }  
   cout<<Q_ps;  
 }
