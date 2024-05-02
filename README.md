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
        for i in range(len(self.questions)):
            print("Question", i+1, ":", self.questions[i])
            user_answer = input("Your answer: ")
            if user_answer.lower() == self.answers[i].lower():
                print("Correct!")
                score += 1
            else:
                print("Incorrect!")
        print("Quiz ended. You scored {}/{}".format(score, len(self.questions)))

if __name__ == "__main__":
    quiz = Quiz()
    quiz.add_question("What is the capital of France?", "Paris")
    quiz.add_question("What is 2 + 2?", "4")
    quiz.add_question("Who wrote 'Romeo and Juliet'?", "Shakespeare")
    quiz.add_question("What is the tallest mammal?", "Giraffe")
    quiz.run_quiz()
