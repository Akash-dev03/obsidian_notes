### 1) Check if a Number is Even or Odd

```bash
# Pseudocode
read n
if n % 2 == 0 then print "Even" else print "Odd"
```

```python
# Python
n = int(input().strip())
print("Even" if n % 2 == 0 else "Odd")
```

```javascript
// JavaScript (browser Node: adapt input)
let n = Number(prompt("n:"));
console.log(n % 2 === 0 ? "Even" : "Odd");
```

```cpp
// C++ (STL)
#include <bits/stdc++.h>
using namespace std;
int main(){ long long n; if(!(cin>>n)) return 0; cout<<(n%2==0?"Even":"Odd")<<"\n"; }
```

```cpp
// C++ (no STL) - use stdio
#include <cstdio>
int main(){ long long n; if(scanf("%lld",&n)!=1) return 0; puts(n%2==0?"Even":"Odd"); }
```

```java
// Java
import java.util.*;
class Main{
  public static void main(String[] args){
    Scanner sc=new Scanner(System.in);
    long n=sc.nextLong();
    System.out.println(n%2==0?"Even":"Odd");
  }
}
```

---

### 2) Find the Largest of Two Numbers

**Pseudocode**

```bash
read a, b
if a > b then print a else print b
```

```python
# Python
a,b = map(int,input().split())
print(a if a>b else b)
```

```javascript
// JavaScript
let arr = prompt("a b").split(/\s+/).map(Number);
console.log(Math.max(arr[0], arr[1]));
```

```cpp
// C++ (STL)
#include <bits/stdc++.h>
using namespace std;
int main(){ int a,b; if(!(cin>>a>>b)) return 0; cout<<max(a,b)<<"\n"; }
```

```cpp
// C++ (no STL)
#include <cstdio>
int main(){ int a,b; if(scanf("%d %d",&a,&b)!=2) return 0; printf("%d\n", a>b? a: b); }
```

```java
// Java
import java.util.*;
class Main{
  public static void main(String[] args){
    Scanner sc=new Scanner(System.in);
    int a=sc.nextInt(), b=sc.nextInt();
    System.out.println(Math.max(a,b));
  }
}
```

---

### 3) Sum of Digits of a Number

**Pseudocode**

```bash
read n (as string or integer)
sum = 0
for each digit d in n: sum += int(d)
print sum
```

```python
# Python
s = input().strip()
print(sum(int(ch) for ch in s if ch.isdigit()))
```

```javascript
// JavaScript
let s = prompt("number:");
console.log([...s].reduce((acc,ch)=> acc + (/\d/.test(ch)?Number(ch):0), 0));
```

```cpp
// C++ (STL)
#include <bits/stdc++.h>
using namespace std;
int main(){ string s; if(!(cin>>s)) return 0; long long sum=0; for(char c:s) if(isdigit(c)) sum+=c-'0'; cout<<sum<<"\n"; }
```

```cpp
// C++ (no STL)
#include <cstdio>
#include <cstring>
int main(){
  char s[201];
  if(scanf("%200s", s)!=1) return 0;
  int sum=0;
  for(int i=0; s[i]; ++i) if(s[i]>='0' && s[i]<='9') sum += s[i]-'0';
  printf("%d\n", sum);
}
```

```java
// Java
import java.util.*;
class Main{
  public static void main(String[] args){
    Scanner sc=new Scanner(System.in);
    String s=sc.next();
    int sum=0;
    for(char c: s.toCharArray()) if(Character.isDigit(c)) sum+= c-'0';
    System.out.println(sum);
  }
}
```

---

### 4) Reverse a String

**Pseudocode**

```
read s
print reverse(s)
```

```python
# Python
s = input().rstrip("\n")
print(s[::-1])
```

```javascript
// JavaScript
let s = prompt("string:");
console.log(s.split("").reverse().join(""));
```

```cpp
// C++ (STL)
#include <bits/stdc++.h>
using namespace std;
int main(){ string s; getline(cin, s); reverse(s.begin(), s.end()); cout<<s<<"\n"; }
```

```cpp
// C++ (no STL)
#include <cstdio>
#include <cstring>
int main(){
  char s[1001];
  if(!fgets(s, 1001, stdin)) return 0;
  int n = strlen(s);
  if(n>0 && s[n-1]=='\n') s[--n]=0;
  for(int i=n-1;i>=0;--i) putchar(s[i]);
  putchar('\n');
}
```

