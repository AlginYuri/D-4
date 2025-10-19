import random

class Adder:
    def operation(self, a, b):
        return a + b

class Multiplier:
    def operation(self, a, b):
        return a * b

class Encryptor(Adder, Multiplier):
    def __init__(self, a, b):
        self.a = a
        self.b = b
        self.result = None
        self.encrypt()

    def encrypt(self):
        action = random.choice(["add", "multiply", "subtract", "divide"])
        if action == "add":
            self.result = super().operation(self.a, self.b)
        elif action == "multiply":
            self.result = Multiplier.operation(self, self.a, self.b)
        elif action == "subtract":
            self.result = self.a - self.b
        elif action == "divide":
            if self.b != 0:
                self.result = round(self.a / self.b, 2)
            else:
                self.result = "Ошибка деления"

    def __str__(self):
        return str(self.result)

x = Encryptor(12, 4)
print("Результат шифрования:", x)
