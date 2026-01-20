class Product:
    """Класс товара"""
    
    def __init__(self, name: str, price: float, quantity: int):
        self.name = name
        self.price = price
        self.quantity = quantity
    
    def update_price(self, new_price: float):
        """Обновление цены товара"""
        if new_price > 0:
            self.price = new_price
            return True
        return False
    
    def update_quantity(self, amount: int):
        """Обновление количества товара (может быть отрицательным для уменьшения)"""
        new_quantity = self.quantity + amount
        if new_quantity >= 0:
            self.quantity = new_quantity
            return True
        return False
    
    def to_dict(self):
        """Преобразование в словарь"""
        return {
            "name": self.name,
            "price": self.price,
            "quantity": self.quantity
        }
    
    def __str__(self):
        return f"{self.name} - Цена: {self.price:.2f} руб., Количество: {self.quantity} шт."


class Store:
    """Класс магазина для управления товарами"""
    
    def __init__(self):
        self.products = []
    
    def add_product(self, product: Product):
        """Добавление товара в магазин"""
        self.products.append(product)
        print(f"Товар '{product.name}' успешно добавлен!")
    
    def show_all_products(self):
        """Показать все товары"""
        if not self.products:
            print("В магазине нет товаров.")
            return
        
        print("\n" + "="*50)
        print("СПИСОК ВСЕХ ТОВАРОВ:")
        print("="*50)
        for idx, product in enumerate(self.products, 1):
            print(f"{idx}. {product}")
        print("="*50)
    
    def find_product(self, name: str):
        """Поиск товара по названию (без учета регистра)"""
        if not self.products:
            return None
        
        search_name = name.lower().strip()
        for product in self.products:
            if product.name.lower() == search_name:
                return product
        
        return None
    
    def search_product(self):
        """Поиск товара по названию (функция для меню)"""
        if not self.products:
            print("В магазине нет товаров для поиска.")
            return
        
        name = input("Введите название товара для поиска: ").strip()
        if not name:
            print("Название не может быть пустым!")
            return
        
        product = self.find_product(name)
        if product:
            print("\n" + "="*50)
            print("НАЙДЕН ТОВАР:")
            print("="*50)
            print(product)
            print("="*50)
        else:
            print(f"Товар с названием '{name}' не найден.")
    
    def delete_product(self):
        """Удаление товара по названию"""
        if not self.products:
            print("В магазине нет товаров для удаления.")
            return
        
        name = input("Введите название товара для удаления: ").strip()
        if not name:
            print("Название не может быть пустым!")
            return
        
        product = self.find_product(name)
        if product:
            self.products.remove(product)
            print(f"Товар '{product.name}' успешно удален!")
        else:
            print(f"Товар с названием '{name}' не найден.")
    
    def calculate_total_value(self):
        """Расчет общей стоимости всех товаров"""
        total = sum(product.price * product.quantity for product in self.products)
        return total
    
    def show_total_value(self):
        """Показать общую стоимость товаров"""
        if not self.products:
            print("В магазине нет товаров.")
            return
        
        total = self.calculate_total_value()
        print("\n" + "="*50)
        print(f"ОБЩАЯ СТОИМОСТЬ ВСЕХ ТОВАРОВ: {total:.2f} руб.")
        print("="*50)
        
        # Дополнительная информация по товарам
        print("\nДетализация:")
        for product in self.products:
            product_value = product.price * product.quantity
            print(f"{product.name}: {product_value:.2f} руб.")
        print("="*50)


def create_product_from_input():
    """Создание товара из пользовательского ввода"""
    print("\n" + "="*50)
    print("ДОБАВЛЕНИЕ НОВОГО ТОВАРА")
    print("="*50)
    
    while True:
        name = input("Введите название товара: ").strip()
        if name:
            break
        print("Название не может быть пустым!")
    
    while True:
        try:
            price = float(input("Введите цену товара (руб.): "))
            if price > 0:
                break
            print("Цена должна быть положительным числом!")
        except ValueError:
            print("Пожалуйста, введите число для цены!")
    
    while True:
        try:
            quantity = int(input("Введите количество товара: "))
            if quantity >= 0:
                break
            print("Количество не может быть отрицательным!")
        except ValueError:
            print("Пожалуйста, введите целое число для количества!")
    
    return Product(name, price, quantity)


def show_menu():
    """Отображение меню"""
    print("\n" + "="*50)
    print("МАГАЗИН ТОВАРОВ - ГЛАВНОЕ МЕНЮ")
    print("="*50)
    print("1. Показать все товары")
    print("2. Добавить товар")
    print("3. Найти товар по названию")
    print("4. Удалить товар")
    print("5. Общая стоимость всех товаров")
    print("0. Выход")
    print("="*50)


def main():
    """Основная функция приложения"""
    store = Store()
    
    # Добавим несколько тестовых товаров для примера
    store.add_product(Product("Молоко", 85.50, 20))
    store.add_product(Product("Хлеб", 45.00, 30))
    store.add_product(Product("Яблоки", 120.00, 15))
    
    while True:
        show_menu()
        
        choice = input("Выберите действие (0-5): ").strip()
        
        if choice == "0":
            print("Выход из программы. До свидания!")
            break
        
        elif choice == "1":
            store.show_all_products()
        
        elif choice == "2":
            try:
                new_product = create_product_from_input()
                store.add_product(new_product)
            except Exception as e:
                print(f"Ошибка при добавлении товара: {e}")
        
        elif choice == "3":
            store.search_product()
        
        elif choice == "4":
            store.delete_product()
        
        elif choice == "5":
            store.show_total_value()
        
        else:
            print("Неверный выбор. Пожалуйста, выберите действие от 0 до 5.")
        
        input("\nНажмите Enter для продолжения...")


if __name__ == "__main__":
    main()