```java
// Java
import java.util.*;
class Main{
  public static void main(String[] args){
    Scanner sc=new Scanner(System.in);
    String s = sc.nextLine();
    System.out.println(new StringBuilder(s).reverse().toString());
  }
}
```

---

### 5) Count Vowels and Consonants in a String

**Pseudocode**

```
read s
v=c=0
for each ch in s:
  if isalpha(ch):
    ch=lower(ch)
    if ch in {a,e,i,o,u} then v++ else c++
print v, c
```

```python
# Python
s = input().lower()
v = sum(1 for ch in s if ch.isalpha() and ch in "aeiou")
c = sum(1 for ch in s if ch.isalpha() and ch not in "aeiou")
print(v, c)
```

```javascript
// JavaScript
let s = prompt("text:").toLowerCase();
let vowels = "aeiou";
let v = 0, c = 0;
for(let ch of s){
  if(/[a-z]/.test(ch)){
    if(vowels.includes(ch)) v++; else c++;
  }
}
console.log(v, c);
```

```cpp
// C++ (STL)
#include <bits/stdc++.h>
using namespace std;
int main(){
  string s; getline(cin,s);
  int v=0,c=0;
  for(char ch: s){
    if(isalpha(ch)){
      char x = tolower(ch);
      if(string("aeiou").find(x)!=string::npos) ++v; else ++c;
    }
  }
  cout<<v<<" "<<c<<"\n";
}
```

```cpp
// C++ (no STL)
#include <cstdio>
#include <cctype>
int main(){
  char s[1001];
  if(!fgets(s,1001,stdin)) return 0;
  int v=0,cnt=0;
  for(int i=0;s[i];++i){
    char ch=s[i];
    if(isalpha((unsigned char)ch)){
      char x = tolower((unsigned char)ch);
      if(x=='a'||x=='e'||x=='i'||x=='o'||x=='u') ++v; else ++cnt;
    }
  }
  printf("%d %d\n", v, cnt);
}
```

```java
// Java
import java.util.*;
class Main{
  public static void main(String[] args){
    Scanner sc=new Scanner(System.in);
    String s = sc.nextLine().toLowerCase();
    int v=0,c=0;
    for(char ch: s.toCharArray()){
      if(Character.isLetter(ch)){
        if("aeiou".indexOf(ch)>=0) v++; else c++;
      }
    }
    System.out.println(v+" "+c);
  }
}
```

---

### 6) Check Palindrome String

_(Now included for all languages — you asked this specifically)_

**Pseudocode**

```
read s
normalize s (optional: lower and remove nonletters)
if s == reverse(s) then print "Palindrome" else print "Not Palindrome"
```

```python
# Python
s = input().strip()
print("Palindrome" if s == s[::-1] else "Not Palindrome")
```

```javascript
// JavaScript
let s = prompt("string:");
let rev = s.split("").reverse().join("");
console.log(s === rev ? "Palindrome" : "Not Palindrome");
```

```cpp
// C++ (STL)
#include <bits/stdc++.h>
using namespace std;
int main(){
  string s; getline(cin,s);
  string t = s; reverse(t.begin(), t.end());
  cout << (s==t ? "Palindrome" : "Not Palindrome") << "\n";
}
```

```cpp
// C++ (no STL)
#include <cstdio>
#include <cstring>
int main(){
  char s[1001];
  if(!fgets(s,1001,stdin)) return 0;
  int n = strlen(s);
  if(n>0 && s[n-1]=='\n') s[--n]=0;
  int i=0,j=n-1; int ok=1;
  while(i<j){ if(s[i]!=s[j]){ ok=0; break; } ++i; --j; }
  puts(ok ? "Palindrome" : "Not Palindrome");
}
```

```java
// Java
import java.util.*;
class Main{
  public static void main(String[] args){
    Scanner sc=new Scanner(System.in);
    String s = sc.nextLine();
    String t = new StringBuilder(s).reverse().toString();
    System.out.println(s.equals(t) ? "Palindrome" : "Not Palindrome");
  }
}
```

---

### 7) Find Factorial of a Number

**Pseudocode**

```
read n
fact = 1
for i from 1 to n: fact *= i
print fact
```

```python
# Python
n = int(input().strip())
fact = 1
for i in range(2, n+1): fact *= i
print(fact)
```

