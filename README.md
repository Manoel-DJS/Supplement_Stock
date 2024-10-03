## Diagrama de Classes - Sujeito a fortes alterações
## English Diagram
```mermaid
classDiagram
    class Supplier {
        -UUID idSupplier
        -String name
        -String contact
        +List<Product> suppliedProducts
        +void supplyProduct(Product product, int quantity)
    }

    class Manufacturer {
        -UUID idManufacturer
        -String name
        -String origin
        +List<Product> manufacturedProducts
        +void manufactureProduct(Product product)
    }

    class Product {
        -long idProduct
        -String name
        -double price
        -int stockQuantity
        -Supplier supplier
        -Manufacturer manufacturer
        +void addStock(int quantity)
        +void removeStock(int quantity)
        +void updatePrice(double newPrice)
    }

    class Stock {
        +List<Product> products
        +void listProducts()
        +Product searchProductByName(String name)
        +void updateStock(Product product, int quantity)
    }

    class Employee {
        -long idEmployee
        -String name
        -String position
        -double salary
        +void performSale(Sale sale)
    }

    class Sale {
        -long idSale
        +Date date
        +Employee employee
        +List<Product> soldProducts
        +Customer customer
        +Payment payment
        +double calculateTotal()
    }

    class Payment {
        -long idPayment
        -String paymentMethod
        -double amount
        +Sale sale
        +void makePayment()
    }

    class Customer {
        -UUID idCustomer
        -String name
        -String email
        -String phone
        +List<Sale> salesHistory
        +void purchaseProduct(Sale sale)
    }

    Product "*" --> "1" Supplier : supplied by
    Product "*" --> "1" Manufacturer : manufactured by
    Stock "1" --> "*" Product : contains
    Sale "1" --> "*" Product : includes
    Employee "1" --> "*" Sale : performs
    Sale "1" --> "1" Payment : associated with
    Sale "*" --> "1" Customer : made by
    Customer "1" --> "*" Sale : has history

```
