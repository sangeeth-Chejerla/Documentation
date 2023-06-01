# Model Fields :

CharField: Used to store strings or text data with a limited length.

TextField: Suitable for storing longer text data without a predetermined length limit.

IntegerField: Stores integer values.

FloatField: Stores floating-point numbers.

BooleanField: Represents boolean values (True or False).

DateTimeField: Stores date and time information.

DateField: Stores date information only.

TimeField: Stores time information only.

EmailField: Specifically designed for storing email addresses.

URLField: Used for storing URLs.

FileField: Stores uploaded files.

ImageField: Similar to FileField but optimized for storing images.

ForeignKey: Establishes a many-to-one relationship with another model.

ManyToManyField: Represents a many-to-many relationship between models.

OneToOneField: Defines a one-to-one relationship between models.

DecimalField: Stores decimal numbers with a fixed number of decimal places.






UUIDField: Stores universally unique identifiers (UUIDs).

BinaryField: Stores binary data, such as images or files, as a byte array.

PositiveIntegerField: Stores positive integer values.

SlugField: Used for storing a short, human-readable value suitable for URL paths.

These are just a few examples of the most important fields in django.

---

# syntax :-

## DecimalField
For example:- to store numbers up to 999.99 with a resolution of 2 decimal places, you’d use:

models.DecimalField(..., max_digits=5, decimal_places=2)

## CharField
CharField(max_length=None, **options)¶
A string field, for small- to large-sized strings.

## DateField:

Syntax: date_field_name = models.DateField(arguments)
Example: date_of_birth = models.DateField(auto_now_add=True)

## EmailField:

Syntax: email_field_name = models.EmailField(arguments)
Example: email = models.EmailField(max_length=255, unique=True)


## SlugField:

Syntax: slug_field_name = models.SlugField(arguments)
Example: slug = models.SlugField(max_length=100, unique=True)


## TextField:

Syntax: text_field_name = models.TextField(arguments)
Example: description = models.TextField(blank=True, null=True)


## ForeignKey (Many-to-One relationship):

Syntax: foreign_key_name = models.ForeignKey(related_model, arguments)
Example: author = models.ForeignKey(User, on_delete=models.CASCADE)


## OneToOneField (One-to-One relationship):

Syntax: one_to_one_field_name = models.OneToOneField(related_model, arguments)
Example: profile = models.OneToOneField(UserProfile, on_delete=models.CASCADE)


## ManyToManyField (Many-to-Many relationship):

Syntax: many_to_many_field_name = models.ManyToManyField(related_model, arguments)
Example: categories = models.ManyToManyField(Category)

## BooleanField:

Syntax: boolean_field_name = models.BooleanField(arguments)
Example: is_active = models.BooleanField(default=True)

## DateTimeField:

Syntax: datetime_field_name = models.DateTimeField(arguments)
Example: created_at = models.DateTimeField(auto_now_add=True)


## FloatField:

Syntax: float_field_name = models.FloatField(arguments)
Example: price = models.FloatField(default=0.0)


## URLField:

Syntax: url_field_name = models.URLField(arguments)
Example: website = models.URLField(max_length=200)

## ImageField:

Syntax: image_field_name = models.ImageField(arguments)
Example: profile_picture = models.ImageField(upload_to='images/')


## BinaryField:

Syntax: binary_field_name = models.BinaryField(arguments)
Example: file_data = models.BinaryField()


## IntegerField:

Syntax: integer_field_name = models.IntegerField(arguments)
Example: age = models.IntegerField(default=0)

## PositiveIntegerField:

Syntax: positive_integer_field_name = models.PositiveIntegerField(arguments)
Example: votes = models.PositiveIntegerField(default=0)


## UUIDField:

Syntax: uuid_field_name = models.UUIDField(arguments)
Example: uuid = models.UUIDField(unique=True)

## Note: Replace date_field_name, email_field_name, slug_field_name, text_field_name, foreign_key_name, one_to_one_field_name, and many_to_many_field_name with the desired field names in your model.