```javascript
// JavaScript
let n = Number(prompt("n:"));
let fact = 1;
for(let i=2;i<=n;i++) fact *= i;
console.log(fact);
```

```cpp
// C++ (STL)
#include <bits/stdc++.h>
using namespace std;
int main(){ long long n; if(!(cin>>n)) return 0; long long f=1; for(long long i=2;i<=n;i++) f*=i; cout<<f<<"\n"; }
```

```cpp
// C++ (no STL)
#include <cstdio>
int main(){ long long n; if(scanf("%lld",&n)!=1) return 0; long long f=1; for(long long i=2;i<=n;i++) f*=i; printf("%lld\n", f); }
```

```java
// Java
import java.util.*;
class Main{
  public static void main(String[] args){
    Scanner sc=new Scanner(System.in);
    long n = sc.nextLong();
    long f=1;
    for(long i=2;i<=n;i++) f*=i;
    System.out.println(f);
  }
}
```

---

### 8) Print Fibonacci Series (n terms)

**Pseudocode**

```
read n
a=0; b=1
repeat n times: print a; (a,b)=(b,a+b)
```

```python
# Python
n = int(input().strip())
a,b = 0,1
for _ in range(n):
    print(a, end=" ")
    a,b = b, a+b
print()
```

```javascript
// JavaScript
let n = Number(prompt("n:"));
let a=0,b=1;
let out = [];
for(let i=0;i<n;i++){ out.push(a); [a,b]=[b,a+b]; }
console.log(out.join(" "));
```

```cpp
// C++ (STL)
#include <bits/stdc++.h>
using namespace std;
int main(){ int n; if(!(cin>>n)) return 0; long long a=0,b=1; for(int i=0;i<n;i++){ cout<<a<<(i+1==n?'\n':' '); auto t=a+b; a=b; b=t; } }
```

```cpp
// C++ (no STL)
#include <cstdio>
int main(){
  int n;
  if(scanf("%d",&n)!=1) return 0;
  long long a=0,b=1;
  for(int i=0;i<n;i++){
    if(i) putchar(' ');
    printf("%lld", a);
    long long t=a+b; a=b; b=t;
  }
  puts("");
}
```

```java
// Java
import java.util.*;
class Main{
  public static void main(String[] args){
    int n = new Scanner(System.in).nextInt();
    long a=0,b=1;
    for(int i=0;i<n;i++){
      System.out.print(a + (i==n-1? "\n":" "));
      long t=a+b; a=b; b=t;
    }
  }
}
```

---

### 9) Find Minimum Value in List

**Pseudocode**

```
read list
min = +inf
for each x in list: if x < min then min = x
print min
```

```python
# Python
arr = list(map(int, input().split()))
print(min(arr))
```

```javascript
// JavaScript
let arr = prompt("nums:").split(/\s+/).map(Number);
console.log(Math.min(...arr));
```

```cpp
// C++ (STL)
#include <bits/stdc++.h>
using namespace std;
int main(){ vector<long long> a; long long x; while(cin>>x) a.push_back(x); if(a.empty()) return 0; cout<< *min_element(a.begin(), a.end()) <<"\n"; }
```

```cpp
// C++ (no STL)
#include <cstdio>
int main(){
  long long x;
  if(scanf("%lld", &x)!=1) return 0;
  long long mn = x;
  while(scanf("%lld",&x)==1) if(x < mn) mn = x;
  printf("%lld\n", mn);
}
```

```java
// Java
import java.util.*;
class Main{
  public static void main(String[] args){
    Scanner sc=new Scanner(System.in);
    List<Integer> a = new ArrayList<>();
    while(sc.hasNextInt()) a.add(sc.nextInt());
    if(a.size()==0) return;
    System.out.println(Collections.min(a));
  }
}
```

---

### 10) Check if Character is Alphabet

**Pseudocode**

```
read ch
if ('a' <= ch <= 'z') or ('A' <= ch <= 'Z') then true else false
```

```python
# Python
ch = input().strip()
print(len(ch)==1 and ch.isalpha())
```

```javascript
// JavaScript
let ch = prompt("char:");
console.log(/^[A-Za-z]$/.test(ch));
```

```cpp
// C++ (STL)
#include <bits/stdc++.h>
using namespace std;
int main(){ char c; if(!(cin>>c)) return 0; cout<<(isalpha((unsigned char)c) ? "true":"false")<<"\n"; }
```

