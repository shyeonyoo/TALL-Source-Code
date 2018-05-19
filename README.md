# TALL-Source-Code
TALL Source Code
#include <stdio.h>

//#include <windows.h>



#define SIZE 500005

#define INT_MAX 2147483647



int n, a, cnt = 1;

int middle, begin, end, d[SIZE+1];//d->STACK

__int64 ans;



void process()

{

 int i;

 d[0] = INT_MAX;

 for(i=0;i<n;i++) {

  scanfs("%d",&a);

  begin = 0;

  end = cnt-1;

  while (true) {

   if(begin > end)

    break;

   middle = (begin+end)/2;

   if(d[middle] < a)

    end = middle-1;

   if(d[middle] > a)

    begin = middle+1;

   if(d[middle] == a)

    end = middle-1;

  }



  if(begin >= 2)

   ans++;

  ans += cnt-begin;

  ////////////////////////////

  begin = 0;

  end = cnt-1;

  while (true) {

   if(begin > end)

    break;

   middle = (begin+end)/2;

   if(d[middle] < a)

    end = middle-1;

   if(d[middle] > a)

    begin = middle+1;

   if(d[middle] == a)

    begin = middle+1;

  }

  cnt = begin+1;

  d[begin] = a;

 }

}



int main()

{

 freopen("INPUT.TXT","r",stdin);

 freopen("OUTPUT.TXT","w",stdout);

 scanfs("%d",&n);

 process();

 printfs("%I64d",ans);

 return 0;

}

