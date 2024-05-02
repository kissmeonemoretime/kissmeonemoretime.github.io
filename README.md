import random

class PersonalityQuiz:
    def __init__(self):
        self.questions = []
        self.answers = []
        self.personality_traits = ['Extroversion', 'Introversion', 'Openness', 'Conscientiousness']
        self.personality_scores = {trait: 0 for trait in self.personality_traits}

    def add_question(self, question, answers, trait_scores):
        self.questions.append(question)
        self.answers.append(answers)
        for trait, score in trait_scores.items():
            self.personality_scores[trait] += score

    def run_quiz(self):
        print("Welcome to the Personality Quiz!")
        print("Answer the following questions with a number from 1 to 5:")
        print("1 - Strongly Disagree, 2 - Disagree, 3 - Neutral, 4 - Agree, 5 - Strongly Agree")
        for i in range(len(self.questions)):
            print("\nQuestion", i+1, ":", self.questions[i])
            for j, answer in enumerate(self.answers[i]):
                print(j+1, "-", answer)
            user_answer = int(input("Your answer: "))
            for trait, score in self.answers[i][user_answer - 1][1].items():
                self.personality_scores[trait] += score

        dominant_trait = max(self.personality_scores, key=self.personality_scores.get)
        print("\nQuiz ended. Your dominant personality trait is:", dominant_trait)

if __name__ == "__main__":
    quiz = PersonalityQuiz()
    quiz.add_question("I prefer socializing in large groups rather than alone.", 
                      [("Strongly Disagree", {'Introversion': 1}),
                       ("Disagree", {'Introversion': 0.5}),
                       ("Neutral", {'Introversion': 0}),
                       ("Agree", {'Extroversion': 0.5}),
                       ("Strongly Agree", {'Extroversion': 1})],
                      {'Extroversion': 0, 'Introversion': 0})
    
    quiz.add_question("I enjoy trying new things and exploring different ideas.", 
                      [("Strongly Disagree", {'Conscientiousness': 0}),
                       ("Disagree", {'Conscientiousness': 0.5}),
                       ("Neutral", {'Openness': 0}),
                       ("Agree", {'Openness': 0.5}),
                       ("Strongly Agree", {'Openness': 1})],
                      {'Openness': 0, 'Conscientiousness': 0})
    
    quiz.add_question("I prefer to plan activities rather than acting spontaneously.", 
                      [("Strongly Disagree", {'Conscientiousness': 1}),
                       ("Disagree", {'Conscientiousness': 0.5}),
                       ("Neutral", {'Conscientiousness': 0}),
                       ("Agree", {'Conscientiousness': -0.5}),
                       ("Strongly Agree", {'Conscientiousness': -1})],
                      {'Conscientiousness': 0})
    
    quiz.add_question("I find it easy to communicate with others and express my thoughts.", 
                      [("Strongly Disagree", {'Introversion': 1}),
                       ("Disagree", {'Introversion': 0.5}),
                       ("Neutral", {'Introversion': 0}),
                       ("Agree", {'Extroversion': 0.5}),
                       ("Strongly Agree", {'Extroversion': 1})],
                      {'Extroversion': 0, 'Introversion': 0})

    quiz.run_quiz()



