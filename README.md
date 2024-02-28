class Flashcard:
    def _init_(self, question, answer):
        self.question = question
        self.answer = answer

class Quiz:
    def _init_(self):
        self.flashcards = []
        self.total_questions = 0
        self.correct_answers = 0

    def add_flashcard(self, flashcard):
        self.flashcards.append(flashcard)

    def take_quiz(self):
        self.total_questions = len(self.flashcards)
        self.correct_answers = 0

        for flashcard in self.flashcards:
            print(flashcard.question)
            user_answer = input("Your answer: ").strip()
            if user_answer.lower() == flashcard.answer.lower():
                print("Correct!")
                self.correct_answers += 1
            else:
                print("Incorrect. The correct answer is:", flashcard.answer)
        
        score = (self.correct_answers / self.total_questions) * 100
        print("Quiz complete! Your score:", score, "%")

class FlashcardQuizApp:
    def _init_(self):
        self.quizzes_taken = []

    def add_quiz(self, quiz):
        self.quizzes_taken.append(quiz)

    def view_scores(self):
        for i, quiz in enumerate(self.quizzes_taken):
            print("Quiz", i+1, "- Score:", (quiz.correct_answers / quiz.total_questions) * 100, "%")

def main():
    app = FlashcardQuizApp()

    # Example usage:
    quiz1 = Quiz()
    quiz1.add_flashcard(Flashcard("What is the capital of France?", "Paris"))
    quiz1.add_flashcard(Flashcard("What is 2+2?", "4"))
    app.add_quiz(quiz1)

    quiz2 = Quiz()
    quiz2.add_flashcard(Flashcard("What is the largest planet in the solar system?", "Jupiter"))
    quiz2.add_flashcard(Flashcard("What is the chemical symbol for water?", "H2O"))
    app.add_quiz(quiz2)

    # Take quizzes
    for quiz in app.quizzes_taken:
        quiz.take_quiz()

    # View scores
    app.view_scores()

if _name_ == "_main_":
    main()
