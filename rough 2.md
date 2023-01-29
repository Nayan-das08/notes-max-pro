---
subject: rough
category:
---
Dec 18, 2022

>Links: [[rough]]

To Whom It May Concern,

I am writing to highly recommend [Nayan Ranjan Das] for the [Summer Students Programme 2023] at [CERN OpenLabs]. I have had the pleasure of working with [him] for the past year as his supervisor at [Amity University, Noida], and I have consistently been impressed by his aptitude for and passion for this field.

In the time that I have known [Nayan], he has consistently demonstrated a strong understanding of AI and machine learning concepts. He has completed several relevant coursework, including [Course] and [Course], and have consistently excelled in these classes. In addition, [Nayan] has completed several independent research projects in these areas, including a project on [Topic] that resulted in a published paper in [Publication].

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

# second
To Whom It May Concern,

I am writing to highly recommend Nayan Ranjan Das for the Summer Student Programme at CERN. As his faculty guide in the field of Artificial Intelligence and Machine Learning, I have had the pleasure of working with Nayan for the past year and can confidently say that he is a dedicated and talented individual.

Nayan has demonstrated a strong aptitude for AIML, consistently producing high-quality work in class and during group projects. He has a deep understanding of the theories and concepts behind AIML and Deep Learning and is able to apply them to solve complex problems.

Nayan also showed exceptional research skills, completing an group study project on Fire Detection Alarm System using Deep Learning, which resulted in a publication in University conference "Confluence 2023". He worked tirelessly on this project, conducting extensive literature reviews and developing new methods to improve the performance of fire detecttion.

Nayan is also a team player and a leader, during group projects and class activities he always demonstrated excellent communication and leadership skills, making sure the team's goals were met and that everyone was working together efficiently.

I have no doubt that Nayan would be an asset to the Summer Student Programme at CERN. He is a hardworking, intelligent and enthusiastic learner, who is eager to learn and contribute to the field of AIML. I strongly recommend Nayan for this opportunity.

Sincerely,
Dr. Supriya Raheja
Professor of Computer Science
Amity School of Engineering and Technology
Amity University, Noida

---
To Whom It May Concern,

I am writing to highly recommend Nayan Ranjan Das for the Summer Students Programme 2023 at CERN. I have had the pleasure of teaching him for the past year at Amity University, Noida, and I have consistently been impressed by his aptitude for and passion for this field.

In the time that I have known Nayan, he has consistently demonstrated a strong understanding of AI and machine learning concepts. He has completed several relevant coursework, including Introduction to AIML and Fundamental of Data Analytics, and have consistently excelled in these classes. In addition, Nayan has completed several independent research projects in these areas, including a project on Fire Detection Alarm System using Deep Learning that resulted in a published paper in Confluence 2023, University conference.

In addition to his technical skills, Nayan is a highly motivated and dedicated individual. He consistently take on additional responsibilities and is always willing to go above and beyond to ensure that projects are completed to the best of his ability. His strong work ethic and positive attitude would make him an asset to any team.

I am certain that Nayan would be an excellent fit for the AI and Machine Learning internship in the Student Summer Programme at CERN. I wholeheartedly recommend them for this opportunity, and I would be happy to provide any further information or elaboration on my endorsement.

Sincerely,
Dr. Krishna Kant Singh
Professor of Deep Learning and Neural Network
Amity School of Engineering and Technology
Amity University, Noida

---
Dear Adriana Bejaoui,

I am writing to express my strong interest in the CERN openlab Internship opportunity. As a Artificial Intelligence and Machine Learning student, I am thrilled about the chance to work alongside the talented individuals at CERN and contribute to cutting-edge research in the field of AIML and other computational aspects of particle physics.

I am particularly drawn to CERN's mission of fostering collaboration and scientific advancement and I am eager to be a part of such a dynamic and innovative organization. The opportunity to work with some of the world's leading experts in this field, and to learn from their experiences, is a once-in-a-lifetime opportunity that I do not want to miss.

I have performed several independent research projects in the field of AIML (especially in AI) and am currently pursuing Undergraduate Engineering in Computer Science with hons. in the same field. I am well versed with several programming languages and have a deep understanding of Deep Learning concepts and Mathematics. I am confident that my skills and experience make me a strong candidate for this internship and I am excited about the prospect of contributing my knowledge and abilities to CERN.

Thank you for considering my application. I look forward to the opportunity to discuss my interest further and learn more about the responsibilities and expectations of the internship role.

Best regards,
Nayan Ranjan Das

---
1. Programming
2. Data Analysis
3. Knowledge of Physics, Math and CS
4. Data processing and visualization
5. Machine Learning

1. Deep Learning
2. TensorFlow
3. Keras
4. Strong teamwork, collaboration
5. Independent problem solving