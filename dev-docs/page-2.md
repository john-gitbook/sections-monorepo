# Page 2

<figure><img src=".gitbook/assets/02_04_25_add_api_spec.svg" alt="hello world!"><figcaption><p>this is a caption</p></figcaption></figure>

{% tabs %}
{% tab title="Test code" %}
{% code title="" %}
```
import Foundation
import UIKit

// MARK: - Basic Data Structures and Functions

// Simple struct with computed properties
struct Person {
    let firstName: String
    let lastName: String
    
    var fullName: String {
        return "\(firstName) \(lastName)"
    }
    
    func greet() -> String {
        return "Hello, I'm \(fullName)"
    }
}

// Array operations and higher-order functions
func arrayExamples() {
    let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    
    // Filter even numbers
    let evenNumbers = numbers.filter { $0 % 2 == 0 }
    print("Even numbers: \(evenNumbers)")
    
    // Map to squares
    let squares = numbers.map { $0 * $0 }
    print("Squares: \(squares)")
    
    // Reduce to sum
    let sum = numbers.reduce(0, +)
    print("Sum: \(sum)")
}

// MARK: - Async/Await Example

func fetchUserData(userId: Int) async throws -> Person {
    // Simulate network delay
    try await Task.sleep(nanoseconds: 1_000_000_000) // 1 second
    
    // Simulate API response
    return Person(firstName: "John", lastName: "Doe")
}

func handleUserFetch() async {
    do {
        let user = try await fetchUserData(userId: 123)
        print("Fetched user: \(user.fullName)")
    } catch {
        print("Failed to fetch user: \(error)")
    }
}

// MARK: - SwiftUI View Example

import SwiftUI

struct ContentView: View {
    @State private var counter = 0
    @State private var userName = ""
    
    var body: some View {
        VStack(spacing: 20) {
            Text("Counter: \(counter)")
                .font(.title)
                .foregroundColor(.blue)
            
            HStack {
                Button("Decrease") {
                    counter -= 1
                }
                .buttonStyle(.bordered)
                
                Button("Increase") {
                    counter += 1
                }
                .buttonStyle(.borderedProminent)
            }
            
            TextField("Enter your name", text: $userName)
                .textFieldStyle(.roundedBorder)
                .padding(.horizontal)
            
            if !userName.isEmpty {
                Text("Hello, \(userName)!")
                    .font(.headline)
                    .foregroundColor(.green)
            }
        }
        .padding()
    }
}

// MARK: - Protocol and Extension Example

protocol Drawable {
    func draw() -> String
}

struct Circle: Drawable {
    let radius: Double
    
    func draw() -> String {
        return "Drawing a circle with radius \(radius)"
    }
    
    var area: Double {
        return Double.pi * radius * radius
    }
}

extension String {
    func capitalizedFirst() -> String {
        guard let first = self.first else { return self }
        return String(first).uppercased() + String(self.dropFirst())
    }
    
    var isValidEmail: Bool {
        let emailRegex = #"^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,}$"#
        return self.range(of: emailRegex, options: [.regularExpression, .caseInsensitive]) != nil
    }
}

// MARK: - Error Handling

enum NetworkError: Error {
    case invalidURL
    case noData
    case decodingError
}

func processData(_ data: Data?) throws -> String {
    guard let data = data else {
        throw NetworkError.noData
    }
    
    guard let string = String(data: data, encoding: .utf8) else {
        throw NetworkError.decodingError
    }
    
    return string
}

// MARK: - Usage Examples

func runExamples() {
    // Person example
    let person = Person(firstName: "Jane", lastName: "Smith")
    print(person.greet())
    
    // Array examples
    arrayExamples()
    
    // String extension examples
    let email = "test@example.com"
    print("Is valid email: \(email.isValidEmail)")
    
    let text = "hello world"
    print("Capitalized: \(text.capitalizedFirst())")
    
    // Circle example
    let circle = Circle(radius: 5.0)
    print(circle.draw())
    print("Area: \(circle.area)")
    
    // Error handling example
    do {
        let result = try processData("Hello".data(using: .utf8))
        print("Processed: \(result)")
    } catch {
        print("Error: \(error)")
    }
}
```
{% endcode %}
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}
