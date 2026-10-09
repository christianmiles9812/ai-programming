Campus Resource Assistant - Design Notes
	
	1. The problem

		The college wants to create a Campus Resource Assistant that helps students find information about campus services, such as the library, tutoring center, academic advising, and
		finacial aid. Students sometimes don't know these resources exist, where they are located, or when they are open. The assistant will let students ask questions in plain english
		and recieve answers based on verified campus information.
	
	2. Why Gemini can't answer non specific campus questions by itself.
		
		Gemini can answer general questions because it has learned information during training. However, it does not automatically know current, campus specific information. Our agents
		uses a Pyhton tool to look up verified information in a .JSON file. This helps the agent provide accurate answers instead of guessing or making up information.
		
	3. Three reasons the campus data is stored in a JSON file.

		1) Seperates data from code: We can update office hours, phone numbers, and locations without changing the Python program

		2) Easy to review: The information can be checked by an college staff member without needing to understand python themselves.

		3) Easy to expand: In the future, the JSON file could be replaced with a database or live API without having to completely rewrite the agent.

	4. Limitations and future improvements
		
		1) Outdated information: Campus hours and room numbers can change, making the JSON data inaccurate. In the future, the agent could us a live campus directory or API to retrieve
								 updated information.

		2) No conversation memory: The agent does not remember previous conversations. A future version could store conversation history so students can ask follow-up questions more naturally.

		3) Limited user interface: The current version uses a terminal and the ADK web interface, which are mainly for development. A future verison could use a Streamlit interface to make
								   the assistant easier for students to use.
	
	5. Inaccurate JSON file

		If the campus information in the JSON file is inaccurate, students could recieve the wrong office hours, visit the wrong location, or contact the wrong perosn. This could prevent students
		from getting the help they need. The information should be verified by the development team using official college sources, with college staff confirming that the information is correct.
		The verified_by and last_verified fields help track who checked the information and when.


JCC resource table

	| Resource        |Location				    |Hours     |Email					 | Website														    | Verified By     | Date Verified |
	|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
	| Library         |Hultquist Library		|8am - 6pm | No email listed         | https://www.sunyjcc.edu/support/learning-commons/library         | Christian Miles | 2026/10/01    |
	| Tutoring Center |Hult 1: Learning Commons |8am - 6pm | No email listed         | https://www.sunyjcc.edu/support/learning-commons/learning-center | Christian Miles | 2026/10/01	  |
	| Advising        |No building listed       |9am - 5pm | No email listed         | https://www.sunyjcc.edu/support/success-center/advising          | Christian Miles | 2026/10/01	  |
	| Financial Aid   |COCE Floor 1			    |9am - 5pm | FinacialAid@sunyjcc.edu | https://www.sunyjcc.edu/support/financial-aid-billing            | Christian Miles | 2026/10/01	  |

Workflow

	Students asks a question
			   |
	Campus resource agent (ADK)
			   |
	Gemini interprets the questions
			   |
	Python tool: get_campus_resource_info
			   |
	campus_resources.json
			   |
	Tool returns the matching resource information
			   |
	Gemini generates the answer
			   |
	Student receives the response