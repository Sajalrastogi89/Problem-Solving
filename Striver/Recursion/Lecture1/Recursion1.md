package Striver.Recursion.Lecture1;

import java.util.Scanner;
public class Recursion1 {
public static void main(String[] args) {
   int n;
   Scanner sc=new Scanner(System.in);
   n=sc.nextInt();
   Recursion1 obj=new Recursion1();
   obj.recursivePrint(n,1);
}

void recursivePrint(int n,int m) {
if(m>n)
return;
System.out.println(m);
recursivePrint(n, m+1);
}    
}