```cpp
// C++ (no STL)
#include <cstdio>
#include <cctype>
int main(){
  int c = getchar();
  while(c=='\n' || c==' ' || c=='\t') c=getchar();
  if(c==EOF) return 0;
  putchar(isalpha(c)?'1':'0');
  putchar('\n');
}
```

```java
// Java
import java.util.*;
class Main{
  public static void main(String[] args){
    char c = new Scanner(System.in).next().charAt(0);
    System.out.println(Character.isLetter(c));
  }
}
```

---

### 11) Count Words in a Sentence

**Pseudocode**

```
read line
split by whitespace
print number of tokens
```

```python
# Python
s = input().strip()
print(0 if not s else len(s.split()))
```

```javascript
// JavaScript
let s = prompt("sentence:").trim();
console.log(s? s.split(/\s+/).length : 0);
```

```cpp
// C++ (STL)
#include <bits/stdc++.h>
using namespace std;
int main(){ string s; getline(cin,s); if(s.find_first_not_of(" \t\n")==string::npos){ cout<<0<<"\n"; return 0;} stringstream ss(s); string w; int cnt=0; while(ss>>w) ++cnt; cout<<cnt<<"\n"; }
```

```cpp
// C++ (no STL)
#include <cstdio>
#include <cstring>
int main(){
  char s[2001];
  if(!fgets(s,2001,stdin)) return 0;
  int n=strlen(s); if(n>0 && s[n-1]=='\n') s[--n]=0;
  int i=0, cnt=0;
  while(i<n){
    while(i<n && (s[i]==' '||s[i]=='\t')) ++i;
    if(i<n) { ++cnt; while(i<n && s[i]!=' ' && s[i]!='\t') ++i; }
  }
  printf("%d\n", cnt);
}
```

```java
// Java
import java.util.*;
class Main{
  public static void main(String[] args){
    Scanner sc=new Scanner(System.in);
    String s = sc.nextLine().trim();
    if(s.isEmpty()) System.out.println(0);
    else System.out.println(s.split("\\s+").length);
  }
}
```

---

### 12) Remove Duplicates from List (preserve order)

**Pseudocode**

```
read list
seen = empty set
out = []
for x in list:
  if x not in seen: append x to out; add x to seen
print out
```

```python
# Python
arr = list(map(int, input().split()))
seen = set(); out=[]
for x in arr:
    if x not in seen:
        seen.add(x); out.append(x)
print(out)
```

```javascript
// JavaScript
let arr = prompt("nums:").split(/\s+/);
let seen = new Set(), out=[];
for(let x of arr) if(!seen.has(x)){ seen.add(x); out.push(x); }
console.log(out.join(" "));
```

```cpp
// C++ (STL)
#include <bits/stdc++.h>
using namespace std;
int main(){ vector<long long> a; long long x; while(cin>>x) a.push_back(x); unordered_set<long long> seen; for(auto v: a) if(!seen.count(v)){ cout<<v<<" "; seen.insert(v);} cout<<"\n"; }
```

```cpp
// C++ (no STL)
#include <cstdio>
#include <cstring>
// Simple version: works for small integers in limited range; for general approach we need more code.
// We'll do O(n^2) naive duplicate check without dynamic containers.
int main(){
  long long arr[10000];
  int n=0;
  while(scanf("%lld",&arr[n])==1) n++;
  for(int i=0;i<n;i++){
    int seen=0;
    for(int j=0;j<i;j++) if(arr[j]==arr[i]){ seen=1; break; }
    if(!seen) { printf("%lld ", arr[i]); }
  }
  puts("");
}
```

```java
// Java
import java.util.*;
class Main{
  public static void main(String[] args){
    Scanner sc=new Scanner(System.in);
    List<Integer> a = new ArrayList<>();
    while(sc.hasNextInt()) a.add(sc.nextInt());
    Set<Integer> seen = new LinkedHashSet<>(a);
    for(int x: seen) System.out.print(x+" ");
    System.out.println();
  }
}
```

---

### 13) Check Prime Number

**Pseudocode**

```
read n
if n <=1 print "Not Prime"
for i from 2 to sqrt(n):
  if n % i == 0: print "Not Prime" and exit
print "Prime"
```

```python
# Python
n = int(input().strip())
if n<=1:
    print("Not Prime")
else:
    import math
    is_prime = True
    for i in range(2, int(math.isqrt(n))+1):
        if n % i == 0:
            is_prime = False
            break
    print("Prime" if is_prime else "Not Prime")
```

