# The fullstack excercise

This is my solution to the fullstack excercise number 2 which requires setting up the Little Lemon back-end api.

## The excercise
Setting up the Little Lemon Back-end API

## Steps to setting up the Little Lemon Back-end API

- [x] **Step 1:** Run the following command to activate the virtual environment:
  ```bash
  pipenv shell
  ```
  Note: Make sure you run the command in the main working directory containing the manage.py file. 

- [x] **Step 2:** To make sure you have the necessary dependencies in place, run the following commands inside pipenv:
  ```bash
  pipenv install django
  pipenv install mysqlclient
  ```
  Note: If you are facing problems with using the virtual environment, you can try running the project without using pipenv.

- [x] **Step 3:** Create a file in the restaurant directory called forms.py and import the following:  
  The Booking model from the file models.py.  
  The module forms from the package django.

- [x] **Step 4:** Still inside the forms.py file, create a class called BookingForm and pass the forms.ModelForm as an argument to it. 

- [x] **Step 5:** Inside the class BookingForm, create another class called Meta and declare the following attributes inside it:  
  Model with the value Booking  
  Field with the value "__all__"

- [x] **Step 6:** In the terminal run both commands to perform the migrations.
  Note: Make sure you have created the correct MySQL user, assigned privileges, and configured the same database before you perform the migrations. 
  Run the necessary commands to make sure the user is created and can access the database.

- [x] **Step 7:** Open the file views.py and observe the code present inside it for the different views on the Little Lemon website. This was part of the functionality that was added using just the Django framework. 
  Remove the comments for the book() view function.
  Also remove the commenting for the import statement below:
  ```python
  # from .forms import BookingForm
  ```
  Observe the book() function that contains the functionality to accept the values added inside the form rendered on the page book.html.
  Note: The necessary imports are already added inside the views.py file. 

- [x] **Step 8:** Create a view function called bookings() and pass the request object to it as an argument. Follow the pseudo code below to add the necessary code for processing the form data. 
  Inside the bookings() view function, add the following pseudo code:
  Create a variable called date and assign it the following value:
  ```python
  request.GET.get('date',datetime.today().date())
  ```
  Create a variable called bookings and assign it the following value:
  ```python
  Booking.objects.all()
  ```
  Create a variable called booking_json and assign it the following value:
  ```python
  serialize('json', bookings)
  ```
  Return the render() function and pass the following arguments to it:
  ```python
  return render(request, "bookings.html", {"bookings": booking_json})
  ```
  Save the views.py file and ensure the code has no errors. 

- [x] **Step 9:** Go to the app-level urls.py file and remove the comment for the URL configuration of the view functions below: 
  bookings 
  book

- [x] **Step 10:** Open the file book.html file present inside the templates folder and update the code as per the instructions below.
  Add a heading using the <h1> tag that says, Make a reservation.

- [x] **Step 11:** Now step inside the <script> tags and add the following pseudo code to update the book.html file. 
  Call the log() function on console and pass the argument “Hello” inside it
  Call the function getElementById() on the document and pass the string "id_reservation_date" to it as an argument. 
  Suffix the code by adding a filter type="date" using a dot operator. 

- [x] **Step 12:** Now open the bookings.html file present inside the templates folder and update the code as per the instructions below.
  Add a heading using the <h1> tag that says All Reservations.

- [x] **Step 13:** Now step inside the <script> tags and add the following pseudo code to update the bookings.html file. 
  Create a constant called bookings and assign it the value of parse() function called over JSON. Pass the following argument inside the parse() function:
  ```javascript
  const bookings = JSON.parse('{{ bookings|safe }}');
  ```
  Call the log() function on console and pass bookings to it as an argument. 
  Create a constant called pretty_json and assign it the value of:
  ```javascript
  const pretty_json = JSON.stringify(bookings, null, 2);
  ```
  Note: Observe the code added inside the file bookings.html and save the file. Make sure there are no errors present in your code. 

- [x] **Step 14:** Open the file index.html and look for the comment:
  <!-- Add code here for book  -->
  Replace the comment with the following code:
  ```html
  <a href="{% url 'book' %}">Book your table now</a>
  ```

- [x] **Step 15:** Open the file _header.html inside the templates or partials folder and look for the comments:
  <!-- Add code here for the book template -->
  <!-- Add code here for the reservations template -->
  Replace the comment with the following code:
  ```html
  <li><a href="{% url 'book' %}">Book</a></li>
  <li><a href="{% url 'bookings' %}">Reservations</a></li>
  ```

- [x] **Step 16:** Add a command to run the server and go to the localhost URL.

- [x] **Step 17:** Go to the tab Book and add three entries inside the form.

- [x] **Step 18:** Once the entries are updated, go to the Reservations tab that you see in the menu bar. You will be able to observe the entries are updated. 

