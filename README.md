# SUSTAINABLE - CLOTHING
![cloth](https://github.com/Icepeak01/sustainably-clothing/assets/153315141/d460c964-f12a-459a-b2fe-4de76c75b7ea)
# OVERVIEW
This project is focused on sales and inventory both during and outside of marketing campaigns for a clothing firm. We have received sustainable data for a clothing store known as sustainable apparel. The data covers the period of about 5 months and the fields includes product category, product price and the firm sales record during and after some marketing campaigns carried out.

The objective is to prepare/insert the data, analyze and answer some thought provoking questions using SQL, and subsequently outline the results that would enhance decision making capabilities and boost profits for the apparel store. The objectives was achieved by;

1. Data Collection
2. Database Creation
3. Table Creation and Inserting Values
4. ERD set up


Top questions answered are:
1. How many transactions were completed during each marketing campaign?
2. Which product had the highest sales quantity?
3. What is the total revenue generated from each marketing campaign?
4. What is the top-selling product category based on the total revenue generated?
5. Which products had a higher quantity sold compared to the average quantity sold?
6. What is the average revenue generated per day during the marketing campaigns?
7. What is the percentage contribution of each product to the total revenue?

### Data Collection
The project's dataset came from an internet data storage source. There were three distinct tables in the dataset, each containing different data that needed to be entered. The three distint tables are;
  1. marketing campaign: This table has 5 columns which are campaign_id, campaign_name, product_id, start_date, end_date and has 3 rows
  2. Transactions: this table consist of 4 columns transaction_id, product_id, quantity, purchase_date, and has 64 unique transactions.
  3. sustainable clothing: This table also has 5 columns which are product_id, product_name, category, size, price and 20 uique products.

### Database Creation
The database was created using postgres GUI
![Screenshot (646)](https://github.com/Icepeak01/sustainably-clothing/assets/153315141/abfd9f3d-4f6e-42a7-bbd0-0bc73a82e62c)

### Table Creation and Inserting Values
CREATE TABLE sustainable_clothing (
product_id INT PRIMARY KEY,
product_name VARCHAR(100),
category VARCHAR(50),
size VARCHAR(10),
price FLOAT
);

INSERT INTO sustainable_clothing (product_id, product_name, category, size, price)
VALUES
(1, 'Organic Cotton T-Shirt', 'Tops', 'S', 29.99),

(2, 'Recycled Denim Jeans', 'Bottoms', 'M', 79.99),

(3, 'Hemp Crop Top', 'Tops', 'L', 24.99),

(4, 'Bamboo Lounge Pants', 'Bottoms', 'XS', 49.99),

(5, 'Eco-Friendly Hoodie', 'Outerwear', 'XL', 59.99),

(6, 'Linen Button-Down Shirt', 'Tops', 'M', 39.99),

(7, 'Organic Cotton Dress', 'Dresses', 'S', 69.99),

(8, 'Sustainable Swim Shorts', 'Swimwear', 'L', 34.99),

(9, 'Recycled Polyester Jacket', 'Outerwear', 'XL', 89.99),

(10, 'Bamboo Yoga Leggings', 'Activewear', 'XS', 54.99),

(11, 'Hemp Overalls', 'Bottoms', 'M', 74.99),

(12, 'Organic Cotton Sweater', 'Tops', 'L', 49.99),

(13, 'Cork Sandals', 'Footwear', 'S', 39.99),

(14, 'Recycled Nylon Backpack', 'Accessories', 'One Size', 59.99),

(15, 'Organic Cotton Skirt', 'Bottoms', 'XS', 34.99),

(16, 'Hemp Baseball Cap', 'Accessories', 'One Size', 24.99),

(17, 'Upcycled Denim Jacket', 'Outerwear', 'M', 79.99),

(18, 'Linen Jumpsuit', 'Dresses', 'L', 69.99),

(19, 'Organic Cotton Socks', 'Accessories', 'M', 9.99),

(20, 'Bamboo Bathrobe', 'Loungewear', 'XL', 69.99);

CREATE TABLE marketing_campaigns (
campaign_id INT PRIMARY KEY,
campaign_name VARCHAR(100),
product_id INT,
start_date DATE,
end_date DATE,
FOREIGN KEY (product_id) REFERENCES sustainable_clothing (product_id)
);

INSERT INTO marketing_campaigns (campaign_id, campaign_name, product_id, start_date, end_date)
VALUES
(1, 'Summer Sale', 2, '2023-06-01', '2023-06-30'),

(2, 'New Collection Launch', 10, '2023-07-15', '2023-08-15'),

(3, 'Super Save', 7, '2023-08-20', '2023-09-15');

CREATE TABLE transactions (
transaction_id INT PRIMARY KEY,
product_id INT,
quantity INT,
purchase_date DATE,
FOREIGN KEY (product_id) REFERENCES sustainable_clothing (product_id)
);

INSERT INTO transactions (transaction_id, product_id, quantity, purchase_date)
VALUES
(1, 2, 2, '2023-06-02'),

(2, 14, 1, '2023-06-02'),

(3, 5, 2, '2023-06-05'),

(4, 2, 1, '2023-06-07'),

(5, 19, 2, '2023-06-10'),

(6, 2, 1, '2023-06-13'),

(7, 16, 1, '2023-06-13'),

(8, 10, 2, '2023-06-15'),

(9, 2, 1, '2023-06-18'),

(10, 4, 1, '2023-06-22'),

(11, 18, 2, '2023-06-26'),

(12, 2, 1, '2023-06-30'),

(13, 13, 1, '2023-06-30'),

(14, 4, 1, '2023-07-04'),

(15, 6, 2, '2023-07-08'),

(16, 15, 1, '2023-07-08'),

(17, 9, 2, '2023-07-12'),

(18, 20, 1, '2023-07-12'),

(19, 11, 1, '2023-07-16'),

(20, 10, 1, '2023-07-20'),

(21, 12, 2, '2023-07-24'),

(22, 5, 1, '2023-07-29'),

(23, 10, 1, '2023-07-29'),

(24, 10, 1, '2023-08-03'),

(25, 19, 2, '2023-08-08'),

(26, 3, 1, '2023-08-14'),

(27, 10, 1, '2023-08-14'),

(28, 16, 2, '2023-08-20'),

(29, 18, 1, '2023-08-27'),

(30, 12, 2, '2023-09-01'),

(31, 13, 1, '2023-09-05'),

(32, 7, 1, '2023-09-05'),

(33, 6, 1, '2023-09-10'),

(34, 15, 2, '2023-09-14'),

(35, 9, 1, '2023-09-14'),

(36, 11, 2, '2023-09-19'),

(37, 17, 1, '2023-09-23'),

(38, 2, 1, '2023-09-28'),

(39, 14, 1, '2023-09-28'),

(40, 5, 2, '2023-09-30'),

(41, 16, 1, '2023-10-01'),

(42, 12, 2, '2023-10-01'),

(43, 1, 1, '2023-10-01'),

(44, 7, 1, '2023-10-02'),

(45, 18, 2, '2023-10-03'),

(46, 12, 1, '2023-10-03'),

(47, 13, 1, '2023-10-04'),

(48, 4, 1, '2023-10-05'),

(49, 12, 2, '2023-10-05'),

(50, 7, 1, '2023-10-06'),

(51, 4, 2, '2023-10-08'),

(52, 8, 2, '2023-10-08'),

(53, 16, 1, '2023-10-09'),

(54, 19, 1, '2023-10-09'),

(55, 1, 1, '2023-10-10'),

(56, 18, 2, '2023-10-10'),

(57, 2, 1, '2023-10-10'),

(58, 15, 2, '2023-10-11'),

(59, 17, 2, '2023-10-13'),

(60, 13, 1, '2023-10-13'),

(61, 10, 2, '2023-10-13'),

(62, 9, 1, '2023-10-13'),

(63, 19, 2, '2023-10-13'),

(64, 20, 1, '2023-10-14');

### ERD Setup
![Screenshot (597)](https://github.com/Icepeak01/sustainably-clothing/assets/153315141/7917940a-547d-4454-8b6a-803da1f1b432)

## Analysis
### 1. How many transactions were completed during each marketing campaign?
![Screenshot (606)](https://github.com/Icepeak01/sustainably-clothing/assets/153315141/f590d3a9-b5fc-4fb1-96d2-aff1b12b0b3c)

### Insights:
With seven completed deals, it appears that this summer's sales campaign has generated the most interest. This may suggest that the Summer Sale campaign was very successful in generating interest from customers and promoting sales.
Six purchases were made during the New Collection Launch campaign, suggesting that consumers were reasonably interested. This implies that the launch of new lines or items was effective in increasing sales.
The Super Save campaign had the fewest transactions (3), but it still generated some interest from customers. Comparing this campaign to the others, it is clear that its effectiveness in generating transactions was lower. To determine why this campaign did not work as expected, more research may be required.

### Recommendation:
Keep Successful Promotions Going: If a sale or promotion works well (like the Summer Sale), it's smart to repeat it in the future. Find out why it was successful, like what deals people liked, and do more of that.
Make Product Launches Exciting: When launching new products (like the New Collection Launch), make sure they're appealing to customers. Learn what customers want and launch products they're interested in.
Improve Less Successful Promotions: If a promotion doesn't do as well (like Super Save), figure out why. Maybe the deals weren't good enough or the timing was off. Make changes to make it better next time.
Keep an Eye on Results: Use tools to track how well promotions are doing. Look at things like how many people are buying and how much money is being made. Use this information to decide what to do next.
Always Try to Make Things Better: Keep testing different ways to promote products and see what works best. Make changes based on what customers like and don't like. The goal is to keep getting better at promoting and selling products.

### 2.  Which product had the highest sales quantity?
![Screenshot (607)](https://github.com/Icepeak01/sustainably-clothing/assets/153315141/720b8268-45cb-4dcb-a826-155973f4b818)

### Insights:
The best-selling items include the "Organic Cotton Sweater," "Bamboo Yoga Leggings," and "Recycled Denim Jeans," each with at least eight units sold. 
This suggests that consumers have a high desire for these products. A wide range of eco-friendly apparel and accessories, from leggings and sweaters to sandals and backpacks, are included in the sales data. This variety shows that consumers are drawn to eco-friendly goods that meet a variety of requirements and tastes.
In comparison to other products, sales of products like "Recycled Nylon Backpack," "Sustainable Swim Shorts," and "Organic Cotton T-Shirt" are lower. They nevertheless still offer opportunities for the company to expand. It is possible to find chances for development and expansion in these product categories by looking into the factors that are causing fewer sales, such as pricing, product characteristics, or marketing visibility.
 When examining sales data, seasonal trends and variations in demand should be taken into consideration. Product categories such as "Bamboo Bathrobe" and "Hemp Crop Top" may witness heightened sales throughout particular times of the year, which could be attributed to shifting consumer tastes or fashion and lifestyle trends.

### Recommendation:
Focus on Popular Products: Put more effort into promoting products like sweaters, leggings, and jeans because they're selling well.
Offer More Variety: Think about adding different styles or options for popular items to attract more customers. Fix Slow-Selling Products: Look at products that aren't selling much and figure out why. Make changes to make them more appealing, or think about getting rid of them if they're not working.
Promote Seasonal Stuff: Promote products like bathrobes or crop tops when it's the right season for them, like promoting swimsuits in the summer. Talk to Customers: Ask customers what they like and don't like, so you can offer products they're more likely to buy. Tell People About Sustainability: Let customers know when products are eco-friendly, like if they're made from organic cotton or recycled materials. Offer Related Stuff: Try to sell other things that go well with what customers are already buying, like socks to go with shoes. Keep Learning and Improving: Keep an eye on what's selling and what's not, and be ready to change things up to keep customers happy and keep sales going up.

### 3. .   What is the total revenue generated from each marketing campaign?
![Screenshot (608)](https://github.com/Icepeak01/sustainably-clothing/assets/153315141/16a9ab3c-5dfc-481a-b926-03aa553e32a0)


### Insights: 
The Summer Sale campaign was the most profitable, demonstrating its high level of success. Customers probably cherished the special offers or discounts made during this period. The New Collection Launch was financially successful as well, suggesting that consumers were drawn to the newly unveiled goods. This indicates that consumers enjoy novelty. Out of all the campaigns, the Super Save campaign brought in less money. This implies that consumers may not have found the offers or reductions to be as enticing.

### Recommendations:
Remain with What Works: Continue running the most profitable campaigns, such as the Summer Sale and New Collection Launch, they have a track record of success. 
Increase the Appeal of Deals: Consider the reasons behind the great reception of the new collection launch and summer sale. To increase revenue, strive to improve transactions in the future. 
Improve the "Super Save" Promotion: The revenue from the Super Save campaign was lower. Consider ways to increase its appeal to consumers, such as by providing better discounts or spreading the word more widely. 
Try Various Approaches to Reach People: Spread the word about deals using more than one method. To reach more people, try sending emails, collaborating with influencers, or using social media.

### 4.   What is the top-selling product category based on the total revenue generated?
![Screenshot (609)](https://github.com/Icepeak01/sustainably-clothing/assets/153315141/51f9e574-1a93-44ef-b1cd-7e465c3abe70)


### Insights: 
 "Bottoms" are the best-selling product category, suggesting that consumers have a strong need for products such as "Organic cotton skirts," "Hemp overalls," "Bamboo lounge pants," and "Recycled denim jeans." 
The popularity of "Bottoms" may be a reflection of seasonal preferences or current fashion trends, offering important information for product development and inventory planning.
Identifying "Bottoms'" success allows for the cross-selling of related goods and the customization of marketing initiatives to increase sales.
It's critical to give "Bottoms" first priority when it comes to inventory control in order to guarantee sufficient stock levels and diversity to successfully satisfy consumer demand.

### Recommendations:
To accommodate a wide range of customer preferences, increase the selection of "Bottoms" products available. Take into account introducing new ideas, styles, or materials in response to consumer feedback and fashion trends.  To promote upselling and raise the average order value, put together packages or bundle deals that contain supplementary items like shirts or accessories with "Bottoms". Invest marketing funds and promotional activities on "Bottoms" in order to take advantage of their renown and boost sales. To grab customers' interest and encourage a purchase, draw attention to important details, fashions, or special offers. To improve the shopping experience and promote repeat sales of "Bottoms" products, interact with customers through tailored marketing campaigns, loyalty programs, or product recommendations. In other to keep abreast of consumer preferences, fashion trends, and competition products in the "Bottoms" area, conduct market research on a regular basis. Make efficient use of the information acquired to guide price plans, marketing campaigns, and product development. Also, make sure that "Bottoms" goods are up to par in terms of fit, design, and durability by placing a high priority on both customer satisfaction and product quality to gain the trust and loyalty of your customers.

### 5. Which products had a higher quantity sold compared to the average quantity sold?
![Screenshot (610)](https://github.com/Icepeak01/sustainably-clothing/assets/153315141/ca794b5f-c0a7-4fb4-b61f-e5dbe05d4a35)

### 6. What is the average revenue generated per day during the marketing campaigns?

![Screenshot (611)](https://github.com/Icepeak01/sustainably-clothing/assets/153315141/8f06bd76-7a65-4676-936b-84c1d0afc9ef)

### 7. What is the percentage contribution of each product to the total revenue?

![Screenshot (612)](https://github.com/Icepeak01/sustainably-clothing/assets/153315141/1b69388c-f119-4f51-9429-9bb3a026f5ab)


### 8. Compare the average quantity sold during marketing campaigns to outside the marketing campaigns

##### AVG QTY SOLD DURING MARKETING CAMPAIGNS
![Screenshot (613)](https://github.com/Icepeak01/sustainably-clothing/assets/153315141/92a4d8e3-b773-49cb-90af-89ee9b23409a)

#### AVG QTY SOLD OUTSIDE MARKETING CAMPAIGNS
![Screenshot (614)](https://github.com/Icepeak01/sustainably-clothing/assets/153315141/4519f470-5995-4285-8da4-6492a9b14444)


### 9. Compare the revenue generated by products inside the marketing campaigns to outside the campaigns
 
 
 #### REVENUE GENERATED DURING MARKETING CAMPAIGN
![Screenshot (615)](https://github.com/Icepeak01/sustainably-clothing/assets/153315141/281ef726-9aad-4924-b258-32b8ec80250a)

#### REVENUE GENERATED OUTSIDE MARKETING CAMPAIGN
![Screenshot (617)](https://github.com/Icepeak01/sustainably-clothing/assets/153315141/47abdd4a-4ca6-4954-a3de-6c54fc1deddd)


### 10.  Rank the products by their average daily quantity sold
![Screenshot (618)](https://github.com/Icepeak01/sustainably-clothing/assets/153315141/d9fdb217-5f9d-48c8-9b83-4c159ef6a890)