```javascript
// JavaScript
let n = Number(prompt("n:"));
if(n<=1){ console.log("Not Prime"); }
else {
  let isPrime=true;
  for(let i=2;i*i<=n;i++) if(n%i===0){ isPrime=false; break; }
  console.log(isPrime? "Prime":"Not Prime");
}
```

```cpp
// C++ (STL)
#include <bits/stdc++.h>
using namespace std;
int main(){
  long long n; if(!(cin>>n)) return 0;
  if(n<=1){ cout<<"Not Prime\n"; return 0;}
  for(long long i=2;i*i<=n;i++) if(n%i==0){ cout<<"Not Prime\n"; return 0; }
  cout<<"Prime\n";
}
```

```cpp
// C++ (no STL)
#include <cstdio>
int main(){
  long long n; if(scanf("%lld",&n)!=1) return 0;
  if(n<=1){ puts("Not Prime"); return 0; }
  for(long long i=2;i*i<=n;i++) if(n%i==0){ puts("Not Prime"); return 0; }
  puts("Prime");
}
```

```java
// Java
import java.util.*;
class Main{
  public static void main(String[] args){
    long n=new Scanner(System.in).nextLong();
    if(n<=1){ System.out.println("Not Prime"); return; }
    for(long i=2;i*i<=n;i++) if(n%i==0){ System.out.println("Not Prime"); return; }
    System.out.println("Prime");
  }
}
```

---

### 14) Count Occurrences of a Character

**Pseudocode**

```
read s
read ch
count = occurrences of ch in s
print count
```

```python
# Python
s = input()
ch = input().strip()
print(s.count(ch))
```

```javascript
// JavaScript
let s = prompt("string:");
let ch = prompt("char:");
console.log([...s].filter(c => c===ch).length);
```

```cpp
// C++ (STL)
#include <bits/stdc++.h>
using namespace std;
int main(){ string s; getline(cin,s); char ch; cin>>ch; cout<<count(s.begin(), s.end(), ch)<<"\n"; }
```

```cpp
// C++ (no STL)
#include <cstdio>
#include <cstring>
int main(){
  char s[2001], ch;
  if(!fgets(s,2001,stdin)) return 0;
  if(scanf(" %c", &ch)!=1) return 0;
  int cnt=0;
  for(int i=0; s[i]; ++i) if(s[i]==ch) ++cnt;
  printf("%d\n", cnt);
}
```

```java
// Java
import java.util.*;
class Main{
  public static void main(String[] args){
    Scanner sc=new Scanner(System.in);
    String s = sc.nextLine();
    char ch = sc.next().charAt(0);
    int cnt=0;
    for(char c: s.toCharArray()) if(c==ch) cnt++;
    System.out.println(cnt);
  }
}
```

---

### 15) Find Second Largest Number

**Pseudocode**

```
read list
remove duplicates (optional)
find largest and second largest (scan once)
print second largest (or error if not exist)
```

```python
# Python
arr = list(map(int, input().split()))
uniq = sorted(set(arr))
if len(uniq) < 2:
    print("No second largest")
else:
    print(uniq[-2])
```

```javascript
// JavaScript
let arr = prompt("nums:").split(/\s+/).map(Number);
let s = Array.from(new Set(arr)).sort((a,b)=>a-b);
if(s.length<2) console.log("No second largest"); else console.log(s[s.length-2]);
```

```cpp
// C++ (STL)
#include <bits/stdc++.h>
using namespace std;
int main(){
  vector<long long> a; long long x; while(cin>>x) a.push_back(x);
  if(a.empty()){ cout<<"No second largest\n"; return 0; }
  sort(a.begin(), a.end());
  a.erase(unique(a.begin(), a.end()), a.end());
  if(a.size()<2) cout<<"No second largest\n"; else cout<<a[a.size()-2]<<"\n";
}
```

```cpp
// C++ (no STL) - O(n) two-pass naive for input as numbers until EOF
#include <cstdio>
#include <limits>
int main(){
  long long x;
  long long mx = LLONG_MIN, second = LLONG_MIN;
  bool found=false;
  while(scanf("%lld",&x)==1){
    found = true;
    if(x > mx){ second = mx; mx = x; }
    else if(x > second && x < mx) second = x;
  }
  if(!found || second==LLONG_MIN) printf("No second largest\n");
  else printf("%lld\n", second);
}
```

