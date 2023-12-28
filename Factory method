#include <iostream>
#include <memory>
using namespace std;

// Абстрактний клас Продукту
class Product {
public:
    virtual ~Product() {}
    virtual string Operation() const = 0;
};

// Конкретні продукти надають різні реалізації інтерфейсу Продукту
class ConcreteProduct1 : public Product {
public:
    string Operation() const override {
        return "Результат операції ConcreteProduct1";
    }
};

class ConcreteProduct2 : public Product {
public:
    string Operation() const override {
        return "Результат операції ConcreteProduct2";
    }
};

// Клас Створювача оголошує фабричний метод, що повертає об'єкт класу Продукт
class Creator {
public:
    virtual ~Creator() {};
    virtual Product* FactoryMethod() const = 0;

    string SomeOperation() const {
        // Виклик фабричного методу для створення об'єкту Продукту
        Product* product = this->FactoryMethod();
        // Використання продукту
        string result = "Creator: Той самий код створювача працює з " + product->Operation();
        delete product;
        return result;
    }
};

// Конкретні Створювачі перевизначають фабричний метод для створення різних екземплярів продуктів
class ConcreteCreator1 : public Creator {
public:
    Product* FactoryMethod() const override {
        return new ConcreteProduct1();
    }
};

class ConcreteCreator2 : public Creator {
public:
    Product* FactoryMethod() const override {
        return new ConcreteProduct2();
    }
};

// Клієнтський код
void ClientCode(const Creator& creator) {
    cout << "Клієнт: Я не знаю клас створювача, але це все ще працює.\n"
         << creator.SomeOperation() << endl;
}

int main() {
    cout << "Запущено з ConcreteCreator1:" << endl;
    Creator* creator1 = new ConcreteCreator1();
    ClientCode(*creator1);
    delete creator1;
    
    cout << "Запущено з ConcreteCreator2:" << endl;
    Creator* creator2 = new ConcreteCreator2();
    ClientCode(*creator2);
    delete creator2;
    
    return 0;
}
