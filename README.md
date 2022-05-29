# food-ordering-application
You have to design a Food Ordering app for a restaurant.   The application will have a log-in for admin and users.   Admin will have the following functionalities:      Add new food items. Food Item will have the following details:     FoodID //It should be generated automatically by the application.     Name     Quantity. For eg, 100ml, 250gm, 4pieces etc     Price     Discount     Stock. Amount left in stock in the restaurant.     Edit food items using FoodID.     View the list of all food items.     Remove a food item from the menu using FoodID.    The user will have the following functionalities:      Register on the application. Following to be entered for registration:     Full Name     Phone Number     Email     Address     Password     Log in to the application     The user will see 3 options:     Place New Order     Order History     Update Profile     Place New Order: The user can place a new order at the restaurant.     Show list of food. The list item should as follows:     1. Tandoori Chicken (4 pieces) [INR 240]     2. Vegan Burger (1 Piece) [INR 320]     3. Truffle Cake (500gm) [INR 900]     Users should be able to select food by entering an array of numbers. For example, if the user wants to order Vegan Burger and Truffle Cake they should enter [2, 3]     Once the items are selected user should see the list of all the items selected. The user will also get an option to place an order.     Order History should show a list of all the previous orders     Update Profile: the user should be able to update their profi
class Restaurant(models.Model):
    OPEN = 1
    CLOSED = 2

    OPENING_STATUS = (
        (OPEN, 'open'),
        (CLOSED, 'closed'),
        )

    BREAKFAST = 1
    LAUNCH = 2
    DINNER = 3
    DELIVERY = 4
    CAFE = 5
    LUXURY = 6
    NIGHT = 7

    FEATURE_CHOICES = (
        (BREAKFAST, 'breakfast'),
        (LAUNCH, 'launch'),
        (DINNER, 'dinner'),
        (DELIVERY, 'delivery'),
        (CAFE, 'cafe'),
        (LUXURY, 'luxury dining'),
        (NIGHT, 'night life'),
        )

    MONDAY = 1
    TUESDAY = 2
    WEDNESDAY = 3
    THURSDAY = 4
    FRIDAY = 5
    SATURDAY = 6
    SUNDAY = 7


    TIMING_CHOICES = (
        (MONDAY, 'monday'),
        (TUESDAY, 'tuesday'),
        (WEDNESDAY, 'wednesday'),
        (THURSDAY, 'thursday'),
        (FRIDAY, 'friday'),
        (SATURDAY, 'saturday'),
        (SUNDAY, 'sunday'),
        )
    user = models.ForeignKey(User)
    restaurant_name = models.CharField(max_length=150, db_index=True)
    slug = models.SlugField(max_length=150, db_index=True)
    address = models.CharField(max_length=100)
    city = models.CharField(max_length=100)
    restaurant_phone_number = models.PositiveIntegerField()
    restaurant_email = models.EmailField(blank=True, null=True)
    owner_email = models.EmailField(blank=True, null=True)
    opening_status = models.IntegerField(choices=OPENING_STATUS, default=OPEN)
    email = models.EmailField()
    restaurant_website = models.TextField(validators=[URLValidator()])
    features = models.IntegerField(choices=FEATURE_CHOICES, default=DINNER)
    timings = models.IntegerField(choices=TIMING_CHOICES, default=MONDAY)
    opening_from = models.TimeField()
    opening_to = models.TimeField()
    facebook_page = models.TextField(validators=[URLValidator()])
    twitter_handle = models.CharField(max_length=80, blank=True, null=True)
    other_details = models.TextField()
    available = models.BooleanField(default=True)
    created = models.DateTimeField(auto_now_add=True)
    updated = models.DateTimeField(auto_now=True)


    class Meta:
        verbose_name = 'restaurant'
        verbose_name_plural = 'restaurants'
        ordering = ('restaurant_name',)
        index_together = (('id','slug'),)


    def __str__(self):
        return self.restaurant_name

    # def get_absolute_url(self):
    #   return reverse('restaurant:restaurant_detail', args=[self.id, self.slug])



class Category(models.Model):
    name = models.CharField(max_length=120,db_index=True) #veg, non-veg
    slug = models.SlugField(max_length=120,db_index=True)

    class Meta:
        ordering=('name', )
        verbose_name = 'category'
        verbose_name_plural = 'categories'

    def __str__(self):
        return self.name



class Menu(models.Model):
    category = models.ForeignKey(Category, related_name="menu")
    restaurant = models.ForeignKey(Restaurant, related_name="restaurant_menu")
    name = models.CharField(max_length=120,db_index=True)
    slug = models.SlugField(max_length=120,db_index=True)
    image = models.ImageField(upload_to='products/%Y/%m/%d', blank=True)
    description = models.TextField(blank=True)
    price = models.DecimalField(max_digits=10,decimal_places=2)
    stock = models.PositiveIntegerField()
    available = models.BooleanField(default=True)
    created = models.DateTimeField(auto_now_add=True)
    updated = models.DateTimeField(auto_now=True)


    class Meta:
        ordering=('name', )
        index_together = (('id', 'slug'), )
        verbose_name = 'menu'

    def __str__(self):
        return self.name

    # def get_absolute_url(self):
    #   return reverse('restaurant:menu_detail', args=[self.id, self.slug])
