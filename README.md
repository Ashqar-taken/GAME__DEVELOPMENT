## EX 5 : TWO DIMENSIONALTRANSFORMATION 

**AIM**

To write a c program to implement 2D transformation of image.


**ALGORITHM**

Step 1:Start the program.

Step 2:Draw the image with default parameters.

Step 3 : Get the choice from the user.

Step 4: Get the parameters for transformation.

Step 5 : Perform the transformation.

Step 6 : Draw the image.

Step 7 : Stop the program.


**Program :**
```
Developed By: Ashqar Ahamed S.T
Registered By: 212224240018
```
```
# include<graphics.h> 
# include<stdio.h> 
# include<conio.h> 
# include<math.h> 
void main() 
{ 
int gd=DETECT,gm,i,j,k,ch; 
float tx,ty,x,y,ang,n,temp; 
float  a[5][3],si,co,b[5][3],c[5][3]; 
initgraph(&gd,&gm,"e:\\tcpp\\bgi"); 
n=4; 
a[0][0]=0;    a[0][1]=0;   a[1][0]=100;  a[1][1]=0; 
a[2][0]=100;  a[2][1]=100; a[3][0]=0;    a[3][1]=100; 
a[4][0]=0;    a[4][1]=0; 
while(1) 
{ 
cleardevice(); 
gotoxy(1,8); 
printf("\n\t******** Program to perform 2-D Transformations ********"); 
printf("\n\t\t\t 1. Accept the polygon"); 
printf("\n\t\t\t 2. Perform translation"); 
printf("\n\t\t\t 3. Perform scaling"); 
printf("\n\t\t\t 4. Perform rotation"); 
printf("\n\t\t\t 5. Perform reflection"); 
printf("\n\t\t\t 6. Perform shearing"); 
printf("\n\t\t\t 7. Exit"); 
printf("\n\t\t\t Enter your choice::"); 
scanf("%d",&ch); 
switch(ch) 
{ 
case 1: 
cleardevice(); 
gotoxy(1,1); 
printf("\n\tEnter no of points.:"); 
scanf("%f",&n); 
 
    for(i=0;i<n;i++) 
 { 
   printf("\n\t Enter x,y co-ordinates for %d::",i+1); 
   scanf("%f %f",&a[i][0],&a[i][1]); 
  } 
       a[i][0]=a[0][0]; 
       a[i][1]=a[0][1]; 
      cleardevice(); 
      for(i=0;i<n;i++) 
      line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]); 
      line(0,240,639,240); 
      line(320,0,320,479); 
      getch(); 
      break; 
 
    case 2: 
      cleardevice(); 
      for(i=0;i<n;i++) 
      line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]); 
      line(0,240,639,240); 
      line(320,0,320,479); 
       gotoxy(1,1); 
       printf("Enter translation vectors tx and ty\n\t"); 
       scanf("%f %f",&x,&y); 
       cleardevice(); 
  for(i=0;i<n;i++) 
  line(320+a[i][0]+x,240-(a[i][1]+y),320+a[i+1][0]+x,240-(a[i+1][1]+y)); 
  line(0,240,639,240); 
  line(320,0,320,479); 
  getch(); 
       break; 
 
    case 3: 
           cleardevice(); 
      for(i=0;i<n;i++) 
      line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]); 
      line(0,240,639,240); 
      line(320,0,320,479); 
     gotoxy(1,1); 
     printf("Enter scaling vectors tx and ty\n\t"); 
     scanf("%f %f",&x,&y); 
     if(x==0) 
     x=1; 
     if(y==0) 
      
 
       y=1; 
       cleardevice(); 
  for(i=0;i<n;i++) 
  line(320+(a[i][0]*x),240-(a[i][1]*y),320+(a[i+1][0]*x),240-(a[i+1][1]*y)); 
  line(0,240,639,240); 
  line(320,0,320,479); 
  getch(); 
  break; 
 
  case 4: 
      cleardevice(); 
      for(i=0;i<n;i++) 
      line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]); 
      line(0,240,639,240); 
      line(320,0,320,479); 
     gotoxy(1,1); 
     printf("Enter the angle of rotation\n\t"); 
     scanf("%f",&ang); 
     ang=ang*0.01745; 
     gotoxy(1,3); 
     printf("Enter point of rotation\n\t"); 
     scanf("%f %f",&x,&y); 
     gotoxy(1,5); 
     printf("1.clockwise  2.anticlockwise\n\t"); 
     scanf("%d",&k); 
     si=sin(ang); 
     co=cos(ang); 
     for(i=0;i<n+1;i++) 
 { 
   c[i][0]=a[i][0]; 
   c[i][1]=a[i][1]; 
   c[i][2]=1; 
 } 
           b[0][0]=co; 
      b[0][1]=si; 
      b[0][2]=0; 
      b[1][0]=(-si); 
      b[1][1]=co; 
      b[1][2]=0; 
      b[2][0]=(-x*co)+(y*si)+x; 
      b[2][1]=(-x*si)-(y*co)+y; 
      b[2][2]=1; 
      
 
 
      if(k==1) 
      { 
 b[0][1]=(-si); 
 b[1][0]=(si); 
 b[2][0]=(-x*co)-(y*si)+x; 
 b[2][1]=(-x*si)+(y*co)+y; 
      } 
 
     for(i=0;i<n+1;i++) 
    { 
       for(j=0;j<3;j++) 
   { 
     a[i][j] = 0 ; 
     for(k=0;k<3;k++) 
     a[i][j] = a[i][j] + c[i][k] * b[k][j] ; 
   } 
     } 
 
     cleardevice(); 
     for(i=0;i<n;i++) 
       line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]); 
       line(0,240,639,240); 
       line(320,0,320,479); 
       getch(); 
       break; 
 
    case 5: 
      cleardevice(); 
      for(i=0;i<n;i++) 
      line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]); 
      line(0,240,639,240); 
      line(320,0,320,479); 
      gotoxy(1,1); 
      printf("\n1.Reflection about Y-axis"); 
      printf("\n2.Reflection about X-axis"); 
      printf("\n3.Reflection about origin"); 
      printf("\n4.Reflection about line y=x"); 
      printf("\n5.Reflection about line y=-x"); 
      printf("\nEnter your choice:"); 
      scanf("%d",&ch); 
     
 
 
 
 
 
  switch(ch) 
      { 
  case 1: 
      for(i=0;i<n+1;i++) 
        a[i][0]=a[i][0]*(-1); 
       /* Plot the polygon */ 
       cleardevice(); 
       for(i=0;i<n;i++) 
       line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]); 
       line(0,240,639,240); 
       line(320,0,320,479); 
       getch(); 
       break; 
 
   case 2: 
       for(i=0;i<n+1;i++) 
        a[i][1]=a[i][1]*(-1); 
        cleardevice(); 
       for(i=0;i<n;i++) 
       line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]); 
       line(0,240,639,240); 
       line(320,0,320,479); 
       getch(); 
    break; 
 
  case 3: 
      for(i=0;i<n+1;i++) 
      { 
        a[i][1]=a[i][1]*(-1); 
        a[i][0]=a[i][0]*(-1); 
      } 
        cleardevice(); 
       for(i=0;i<n;i++) 
       line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]); 
       line(0,240,639,240); 
       line(320,0,320,479); 
       getch(); 
    break; 
 
   case 4: 
      for(i=0;i<n+1;i++) 
      { 
       temp=a[i][0]; 
       a[i][0]=a[i][1]; 
       a[i][1]=temp; 
      } 
       cleardevice(); 
       for(i=0;i<n;i++) 
       line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]); 
       line(0,240,639,240); 
       line(320,0,320,479); 
       line(0,479,639,0); 
       getch(); 
    break; 
 
   case 5: 
      for(i=0;i<n+1;i++) 
      { 
       temp=a[i][0]; 
       a[i][0]=a[i][1]; 
       a[i][1]=temp; 
      } 
     
              for(i=0;i<n+1;i++) 
      { 
        a[i][1]=a[i][1]*(-1); 
        a[i][0]=a[i][0]*(-1); 
      } 
              cleardevice(); 
       for(i=0;i<n;i++) 
       line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]); 
       line(0,240,639,240); 
       line(320,0,320,479); 
       line(0,0,639,479); 
       getch(); 
    break; 
  default: 
    break; 
      } 
      break; 
 
    case 6: 
       cleardevice(); 
      for(i=0;i<n;i++) 
      line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]); 
      line(0,240,639,240); 
      line(320,0,320,479); 
      gotoxy(1,1); 
      printf("\n1.X shear with y reference line"); 
      printf("\n2.Y shear with x reference line"); 
 
 
      printf("\nEnter your choice:"); 
      scanf("%d",&ch); 
      switch(ch) 
      { 
 
       case 1: 
   printf("\nEnter the x-shear parameter value:"); 
   scanf("%f",&temp); 
   printf("\nEnter the yref line"); 
   scanf("%f",&ty); 
       b[0][0]=1; 
      b[0][1]=0; 
      b[0][2]=0; 
      b[1][0]=temp; 
      b[1][1]=1; 
      b[1][2]=0; 
      b[2][0]=(-temp)*(ty); 
      b[2][1]=0; 
      b[2][2]=1; 
 
     for(i=0;i<n+1;i++) 
     a[i][2]=1; 
  
  for(i=0;i<n+1;i++) 
    { 
       for(j=0;j<3;j++) 
   { 
     c[i][j] = 0 ; 
     for(k=0;k<3;k++) 
     c[i][j] = c[i][j] + a[i][k] * b[k][j] ; 
   } 
     } 
 
     cleardevice(); 
     for(i=0;i<n;i++) 
       line(320+c[i][0],240-c[i][1],320+c[i+1][0],240-c[i+1][1]); 
       line(0,240,639,240); 
       line(320,0,320,479); 
       getch(); 
 break; 
 
       case 2: 
   printf("\nEnter the y-shear parameter value:"); 
   scanf("%f",&temp); 
              printf("\nEnter the xref line"); 
   scanf("%f",&tx); 
                 b[0][0]=1; 
      b[0][1]=temp; 
      b[0][2]=0; 
      b[1][0]=0; 
      b[1][1]=1; 
      b[1][2]=0; 
      b[2][0]=0; 
      b[2][1]=(-temp)*(tx); 
      b[2][2]=0; 
     for(i=0;i<n+1;i++) 
     a[i][2]=1; 
  
  for(i=0;i<n+1;i++) 
    { 
       for(j=0;j<3;j++) 
   { 
     c[i][j] = 0 ; 
     for(k=0;k<3;k++) 
     c[i][j] = c[i][j] + a[i][k] * b[k][j] ; 
   } 
     } 
 
          cleardevice(); 
     for(i=0;i<n;i++) 
       line(320+c[i][0],240-c[i][1],320+c[i+1][0],240-c[i+1][1]); 
       line(0,240,639,240); 
       line(320,0,320,479); 
       getch(); 
 break; 
 
case 7: 
    exit(1); 
    closegraph(); 
    restorecrtmode(); 
    break; 
    default: break; 
    } 
}
```


