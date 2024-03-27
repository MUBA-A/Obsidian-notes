[[Prompt Engineering (Learning)]]


+ Backend/Django/REST API
	+ Prompt Engineering
		+ Comment: We use openai functional call (which returns the response in JSON; https://cookbook.openai.com/examples/how_to_call_functions_with_chat_models). Here, there needs to be number of different prompts by optimized by us. Prompt optimization will be done on the openai playground (https://platform.openai.com/playground). There could be, however, good AIs out there for question generation >>> search
		+ ToDo: We need to do two things in general. But the order of operation will be three things: in order, it will be 1. translation of OSR 2. quiz generation (in English) and 3. translation of quiz. Translation is broken up into two tasks.
			+ Translation: English open source resource (OSR) into minor language.
				1. GPT is retarded when it comes to minor languages. Thus, models such as BigTranslation or some other model on huggingface or DeepL API should be used. **This is the first thing we need to decide on. The whole point of the project is to translate stuff into minor language, so the focal point of all of this is to find good model.**
				2. Create optimized prompt. Prompts contain various parameters (See models.py in gpt_db folder). You are free to design whatever kind of script you want but it general. [I will add more details here once we do #1 above]
				3. Translate OSR digests into Mongolian (any other minor language tbf. But one of us has to be fluent in the target language). The result will be checked/validated by me (or you). As for what OSR digests to feed the model: 
					+ For the time being, the main subject will be biology. Other subjects like math or physics are heavy on image/figures and biology mostly can be about textual reading. The syllabus is on the biology textbook on openstax. We will go through the first chapter.
					+ Here, I'm not sure how to pull the textbook content. I'm not seeing any API in python so far. [Looking through currently] If push comes to shove, we will have to download each textbook and use some python library to extract each piece of content.
					+ After we're done with biology, math will be the next subject. If we can conquer math with all its figures, other subjects like physics and social science will be pretty similar. Although, we will need to use other tools that are strong with math like wolfram alpha (https://products.wolframalpha.com/api/pricing) to solve the math problems. LLMs can't be trusted with the correct solution for given math problem.
			+ Quiz generation: For now, it will be 10 questions (multiple choice) for each subject. Once we setup the entire thing, populating it will not be tough. The key here is quality (of the prompt) over quantity.
				+ As mentioned before, we will only do first chapter of biology textbook from openstax. That is still a lot of words so we have to chunk it out each call. This chunking process affects how we optimize the prompt. Ideally, better and more holistic questions can be made if we use the whole text. But alas, the model will have only chunk of the whole chapter to make questions from. Thus, it will be harder to generated questions that test sophisticated understanding and creative application of the holistic acquired knowledge. No need to worry about this for now but each chapter can be digested to fit into the token limit to deal with this problem. Here, it doesn't have to be gpt maybe?
	+ Content Mass Generation: Here, we will focus on quantity. Validation and filtering will be necessary after the mass generation.
		+ Quiz generation (1000 for each subject. Three subjects at first) based on the digest.
			+ Quiz validation by gpt (this stage will be skipped at first but if we're talking 100k questions + answers being generated, this stage will be needed. There needs to be another prompt for critical filtering by the model)
			+ Quiz validation by a person. You will just have to press "Validate" or "Delete" buttons for each questions and their translations. You should be able to edit them and press "Yes" if there's just minor issue with it.
		+ Translation: exactly the same thing as above. There will have to be validation for each translation.
	+ Gamification:
		+ Authentication/Authorization: Gotta make profile and character to be developed first. https://stackoverflow.blog/2021/10/06/best-practices-for-authentication-and-authorization-for-rest-apis/
			+ As to what parameters to be added: [Undecided] 
			+ Candidates: Elo system (both for the user and for the questions), Ranking system (S>A>B>C...; questions can have status like "X% of people answered correctly"), Roadmap of Clear Goals, Predictions for College Entrance Exam scores ("At this level, you will get 700/800 score on the college entrance exam").
+ [[Node.js]] (Front-end that communicates with REST API)
	+ This is still unupdated [Still needs to be sorted out]
	+ [[basic react from w3school]]
	+ Routing and how to handle stuff gotten from html form and relay that to the django API.
		+ Understanding CORS
		+ Rendering
			+ Partial rendering
	+ Basic page generation
	+ css, website design
	+ 
+ Deploy https://www.reddit.com/r/nextjs/comments/zu8iqc/how_to_deploy_a_website_with_django_backend_and/
+ React Native
+ Content Diversification
	+ Skill-based tests
	+ Information hub



Validators for models fields (e.g. 0-100 range validator for temperature field in Prompt) https://www.django-rest-framework.org/api-guide/validators/

