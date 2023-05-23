>Links: [[College]]

- mod 1
	- life cycle models
	- CMM
	- quality models
	- agile
- mod 2
	- metrics
	- FP
	- COCOMO

---
- waterfall model
	- when *requirements are well understood*, fixed and the technology is stable
- v shaped
	- when *testing is critical* and the testing phase is emphasized
- prototype
	- when *requirements are unclear* and prototypes need to be shown
- spiral 
	- when the project is complex and high risk
	- requirements are unclear
	- when constant feedback is needed.
- iterative 
	- when requirements are not well understood,
	- there is a need to get a working prototype quickly.
- incremental
	- when there are changing requirements 
	- when the technology is not well understood

## prototyping model
- earlier models needed definite designs
- they lack customer interaction
- enter, this one
- concerns the approval of customers
- can't move fwd till customer is satisfied
- time consuming
- 4 types
	- throwaway
		- prepare something, don't like, throw, create from scratch again
	- evolutionary
		- dont throw, modify/refine
- phases
	- initial req
	- design and eval
		- prototyping
		- customer eval
		- review and updation
		- design
	- dev
	- test
	- deploy/maintain

## spiral model
- concerns risk identification, analysis, prioritization, handling
- simple figure = 4 quads
	- req analysis
	- coding and tesitn
	- eval
	- risk analysis and planning
		- has to be done parallely along with all the phases

## interative model
- 3 iterations consisting of phases
- modular
- dont move till one module/iteration is satisfactory

## incremental model
- worst (more than waterfall? ou yea)
- do all phases $n$ times
- lot of deployment time

---
## CMM
>how mature the organization is?
- prev models don't consider the structure/characteristics/standard of org
- this models the level of the org
- how much can they handle
- 5 levels
	1. **initial**
		- org characterized by *ad hoc activities*
		- *very few* processes defined and followed
		- diff engineers folo their own standards/processes
		- resulting effort becomes chaotic
		- called *chaotic level*
		- success only due to some individuals
	2. **repeatable**
		- basic project management practices (cost and schedule) are followed
		- use cost estimation techniques
		- focus on same kinds of problems
	3. **defined**
		- processes for *management* are mainained along with that for development
		- common org wide understanding of activities, etc
		- *product qualities* are not defined
	4. **quantitatively managed**
		- focus on software metrics
		- 2 types of metrics collected
			- *product metrics*
				- size
				- reliability
				- time complexity
				- understandability
			- *process metrics* (testing)
				- avg defect correction time
				- avg no of defects found per hour of inspection
	5. **optimizing**
		- have everything
- customer side constraints force them to move down the levels

---
## software quality
- conformance to req and/or fitness of use
- customer satisfaction + internal parameter checks

### quality models
- **McCall's**
	- ![[Pasted image 20230524005555.png]]
	- three perspectives
		- *product revision*
			1. maintainability
			2. flexibility
			3. testability
		- *product transition*
			1. portability
			2. reusability
			3. interoperability
		- *product operation*
			1. correctness
			2. reliability
			3. efficiency
			4. integrity
			5. usabillity

- **Boehm's**
	- seven quality factors
		1. portability
		2. reliability
		3. efficiency
		4. usability
		5. testability
		6. understandability
		7. flexibility

- **ISO 9000**
	- guidelines for maintaining a quality system
	- *ISO 9001* for orgs in design, development, production, servicing
	- *ISO 9002* for orgs in production
	- *ISO 9003* for orgs in installation and testing
	- main requirements of ISO 9001
		1. management responsibility
		2. quality system
		3. contract reviews
		4. design control
		5. document control
		6. purchasing
		7. purchaser supplied products
		8. product identification
		9. process control
		10. inspection and testing
		11. inspection, measuring, test quipment
		12. inspection and test status
		13. control of noncomforming product
		14. corrective action
		15. handling
		16. quality records
		17. quality audits
		18. training
	- features of ISO 9001
		- all docs should be properly managed
		- proper plans should be prepared
		- imp docs be checked for effectiveness
		- product should be tested against specification
		- org aspects should be addressed

## agile methodology
Agile methodologies refer to a set of software development approaches that prioritize flexibility, collaboration, and iterative development. These methodologies emphasize adaptive planning, continuous improvement, and rapid delivery of working software. Here are some key aspects of agile methodologies:

- **Iterative and Incremental Development**: Agile methodologies break the project into smaller iterations or increments, with each iteration delivering a working version of the software. This allows for early and frequent delivery of valuable functionality.

- **Adaptive Planning**: Agile methodologies embrace change by acknowledging that requirements can evolve over time. Instead of rigidly following a predefined plan, agile teams continuously refine and adjust their plans based on feedback, new insights, and changing priorities.

- **Cross-Functional and Collaborative Teams**: Agile promotes close collaboration among team members from different disciplines, such as developers, testers, designers, and stakeholders. The emphasis is on effective communication, shared ownership, and collaboration to achieve project goals.    

- **Continuous User Involvement**: Agile methodologies emphasize the involvement of users or stakeholders throughout the development process. Regular feedback and close collaboration help ensure that the delivered software meets the users' needs and expectations.

- **Emphasis on Communication**: Agile methodologies prioritize effective and transparent communication within the team and with stakeholders. Frequent meetings, such as daily stand-ups and regular retrospectives, facilitate information sharing, issue resolution, and alignment.
   
- **Embracing Change**: Agile methodologies recognize that change is inevitable and welcome it as an opportunity to enhance the product. Changes can be accommodated at any stage of development, and feedback from users or stakeholders is incorporated iteratively.

- **Continuous Improvement**: Agile methodologies foster a culture of continuous improvement. Regular retrospectives allow the team to reflect on their processes, identify areas of improvement, and implement changes to enhance productivity, quality, and team dynamics.

- **Agile Frameworks**: Several frameworks fall under the agile umbrella, including *Scrum*, *Kanban*, Extreme Programming (*XP*), and *Lean* Software Development. Each framework provides specific practices, roles, and ceremonies to guide the implementation of agile principles.

Agile methodologies aim to deliver value early and often, promote collaboration and adaptability, and improve overall project success by embracing change and customer feedback. They have gained popularity due to their ability to address the challenges of rapidly evolving requirements and dynamic business environments.

---







## books
- K. K. Aggarwal & Yogesh Singh, “Software Engineering”
- R. S. Pressman, “Software Engineering – A practitioner’s approach”