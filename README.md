# A car part webshop app to give an insight into my software development skills

# Feature checklist

| Feature | Status | Comment |
| --- | --- | --- |
| All products in a database | DONE | |
| Add a product to the shopping cart | DONE | |
| Remove a product from the shopping cart | DONE | |
| Order the current contents in the shopping cart | DONE | |
| Select a delivery date and time | DONE | |
| See an overview of all the products | DONE | |
| View the details of a product | DONE | |
| Use Postgres w/ Docker | DONE | |
| Implement a RESTful API | DONE | |
| Use an ORM | DONE | Django ORM |

# Setup

1. Create a .env file in the root folder and set DB_NAME, DB_USERNAME, and DB_PASSWORD in it
2. Run the image: ```docker-compose up -d --build```
3. Migrate: ```docker-compose exec web python manage.py migrate```
4. (Optional) Run the feature tests: ```docker-compose exec web python manage.py test```
5. Create a Django superuser (will get user ID 1): ```docker-compose exec web python manage.py createsuperuser```
6. On the Django admin page create a simple user (will have the id 2)
7. Add products on the Django admin page or via API like: ```curl -XPOST "http://127.0.0.1:8000/products/" -H "Content-Type: application/json" -d '{"name": "Lexani Rim Set", "details": "The beautiful Lexani Rim set"}'```
8. (Optional) Check the products you added: ```curl -XGET "http://127.0.0.1:8000/products/"```
9. (Optional) Check the details of a product: ```curl -XGET "http://127.0.0.1:8000/products/1/?fields=id,details"```
10. Add products to the cart like: ```curl -XPOST "http://127.0.0.1:8000/cart/2/" -H "Content-Type: application/json" -d '{"product_id": 1}'```
11. Check the cart contents: ```curl -XGET "http://127.0.0.1:8000/cart/2/"```
12. Try the rest of the features using the available endpoints

# Limitations

There is no user authentication & authorization yet due to time constraints. Features can be tried and tested using the test user ID 2.

# Future next steps

* See TODOs in the code
* 1 cart per user instead of the current single global cart
* User authentication & authorizations
* Time zone support
