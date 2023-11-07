#palindrom 

package array;
import java.util.*;
public class Array_list {
public static void main(String[] args) {
Scanner sc = new Scanner(System.in);
System.out.println("enter number: ");
int n = sc.nextInt();
int sum = 0;
int temp = n;
while (n>0)
{
int row = n%10;
Sum = sum 10+rem;
n = n/10;
}
if (sum==temp)
{
System.out.println("palindrome");
}
else{
System.out.println("not palindrome");
}

# armstron 

package array;
import java.util.*;
public class Array_list {
public static void main(String[] args) {
Scanner sc = new Scanner(System.in);
System.out.println("enter number: ");
int n = sc.nextInt();
int sum = 0;
int temp = n;
while(n>0)
int rem n%10;
I am = am+rem*rem*rem;
n = n/10;
}
if (sum==temp)
{
}
System.out.println("armstrong");
else{
System.out.println("not armstrong");
}
}


# display its binary equivalent.

package experment1;
import java.util.Scanner;
public class sample5 {
public static void main(String[] args) {
Scanner sc=new Scanner(System.in);
System.out.println("enter the number:");
int N = sc.nextInt();
int r;
int m=1;
int binary=0;
while ( N > 0)
{
r = N % 2;
N = N / 2;
binary = binary + (r*m);
m = m * 10;
}
System.out.println(binary);
}
}

# fibbinochi

package array;
import java.util.*;
public class Array_list {
public static void main(String[] args) {
Scanner sc = new Scanner(System.in);
int a = 0;
int b = 1;
System.out.println("enter number: ");
int n = sc.nextInt();
for (int i=0;i<n;i++)
{
System.out.println(a);
int c = a+b;
a = b
b = c
}
}

# n Array. Find out the sum of all the odd numbers and even numbers

importjava.util.Scanner;
public class sample1 {
public static void main(String[] args) {
int i;
Scanner sc = new Scanner(System.in);
System.out.print("Enter the size of an array : ");
int size = sc.nextInt();
int a[] = new int[size];
System.out.println("Enter the " + size + " elements");
for( i=0; i<a.length; i++)
{
a[i] = sc.nextInt();
}
System.out.println("The elements are : ");
for( i=0; i<a.length; i++)
{
System.out.print(a[i]+" ");
}
System.out.println("\nThe list of Odd & Even");
int even=0, odd=0;
for(i=0; i<a.length; i++)
{
if(a[i] %2 == 0)
even += a[i];
else
odd += a[i];
}
System.out.println("Even : " + even);
System.out.println("Odd :" + odd);
}

# even or odd

import java.util.Scanner;
public class Endsem
public static void main(String[] args) {
Scanner Sc= new Scanner(System.in); System.out.println("Enter any number: ");
int num = sc.nextInt();
if (num%2==0) {
System.out.println("Even");
}
else {
System.out.println("odd");
}

}

# Display all duplicate characters from the array vovles and consonants
import java.util.*;
public class Sample2 {
public static void main(String[] args) {
Scanner sc = new Scanner(System.in); char[] v = { 'a', 'e', 'i', 'o', 'u' };
int vc = 0, n, flag = 0, dcc = 0; char arr[];
char dcarr[];
System.out.println("Enter the Size of the array: "); n = sc.nextInt();
arr = new char[n]; dcarr = new char[n];
System.out.println("Enter the characters"); for (int i = 0; i < n; i++) {
arr[i] = sc.next().charAt(0); for (int j = 0; j < 5; j++)
if (arr[i] == v[j])
vc = vc + 1;
}
for (int i = 0; i < n; i++) {
for (int j = 0; j < n; j++) { if (i != j) {
if (arr[i] == arr[j]) {
flag = 0;
for (int k = 0; k < n; k++) {
if (dcarr[k] == arr[i])
flag = 1;
}
if (flag != 1) {
dcarr[dcc] = arr[i]; dcc = dcc + 1;
}
}
}
}
}
System.out.print("The Duplicate Characters are : "); for (int i = 0; i <
dcc; i++)
System.out.print(dcarr[i] + " "); System.out.println("");
System.out.println("Number of vowels: " + vc);
System.out.println("Number of consonants: " + (n-vc));
}
}

# 3 arrays where first array stores all small alphabetical letters,

import java.util.Scanner;
import java.util.Random;
public class Sample3 {
public static void main(String[] args) {
Random random = new Random();
random.setSeed(1234567890);
Scanner in = new Scanner(System.in);
int l;
String password="";
char[] small =
{'a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z'};
char[] capital= {'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I','J', 'K', 'L', 'M',
'N', 'O', 'P', 'Q','R','S','T', 'U', 'V','W', 'X', 'Y', 'Z'};
int[] numbers = {0,1,2,3,4,5,6,7,8,9};
System.out.println("Enter the Length of the Password");
l = in.nextInt();
for(int i=0;i<l;i++){
switch(random.nextInt(3)) {
case 0:
case 1:
password = password + capital[random.nextInt(26)];
break;
case 2:
password = password +
(char)(numbers[random.nextInt(10)]+'0');
break;
}
}
System.out.println(password);
}
}

# Write the java program to get a String from the user and print the number of Letters and Digits

import java.util.Scanner;
public class sample1 {
public static void main(String[] args)
{
Scanner sc = new Scanner(System.in);
System.out.println("Enter a sentence:");
char[] s = sc.nextLine().toCharArray();
int L=0 , D=0;
boolean l,d;
for (char ch:s)
{
if(Character.isAlphabetic(ch))
{
L++;
}
else if(Character.isDigit(ch))
{
D++;
}
}
System.out.println("LETTER: "+ L);
System.out.println("DIGITS: "+ D);
}
}

# print the number ofspaces, words
import java.util.Scanner;
public class sample2 {
public static void main(String[] args)
{
Scanner sc = new Scanner(System.in);
System.out.println("Enter a paragraph:");
String s=sc.nextLine();
int scount=0,wcount=0,ccount=0;
String[] l=s.split("\n");
char[] ch=new char[s.length()];
for(inti=0;i<s.length();i++)
{
char c=s.charAt(i);
if(((i>0)&& (s.charAt(i)!=' ') &&(s.charAt(i-1)==' '))
|| ((s.charAt(i)!=' ')&&(i==0)))
{
wcount++;
}
if(c!=32)
{
ccount++;
}
else if(c==32)
{
scount++;
}
/*else if(ch=='\n')
{
lcount++;
}*/
}
System.out.println("Number of spaces:"+scount);
System.out.println("Number of words:"+wcount);
System.out.println("Number of characters:"+ccount);
System.out.println("Number of lines:"+l.length);
}
}

# string from the user and print The largest and shortest words

import java.util.Scanner;
public class sample3 {
public static void main(String[] args)
{
Scanner sc = new Scanner(System.in);
System.out.println("Enter a paragraph:");
String s = sc.nextLine();
String[] Sarr = s.split(" ");
String Greatest, Smallest;
int gl, sl;
Greatest = Sarr[0];
Smallest = Sarr[0];
sl = Sarr[0].length();
gl = Sarr[0].length();
for(String S : Sarr)
{
if(S.length() > gl)
{
gl = S.length();
Greatest = S;
}
else if(S.length() < sl)
{
sl = S.length();
Smallest = S;
}
}
System.out.println("Greatest word: "+ Greatest + " - " + gl + "
Characters");
System.out.println("Shortest word: "+ Smallest + " - " + sl + "
Characters");
}
}

# multiplication table of number 5 for every 3 seconds
import java.util.Scanner;
class thread implements Runnable {
public void run() {
Scanner scan=new Scanner(System.in);
System.out.print("Enter Table : ");
int num=scan.nextInt();
for (int i=1;i<=10;i++) {
System.out.println(num+"x"+i+"="+(num*i));
try {
Thread.sleep(3000);
}
catch (Exception e) {
System.out.println(e);
}
}
System.out.println("Program Executed
Successfully");
scan.close();
}
}
public class table {
public static void main(String[] args) {
thread obj=new thread();
Thread thread=new Thread(obj);
thread.start();
}
}