```java
// Java
import java.util.*;
class Main{
  public static void main(String[] args){
    Scanner sc=new Scanner(System.in);
    List<Integer> a=new ArrayList<>();
    while(sc.hasNextInt()) a.add(sc.nextInt());
    Set<Integer> s=new TreeSet<>(a);
    if(s.size()<2) System.out.println("No second largest");
    else {
      Iterator<Integer> it = s.descendingIterator();
      it.next(); System.out.println(it.next());
    }
  }
}
```

---

### 16) Swap Two Numbers (With and Without Third Variable)

**Pseudocode**

```
read a,b
# with third: t=a; a=b; b=t
# without: a=a+b; b=a-b; a=a-b  (watch overflow)
```

```python
# Python (without temp)
a,b = map(int,input().split())
a,b = b,a
print(a, b)
```

```javascript
// JavaScript (without temp via destructuring)
let [a,b] = prompt("a b").split(/\s+/).map(Number);
[a,b] = [b,a];
console.log(a,b);
```

```cpp
// C++ (STL) - with temp
#include <bits/stdc++.h>
using namespace std;
int main(){ int a,b; if(!(cin>>a>>b)) return 0; int t=a; a=b; b=t; cout<<a<<" "<<b<<"\n"; }
```

```cpp
// C++ (no STL) - without temp, using arithmetic
#include <cstdio>
int main(){
  long long a,b;
  if(scanf("%lld %lld",&a,&b)!=2) return 0;
  a = a + b;
  b = a - b;
  a = a - b;
  printf("%lld %lld\n", a, b);
}
```

```java
// Java
import java.util.*;
class Main{
  public static void main(String[] args){
    Scanner sc=new Scanner(System.in);
    int a=sc.nextInt(), b=sc.nextInt();
    // swap without temp
    a = a + b; b = a - b; a = a - b;
    System.out.println(a+" "+b);
  }
}
```

---

### 17) Convert List to String (concatenate elements)

**Pseudocode**

```
read list of tokens
join tokens into string (no separator or with separator)
print result
```

```python
# Python
arr = input().split()
print("".join(arr))     # no separator
# or print(" ".join(arr)) for space-separated
```

```javascript
// JavaScript
let arr = prompt("items:").split(/\s+/);
console.log(arr.join('')); // no separator
```

```cpp
// C++ (STL) - join without separator
#include <bits/stdc++.h>
using namespace std;
int main(){
  vector<string> v; string s;
  while(cin>>s) v.push_back(s);
  for(auto &x: v) cout<<x;
  cout<<"\n";
}
```

```cpp
// C++ (no STL)
#include <cstdio>
int main(){
  char s[201];
  int first = 1;
  while(scanf("%200s", s)==1){
    if(!first) ; // nothing, just concatenate
    printf("%s", s);
    first = 0;
  }
  printf("\n");
}
```

```java
// Java
import java.util.*;
class Main{
  public static void main(String[] args){
    Scanner sc=new Scanner(System.in);
    StringBuilder sb = new StringBuilder();
    while(sc.hasNext()) sb.append(sc.next());
    System.out.println(sb.toString());
  }
}
```

---

### 18) Find Length of Last Word

**Pseudocode**

```
read line
trim trailing spaces
find last space position
length = len(line) - last_space_pos - 1
print length
```

```python
# Python
s = input().rstrip()
parts = s.split()
print(len(parts[-1]) if parts else 0)
```

```javascript
// JavaScript
let s = prompt("line:").trim();
if(!s) console.log(0);
else console.log(s.split(/\s+/).pop().length);
```

```cpp
// C++ (STL)
#include <bits/stdc++.h>
using namespace std;
int main(){ string s; getline(cin,s);
  stringstream ss(s); string w; string last="";
  while(ss>>w) last=w;
  cout<<last.size()<<"\n";
}
```

```cpp
// C++ (no STL)
#include <cstdio>
#include <cstring>
int main(){
  char s[2001];
  if(!fgets(s,2001,stdin)) return 0;
  int n=strlen(s); if(n>0 && s[n-1]=='\n') s[--n]=0;
  while(n>0 && (s[n-1]==' '||s[n-1]=='\t')) s[--n]=0;
  int i=n-1;
  while(i>=0 && s[i]!=' ' && s[i]!='\t') --i;
  printf("%d\n", n - i - 1);
}
```

