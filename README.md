import random

class Quiz:
    def __init__(self):
        self.questions = []
        self.answers = []

    def add_question(self, question, answer):
        self.questions.append(question)
        self.answers.append(answer)

    def run_quiz(self):
        score = 0
        print("Welcome to the General Knowledge Quiz!")
        print("Answer the following questions:")
        for i in range(len(self.questions)):
            print("\nQuestion", i+1, ":", self.questions[i])
            user_answer = input("Your answer: ")
            if user_answer.lower() == self.answers[i].lower():
                print("Correct!")
                score += 1
            else:
                print("Incorrect! The correct answer is:", self.answers[i])
        print("\nQuiz ended. You scored {}/{}".format(score, len(self.questions)))

if __name__ == "__main__":
    quiz = Quiz()
    quiz.add_question("What is the capital of Italy?", "Rome")
    quiz.add_question("What is the largest planet in our solar system?", "Jupiter")
    quiz.add_question("Who painted the Mona Lisa?", "Leonardo da Vinci")
    quiz.add_question("What is the powerhouse of the cell?", "Mitochondria")
    quiz.run_quiz()


