# Page 2

<figure><img src=".gitbook/assets/02_04_25_add_api_spec.svg" alt="hello world!"><figcaption><p>this is a caption</p></figcaption></figure>

{% tabs %}
{% tab title="Python" %}
{% code title="swift-code" %}
```python
import json
import requests
from typing import List, Dict, Optional
from dataclasses import dataclass
from datetime import datetime, timedelta
import asyncio
import aiohttp

# MARK: - Classes and Data Structures

@dataclass
class Person:
    first_name: str
    last_name: str
    age: int
    email: Optional[str] = None
    
    @property
    def full_name(self) -> str:
        return f"{self.first_name} {self.last_name}"
    
    def is_adult(self) -> bool:
        return self.age >= 18
    
    def __str__(self) -> str:
        return f"Person({self.full_name}, {self.age} years old)"

class TaskManager:
    def __init__(self):
        self.tasks = []
    
    def add_task(self, task: str, priority: int = 1):
        self.tasks.append({
            'task': task,
            'priority': priority,
            'created': datetime.now(),
            'completed': False
        })
    
    def complete_task(self, task_index: int):
        if 0 <= task_index < len(self.tasks):
            self.tasks[task_index]['completed'] = True
    
    def get_pending_tasks(self) -> List[Dict]:
        return [task for task in self.tasks if not task['completed']]
    
    def get_high_priority_tasks(self) -> List[Dict]:
        return sorted(
            [task for task in self.tasks if task['priority'] >= 3 and not task['completed']],
            key=lambda x: x['priority'],
            reverse=True
        )

# MARK: - List Comprehensions and Functional Programming

def list_operations():
    numbers = list(range(1, 21))
    
    # List comprehensions
    squares = [x**2 for x in numbers]
    even_squares = [x**2 for x in numbers if x % 2 == 0]
    
    # Dictionary comprehension
    number_info = {x: {'square': x**2, 'cube': x**3, 'even': x % 2 == 0} for x in numbers[:10]}
    
    # Set comprehension
    unique_remainders = {x % 7 for x in numbers}
    
    print(f"Squares: {squares[:5]}...")
    print(f"Even squares: {even_squares[:5]}...")
    print(f"Unique remainders when divided by 7: {unique_remainders}")
    
    # Filter, map, reduce examples
    from functools import reduce
    
    filtered_numbers = list(filter(lambda x: x % 3 == 0, numbers))
    mapped_numbers = list(map(lambda x: x * 2, numbers[:5]))
    sum_of_squares = reduce(lambda acc, x: acc + x**2, numbers[:5], 0)
    
    print(f"Numbers divisible by 3: {filtered_numbers}")
    print(f"First 5 numbers doubled: {mapped_numbers}")
    print(f"Sum of squares of first 5: {sum_of_squares}")

# MARK: - File Operations and JSON

def file_operations():
    # Writing to file
    data = {
        'users': [
            {'name': 'Alice', 'age': 30, 'city': 'New York'},
            {'name': 'Bob', 'age': 25, 'city': 'San Francisco'},
            {'name': 'Charlie', 'age': 35, 'city': 'Chicago'}
        ],
        'timestamp': datetime.now().isoformat()
    }
    
    # Write JSON
    with open('users.json', 'w') as f:
        json.dump(data, f, indent=2)
    
    # Read and process JSON
    try:
        with open('users.json', 'r') as f:
            loaded_data = json.load(f)
            
        print("Loaded users:")
        for user in loaded_data['users']:
            print(f"  {user['name']} ({user['age']}) from {user['city']}")
            
    except FileNotFoundError:
        print("File not found!")
    except json.JSONDecodeError:
        print("Invalid JSON format!")

# MARK: - Web Requests and API Handling

def web_requests_example():
    """Example of making HTTP requests"""
    try:
        # GET request
        response = requests.get('https://jsonplaceholder.typicode.com/posts/1')
        response.raise_for_status()
        
        post_data = response.json()
        print(f"Post title: {post_data['title']}")
        
        # POST request
        new_post = {
            'title': 'My New Post',
            'body': 'This is the content of my post',
            'userId': 1
        }
        
        post_response = requests.post(
            'https://jsonplaceholder.typicode.com/posts',
            json=new_post
        )
        
        if post_response.status_code == 201:
            created_post = post_response.json()
            print(f"Created post with ID: {created_post['id']}")
            
    except requests.RequestException as e:
        print(f"Request failed: {e}")

# MARK: - Async/Await Example

async def fetch_url(session, url):
    """Fetch a single URL asynchronously"""
    try:
        async with session.get(url) as response:
            return await response.json()
    except Exception as e:
        print(f"Error fetching {url}: {e}")
        return None

async def fetch_multiple_posts():
    """Fetch multiple posts concurrently"""
    urls = [f'https://jsonplaceholder.typicode.com/posts/{i}' for i in range(1, 6)]
    
    async with aiohttp.ClientSession() as session:
        tasks = [fetch_url(session, url) for url in urls]
        results = await asyncio.gather(*tasks)
        
        print("Fetched posts:")
        for i, post in enumerate(results, 1):
            if post:
                print(f"  {i}. {post['title'][:50]}...")

# MARK: - Decorators and Context Managers

def timer_decorator(func):
    """Decorator to time function execution"""
    import time
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(f"{func.__name__} took {end - start:.4f} seconds")
        return result
    return wrapper

class DatabaseConnection:
    """Context manager example"""
    def __init__(self, connection_string):
        self.connection_string = connection_string
        self.connected = False
    
    def __enter__(self):
        print(f"Connecting to {self.connection_string}")
        self.connected = True
        return self
    
    def __exit__(self, exc_type, exc_val, exc_tb):
        print("Closing database connection")
        self.connected = False
    
    def query(self, sql):
        if self.connected:
            return f"Executing: {sql}"
        else:
            raise Exception("Not connected to database")

# MARK: - Error Handling and Custom Exceptions

class ValidationError(Exception):
    """Custom exception for validation errors"""
    pass

def validate_email(email: str) -> bool:
    """Simple email validation"""
    import re
    pattern = r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$'
    return re.match(pattern, email) is not None

def create_user(name: str, email: str, age: int) -> Person:
    """Create user with validation"""
    if not name.strip():
        raise ValidationError("Name cannot be empty")
    
    if not validate_email(email):
        raise ValidationError("Invalid email format")
    
    if age < 0 or age > 150:
        raise ValidationError("Age must be between 0 and 150")
    
    return Person(name.split()[0], name.split()[-1], age, email)

# MARK: - Generator Functions

def fibonacci_generator(n: int):
    """Generate fibonacci numbers up to n"""
    a, b = 0, 1
    count = 0
    while count < n:
        yield a
        a, b = b, a + b
        count += 1

def file_line_processor(filename: str):
    """Process file lines one at a time (memory efficient)"""
    try:
        with open(filename, 'r') as f:
            for line_num, line in enumerate(f, 1):
                yield line_num, line.strip()
    except FileNotFoundError:
        print(f"File {filename} not found")

# MARK: - Main Execution Examples

@timer_decorator
def run_examples():
    """Run all examples"""
    print("=== Python Examples ===\n")
    
    # Person and TaskManager examples
    person = Person("John", "Doe", 25, "john@example.com")
    print(f"Created: {person}")
    print(f"Is adult: {person.is_adult()}\n")
    
    # Task manager
    tm = TaskManager()
    tm.add_task("Learn Python", 5)
    tm.add_task("Write documentation", 3)
    tm.add_task("Buy groceries", 2)
    
    print("High priority tasks:")
    for task in tm.get_high_priority_tasks():
        print(f"  - {task['task']} (Priority: {task['priority']})")
    print()
    
    # List operations
    list_operations()
    print()
    
    # File operations
    file_operations()
    print()
    
    # Fibonacci generator
    print("First 10 Fibonacci numbers:")
    fib_numbers = list(fibonacci_generator(10))
    print(fib_numbers)
    print()
    
    # Context manager example
    with DatabaseConnection("postgresql://localhost:5432/mydb") as db:
        result = db.query("SELECT * FROM users")
        print(result)
    print()
    
    # Error handling example
    try:
        user = create_user("Jane Smith", "jane@example.com", 28)
        print(f"Created user: {user}")
    except ValidationError as e:
        print(f"Validation error: {e}")

if __name__ == "__main__":
    # Run synchronous examples
    run_examples()
    
    # Run async example (uncomment to test)
    # asyncio.run(fetch_multiple_posts())
```
{% endcode %}
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}
