---
subject: rough
category:
---
Dec 18, 2022

>Links: [[rough]]

To Whom It May Concern,

I am writing to highly recommend [Nayan Ranjan Das] for the AI and Machine Learning internship at [CERN OpenLabs]. I have had the pleasure of working with [him] for the past year as his supervisor at [Amity University, Noida], and I have consistently been impressed by his aptitude for and passion for this field.

In the time that I have known [Nayan], he has consistently demonstrated a strong understanding of AI and machine learning concepts. They have completed several relevant coursework, including [Course] and [Course], and have consistently excelled in these classes. In addition, [Nayan] has completed several independent research projects in these areas, including a project on [Topic] that resulted in a published paper in [Publication].

In addition to their technical skills, [Nayan] is a highly motivated and dedicated individual. They consistently take on additional responsibilities and are always willing to go above and beyond to ensure that projects are completed to the best of their ability. Their strong work ethic and positive attitude would make them an asset to any team.

I have no doubt that [Name] would be an excellent fit for the AI and Machine Learning internship at [Company]. I wholeheartedly recommend them for this opportunity, and I would be happy to provide any further information or elaboration on my endorsement.

Sincerely, [Your Name]


---

```
(1+2)*3
3*(1+2)
```

# water jug problem (BFS)
```cpp
#include <bits/stdc++.h>
using namespace std;
class nodes{
	public: 
		pair<int,int> p;
		int first;
		int second;
		string s;
};
string makestring(int a,int b){
	std::stringstream out1;
	std::stringstream out2;
	string t1,t2,str;
    out1 << a;
    t1 = out1.str();
    out2 << b;
    t2 = out2.str();
    str = "("+t1+","+t2+")";
    return str;
}
int main()
{
	int counter = 0;
    ios::sync_with_stdio(false);
    //pair<int,int> cap,ini,final;
    nodes cap,ini,final;
    ini.p.first=0,ini.p.second=0;
    ini.s = makestring(ini.p.first,ini.p.second);
    //Input initial values
    cout<<"Enter the capacity of 2 jugs\n";
    cin>>cap.p.first>>cap.p.second;
    //input final values
    cout<<"Enter the required jug config\n";
    cin>>final.p.first>>final.p.second;
    //Using BFS to find the answer
    queue<nodes> q;
    q.push(ini);
    nodes jug;
    while(!q.empty()){
    	//Base case
    	jug = q.front();
    	if(jug.p.first == final.p.first){// && jug.p.second == final.p.second){
    		cout<<jug.s<<endl;
    		// counter++;
    		// if(counter==5)
	  		return 0;
    	}
    	nodes temp = jug;
    	//Fill 1st Jug
    	if(jug.p.first<cap.p.first){
			temp.p = make_pair(cap.p.first,jug.p.second);
			temp.s = jug.s + makestring(temp.p.first,temp.p.second);
			q.push(temp);
    	}
    	//Fill 2nd Jug
    	if(jug.p.second<cap.p.second){
			temp.p = make_pair(jug.p.first,cap.p.second);
			temp.s = jug.s + makestring(temp.p.first,temp.p.second);
			q.push(temp);
    	}
    	//Empty 1st Jug
    	if(jug.p.first>0){
			temp.p = make_pair(0,jug.p.second);
			temp.s = jug.s + makestring(temp.p.first,temp.p.second);
			q.push(temp);
    	}
    	//Empty 2nd Jug
    	if(jug.p.second>0){
			temp.p = make_pair(jug.p.first,0);
			temp.s = jug.s + makestring(temp.p.first,temp.p.second);
			q.push(temp);
    	}
    	//Pour from 1st jug to 2nd until its full
    	if(jug.p.first>0 && (jug.p.first+jug.p.second)>=cap.p.second){
    		temp.p = make_pair((jug.p.first-(cap.p.second-jug.p.second)),cap.p.second);
    		temp.s = jug.s + makestring(temp.p.first,temp.p.second);
    		q.push(temp);
    	}
    	//Pour from 2nd jug to 1st until its full
    	if(jug.p.second>0 && (jug.p.first+jug.p.second)>=cap.p.first){
    		temp.p = make_pair(cap.p.first,(jug.p.second-(cap.p.first-jug.p.first)));
    		temp.s = jug.s + makestring(temp.p.first,temp.p.second);
    		q.push(temp);
    	}
    	//Pour all water from 1st to 2nd
    	if(jug.p.first>0 && (jug.p.first+jug.p.second)<=cap.p.second){
    		temp.p = make_pair(0,jug.p.first+jug.p.second);
    		temp.s = jug.s + makestring(temp.p.first,temp.p.second);
    		q.push(temp);
    	}
    	//Pour from 2nd jug to 1st until its full
    	if(jug.p.second>0 && (jug.p.first+jug.p.second)<=cap.p.first){
    		temp.p = make_pair(jug.p.first+jug.p.second,0);
    		temp.s = jug.s + makestring(temp.p.first,temp.p.second);
    		q.push(temp);
    	}
    	q.pop();
    }
	return 0;
}
```