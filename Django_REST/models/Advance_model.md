# Abstract base class:-

In Django, an abstract base class is a way to define a model that provides common fields, methods, and behavior that can be inherited by other models. It allows you to encapsulate reusable functionality and avoid code duplication. Here's an example to explain the concept of an abstract base class in Django:

```python
from django.db import models

class TimeStampedModel(models.Model):
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)

    class Meta:
        abstract = True
```

In this example, we have defined an abstract base class called `TimeStampedModel`. It includes two fields: `created_at` and `updated_at`. These fields will automatically track the creation and modification timestamps of the models that inherit from this base class.

The `abstract = True` option in the `Meta` class indicates that `TimeStampedModel` is an abstract base class and should not create its own database table. It is meant to be inherited by other models to provide the timestamp functionality.

Now, let's create a model that inherits from `TimeStampedModel`:

```python
class Book(TimeStampedModel):
    title = models.CharField(max_length=100)
    author = models.ForeignKey(Author, on_delete=models.CASCADE)
    publication_date = models.DateField()
```

In this example, the `Book` model extends the `TimeStampedModel` abstract base class. By doing so, it inherits the `created_at` and `updated_at` fields, along with their behavior, from the `TimeStampedModel`. This eliminates the need to define those fields in the `Book` model explicitly.

By using abstract base classes, you can centralize common functionality, such as timestamps, in one place. It promotes code reuse, reduces redundancy, and provides a convenient way to manage shared fields, methods, or behaviors across multiple models.

It's important to note that abstract base classes cannot be instantiated directly. They exist solely to be inherited by other models. When you inherit from an abstract base class, Django creates a database table for the child model, including any fields inherited from the abstract base class.

Abstract base classes are a powerful feature in Django that helps organize and structure your models by extracting shared functionality into reusable components.

---

## Model Inheritance 

In Django, model inheritance allows you to create new models by inheriting fields and methods from existing models. This concept is commonly known as model inheritance or model subclassing. Along with model inheritance, you can also inherit meta options, such as ordering and constraints, to customize the behavior of the inherited models. Here's an example to explain model inheritance and meta inheritance in Django:

```python
from django.db import models

class BaseModel(models.Model):
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)

    class Meta:
        abstract = True
        ordering = ['created_at']

class Book(BaseModel):
    title = models.CharField(max_length=100)
    author = models.ForeignKey(Author, on_delete=models.CASCADE)
    publication_date = models.DateField()

    class Meta(BaseModel.Meta):
        verbose_name_plural = 'Books'

class Magazine(BaseModel):
    title = models.CharField(max_length=100)
    editor = models.ForeignKey(Editor, on_delete=models.CASCADE)
    publication_date = models.DateField()

    class Meta(BaseModel.Meta):
        verbose_name_plural = 'Magazines'
```

In this example, we have a base model called `BaseModel` that includes common fields like `created_at` and `updated_at`. The `BaseModel` is marked as abstract using `abstract = True` in its `Meta` class. This ensures that `BaseModel` itself will not create a database table but will be available for inheritance.

The `Book` model inherits from `BaseModel` and adds additional fields specific to books. Similarly, the `Magazine` model inherits from `BaseModel` and adds its own fields. By inheriting from `BaseModel`, both `Book` and `Magazine` models automatically include the `created_at` and `updated_at` fields.

To inherit meta options, such as ordering, from the `BaseModel`, we define a nested `Meta` class in each child model and specify `class Meta(BaseModel.Meta)`. This way, the child models inherit the ordering defined in the `BaseModel` and can also override or add their own meta options. In the example, both `Book` and `Magazine` models inherit the `ordering` option, which orders instances based on the `created_at` field.

Furthermore, the child models can customize other meta options. In the example, both `Book` and `Magazine` models define their own `verbose_name_plural` to provide specific names for plural objects.

Model inheritance and meta inheritance in Django allow you to create a hierarchy of models with shared fields, methods, and meta options. This approach promotes code reuse, simplifies model definitions, and allows for customization and specialization at each level of inheritance.

----