```java
// Java
import java.util.*;
class Main{
  public static void main(String[] args){
    String s = new Scanner(System.in).nextLine().trim();
    if(s.isEmpty()) System.out.println(0);
    else System.out.println(s.substring(s.lastIndexOf(' ')+1).length());
  }
}
```

---

### 19) Check if Two Strings Are Anagrams

**Pseudocode**

```
read a, b
if sort(a) == sort(b) then yes else no
```

```python
# Python
a = input().strip()
b = input().strip()
print("Anagram" if sorted(a) == sorted(b) else "Not Anagram")
```

```javascript
// JavaScript
let a = prompt("a:"), b = prompt("b:");
let sa = a.split("").sort().join(""), sb = b.split("").sort().join("");
console.log(sa===sb? "Anagram":"Not Anagram");
```

```cpp
// C++ (STL)
#include <bits/stdc++.h>
using namespace std;
int main(){
  string a,b; getline(cin,a); getline(cin,b);
  sort(a.begin(), a.end()); sort(b.begin(), b.end());
  cout<<(a==b? "Anagram":"Not Anagram")<<"\n";
}
```

```cpp
// C++ (no STL) - naive char counts for ASCII
#include <cstdio>
#include <cstring>
int main(){
  char a[1001], b[1001];
  if(!fgets(a,1001,stdin)) return 0;
  if(!fgets(b,1001,stdin)) return 0;
  int na=strlen(a), nb=strlen(b);
  if(na>0 && a[na-1]=='\n') a[--na]=0;
  if(nb>0 && b[nb-1]=='\n') b[--nb]=0;
  int ca[256]={0}, cb[256]={0};
  for(int i=0;a[i];++i) ca[(unsigned char)a[i]]++;
  for(int i=0;b[i];++i) cb[(unsigned char)b[i]]++;
  for(int i=0;i<256;i++) if(ca[i]!=cb[i]){ puts("Not Anagram"); return 0; }
  puts("Anagram");
}
```

```java
// Java
import java.util.*;
class Main{
  public static void main(String[] args){
    Scanner sc=new Scanner(System.in);
    String a=sc.nextLine(), b=sc.nextLine();
    char[] ca=a.toCharArray(), cb=b.toCharArray();
    Arrays.sort(ca); Arrays.sort(cb);
    System.out.println(Arrays.equals(ca,cb) ? "Anagram" : "Not Anagram");
  }
}
```

---

### 20) Print Unique Characters in Order (first occurrence preserved)

**Pseudocode**

```
read s
seen = empty set
for ch in s:
  if ch not in seen: print ch; add ch to seen
```

```python
# Python
s = input()
seen = set()
out = []
for ch in s:
    if ch not in seen:
        seen.add(ch); out.append(ch)
print("".join(out))
```

```javascript
// JavaScript
let s = prompt("s:");
let seen = new Set(), out=[];
for(let ch of s) if(!seen.has(ch)){ seen.add(ch); out.push(ch); }
console.log(out.join(''));
```

```cpp
// C++ (STL)
#include <bits/stdc++.h>
using namespace std;
int main(){
  string s; getline(cin,s);
  vector<bool> seen(256,false);
  for(char ch: s){
    unsigned char u = (unsigned char)ch;
    if(!seen[u]){ cout<<ch; seen[u]=true; }
  }
  cout<<"\n";
}
```

```cpp
// C++ (no STL)
#include <cstdio>
#include <cstring>
int main(){
  char s[2001];
  if(!fgets(s,2001,stdin)) return 0;
  int seen[256]={0};
  for(int i=0;s[i];++i){
    unsigned char u = s[i];
    if(!seen[u]){ putchar(u); seen[u]=1; }
  }
  putchar('\n');
}
```

```java
// Java
import java.util.*;
class Main{
  public static void main(String[] args){
    String s = new Scanner(System.in).nextLine();
    Set<Character> seen = new LinkedHashSet<>();
    StringBuilder sb = new StringBuilder();
    for(char ch: s.toCharArray()){
      if(seen.add(ch)) sb.append(ch);
    }
    System.out.println(sb.toString());
  }
}
```

---

If you want this delivered as a single `.md` file for download, tell me and I will paste a ready-to-save `.md` file content (or — if you prefer — I can compress it to a GitHub gist style snippet).