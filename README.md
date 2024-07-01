# tinyredis

> *Experimental minimalist API for redis*

    pip install tinyredis

## Sample

```python
import redis
from tinyredis import TinyRedis
from dataclasses import dataclass

@dataclass
class Todo: id:int; title:str; done:bool

todos = TinyRedis(redis.from_url(YOUR_URL), Todo)

todo = todos.insert(Todo(1, "Create README example", False))
# or: todo = todos.insert(title="Create README example", done=False)
# if you don't pass `id`, a uuid4 id will be created for you
print(todos())  # Prints all todos
todo.done = True
todos.update(todo)
print(todos[todo.id])
todos.delete(todo.id)
```
