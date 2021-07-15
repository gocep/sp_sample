# Sample Snowplow Micro usage

Demonstration of capturing different events in simple 2 page ecommerce site.
We have one main page containing the shop items and after clicking on single product, it opens the product details page

## Installation

Application code is inside app directory, it has 2 static html pages and related js and css files. On the root of the project there is docker-compose.yml file, where we have 2 services, one is for the web application, the second is the snowplow micro collector

To run the applications, execute this command
```bash
docker-compose up --build
```

## Usage

Web application will be running on port 8002, while the Snowplow Micro will run on its default port 9090

To access the web app, navigate to [localhost:8002](http://localhost:8002/)
To view the events stored on Snowplow Micro, navigate to [localhost:9090/micro/good](http://localhost:9090/micro/good)

Several different events are stored like page views, cart related events like adding product to cart, changing the quantity, removing product from cart, emptying the cart, checkout.

Another useful feature is adding events tracking on the related products on the single product page, which will be beneficial for testing which products are more clicked/wanted, and based on that to plan positioning of items, price discounts, improving recommendation engine

There is also event tracking on the product rating widget and social sharing widget to get more insights for the product.

Cart based trackers will allow us to find abandoned carts which is the most critical part in each ecommerce application and we can follow up with those customers on email, sms and improve the conversion rate.


## Trackers
For tracking of the events, there are several different options used.

Most of the events are using **trackStructEvent**

There is single usage of **trackAddToCart** on Add to cart from product details page (iglu:com.snowplowanalytics.snowplow/add_to_cart/jsonschema/1-0-0)

Social sharing events are using **trackSocialInteraction** (iglu:com.snowplowanalytics.snowplow/social_interaction/jsonschema/1-0-0)

## License
[MIT](https://choosealicense.com/licenses/mit/)