**Output :**

## Polygon

![1](https://github.com/user-attachments/assets/529ce2e3-c1a1-47e8-ae75-9531b53b2ba9)

![2](https://github.com/user-attachments/assets/80530c7b-8abf-47fb-830f-ad31d679d3cb)

![3](https://github.com/user-attachments/assets/c844c7c3-eb7c-47ef-87e7-136951c0b0c0)

## Translation

![4](https://github.com/user-attachments/assets/5e352d09-8719-4b1f-80bc-86a1f2ef9cb5)

![5](https://github.com/user-attachments/assets/a0ef0b7f-1e83-4348-9683-ab79331f48e7)

![6](https://github.com/user-attachments/assets/7994228d-402e-40e2-9345-f44839e7d5ab)

## Scaling

![7](https://github.com/user-attachments/assets/30d9080e-a284-4f6f-8c9a-037d43bad24a)

![8](https://github.com/user-attachments/assets/0ebff6f4-5f81-41f3-b832-738127f24666)

![9](https://github.com/user-attachments/assets/63738bde-4423-49e1-a814-7d4fe8b348c4)

## Rotaion
![10](https://github.com/user-attachments/assets/46189e55-093a-40c9-9e5c-9e7cf95663fb)

![11](https://github.com/user-attachments/assets/1faedc50-b8c4-4f24-a4dc-b9f2a8a284f3)

![12](https://github.com/user-attachments/assets/51adadd8-87ba-4235-bd79-3058897f7b64)

## Reflection

![13](https://github.com/user-attachments/assets/9203087a-51d2-475d-8f10-49c4f1236b61)

![14](https://github.com/user-attachments/assets/a94e8c0b-5891-433f-9ace-0054374412dc)

![15](https://github.com/user-attachments/assets/44941e65-42a7-43f7-8958-9960320d2f76)

## Shearing

![16](https://github.com/user-attachments/assets/9d28d5a3-9a0a-4a70-9801-ce1f72ec565f)

![17](https://github.com/user-attachments/assets/71336f3d-d4b5-48bd-8b0c-eae43374029b)

![18](https://github.com/user-attachments/assets/80dbf182-ff61-4b96-b9be-9dd0f4999a07)

**Result :**
A c program to implement 2D transformation of image was was written and executed successfully.
