<a name="br1"></a> 

In [2]: **import** pandas **as** pd

**import** matplotlib.pyplot **as** plt

**import** seaborn **as** sns

In [3]: df **=** pd**.**read\_csv('Diwali Sales Data.csv', encoding**=**'unicode\_escape')

In [4]: df

Out[4]:

**User\_ID Cust\_name Product\_ID Gender Age Group Age Marital\_Status**

**State**

**Zone**

**Occupation Product\_Category Orders Amount**

**0**

**1**

1002903

1000732

1001990

1001425

1000588

...

Sanskriti P00125942

Kartik P00110942

Bindu P00118542

Sudevi P00237842

Joni P00057942

F

F

Teenager

Adult

28

35

35

16

28

...

0

1

1

0

1

...

1

0

0

0

0

Maharashtra Western

Healthcare

Govt

Auto

Auto

1

3

3

2

2

...

4

3

4

3

3

23952\.0

23934\.0

23924\.0

23912\.0

23877\.0

...

Andhra Pradesh Southern

**2**

F

Adult

Uttar Pradesh

Central

Automobile

Construction

Auto

**3**

M

M

...

M

M

F

Teenager

Teenager

...

Karnataka Southern

Auto

**4**

Gujarat Western Food Processing

Auto

**...**

...

Manning P00296942

**11235** 1004089 Reichenbach P00171342

...

...

...

...

Chemical

Healthcare

Textile

...

**11234** 1000695

Teenager

Adult

19

33

40

37

19

Maharashtra Western

Haryana Northern

Office

Veterinary

Office

Office

Office

370\.0

367\.0

**11236** 1001209

**11237** 1004023

**11238** 1002744

Oshin P00201342

Noonan P00059442

Brumley P00281742

Adult

Madhya Pradesh

Central

Karnataka Southern

Maharashtra Western

213\.0

M

F

Adult

Agriculture

Healthcare

206\.0

Teenager

188\.0

11239 rows × 13 columns

In [5]: df**.**shape

Out[5]: (11239, 13)

In [6]: df**.**isnull()**.**sum()

Out[6]: User\_ID

Cust\_name

Product\_ID

Gender

0

0

0

0

0

0

0

0

0

0

0

0

0

Age Group

Age

Marital\_Status

State

Zone

Occupation

Product\_Category

Orders

Amount

dtype: int64

In [7]: df**.**info()

<class 'pandas.core.frame.DataFrame'>

RangeIndex: 11239 entries, 0 to 11238

Data columns (total 13 columns):

\# Column

\--- ------

0 User\_ID

1 Cust\_name

2 Product\_ID

3 Gender

4 Age Group

5 Age

6 Marital\_Status

7 State

Non-Null Count Dtype

\-------------- -----

11239 non-null int64

11239 non-null object

11239 non-null object

11239 non-null object

11239 non-null object

11239 non-null int64

11239 non-null int64

11239 non-null object

11239 non-null object

11239 non-null object

8 Zone

9 Occupation

10 Product\_Category 11239 non-null object

11 Orders

12 Amount

11239 non-null int64

11239 non-null float64

dtypes: float64(1), int64(4), object(8)

memory usage: 1.1+ MB

In [8]: df**.**describe()

Out[8]: **User\_ID**

**count** 1.123900e+04 11239.000000 11239.000000 11239.000000 11239.000000

**Age Marital\_Status**

**Orders**

**Amount**

**mean** 1.003004e+06

**std** 1.716039e+03

**min** 1.000001e+06

**25%** 1.001492e+06

**50%** 1.003064e+06

**75%** 1.004426e+06

**max** 1.006040e+06

35\.410357

12\.753866

12\.000000

27\.000000

33\.000000

43\.000000

92\.000000

0\.420055

0\.493589

0\.000000

0\.000000

0\.000000

1\.000000

1\.000000

2\.489634

1\.114967

1\.000000

2\.000000

2\.000000

9453\.610858

5222\.355869

188\.000000

5443\.000000

8109\.000000

3\.000000 12675.000000

4\.000000 23952.000000

In [9]: df**.**info()

<class 'pandas.core.frame.DataFrame'>

RangeIndex: 11239 entries, 0 to 11238

Data columns (total 13 columns):

\# Column

\--- ------

0 User\_ID

1 Cust\_name

2 Product\_ID

3 Gender

4 Age Group

5 Age

6 Marital\_Status

7 State

Non-Null Count Dtype

\-------------- -----

11239 non-null int64

11239 non-null object

11239 non-null object

11239 non-null object

11239 non-null object

11239 non-null int64

11239 non-null int64

11239 non-null object

11239 non-null object

11239 non-null object

8 Zone

9 Occupation

10 Product\_Category 11239 non-null object

11 Orders

12 Amount

11239 non-null int64

11239 non-null float64

dtypes: float64(1), int64(4), object(8)

memory usage: 1.1+ MB

In [10]: df['Amount'] **=** df['Amount']**.**astype('int')

In [11]: df['Amount']**.**dtypes

Out[11]: dtype('int32')

**Gender**

In [14]: df**.**columns

Out[14]: Index(['User\_ID', 'Cust\_name', 'Product\_ID', 'Gender', 'Age Group', 'Age',

'Marital\_Status', 'State', 'Zone', 'Occupation', 'Product\_Category',

'Orders', 'Amount'],

dtype='object')

In [15]: ax **=** sns**.**countplot(x**=**'Gender', data **=** df)

**for** bars **in** ax**.**containers:

ax**.**bar\_label(bars)

In [48]: sales **=** df**.**groupby(['Gender'], as\_index**=False**)['Amount']**.**sum()**.**sort\_values(by**=**'Amount', ascending **= False**)

sales

Out[48]:

**Gender**

**Amount**

74335853

31913276

**0**

**1**

F

M

In [52]: sns**.**barplot(x**=**'Gender', y**=**'Amount', data**=**sales)

Out[52]: <Axes: xlabel='Gender', ylabel='Amount'>

\***From the above graphs we can see that most of the buyers are females and also females have more purshasing power than men.**\*

**Age Group**

In [53]: df**.**columns

Out[53]: Index(['User\_ID', 'Cust\_name', 'Product\_ID', 'Gender', 'Age Group', 'Age',

'Marital\_Status', 'State', 'Zone', 'Occupation', 'Product\_Category',

'Orders', 'Amount'],

dtype='object')

In [67]: ax **=** sns**.**countplot(x**=**'Age Group', data**=**df, hue**=**'Gender')

**for** bars **in** ax**.**containers:

ax**.**bar\_label(bars)

In [59]: Age\_group **=** df**.**groupby(['Age Group'], as\_index**=False**)['Amount']**.**sum()**.**sort\_values(by**=**'Amount', ascending**=False**)

Age\_group

Out[59]:

**Age Group**

**Amount**

**0**

**2**

**1**

Adult 54913142

Teenager 37072031

Senior 14263956

In [66]: sns**.**barplot(x**=**'Age Group', y**=**'Amount', data**=**Age\_group)

Out[66]: <Axes: xlabel='Age Group', ylabel='Amount'>

\***From the Above graphs we can see that most of the buyers are Abult Females.**\*

**States**

In [68]: df**.**columns

Out[68]: Index(['User\_ID', 'Cust\_name', 'Product\_ID', 'Gender', 'Age Group', 'Age',

'Marital\_Status', 'State', 'Zone', 'Occupation', 'Product\_Category',

'Orders', 'Amount'],

dtype='object')

In [77]: sales\_orders **=** df**.**groupby(['State'],as\_index**=False**)['Orders']**.**sum()**.**sort\_values(by**=**'Orders', ascending**=False**)**.**head(10)

sales\_orders

Out[77]:

**State Orders**

**14**

**10**

**7**

Uttar Pradesh

4807

3810

3240

2740

2252

2051

1568

1137

1109

1066

Maharashtra

Karnataka

**2**

Delhi

**9**

Madhya Pradesh

Andhra Pradesh

Himachal Pradesh

Kerala

**0**

**5**

**8**

**4**

Haryana

**3**

Gujarat

In [78]: sns**.**set(rc**=**{'figure.figsize':(15,5)})

sns**.**barplot(x**=**'State', y**=**'Orders', data**=**sales\_orders)

Out[78]: <Axes: xlabel='State', ylabel='Orders'>

In [80]: sales\_amount **=** df**.**groupby(['State'],as\_index**=False**)['Amount']**.**sum()**.**sort\_values(by**=**'Amount', ascending**=False**)**.**head(10)

sales\_amount

Out[80]:

**State**

**Amount**

**14**

**10**

**7**

Uttar Pradesh 19374968

Maharashtra 14427543

Karnataka 13523540

Delhi 11603818

**2**

**9**

Madhya Pradesh

Andhra Pradesh

Himachal Pradesh

Haryana

8101142

8037146

4963368

4220175

4022757

3946082

**0**

**5**

**4**

**1**

Bihar

**3**

Gujarat

In [81]: sns**.**set(rc**=**{'figure.figsize':(15,5)})

sns**.**barplot(x**=**'State', y**=**'Amount', data**=**sales\_amount)

Out[81]: <Axes: xlabel='State', ylabel='Amount'>

\***From the above graphs we can see that most of orders are from Uttar Pradesh, Magarashtra, Kaenatka and Delhi respectfully.**\*

**Marital Status**

In [82]: df**.**columns

Out[82]: Index(['User\_ID', 'Cust\_name', 'Product\_ID', 'Gender', 'Age Group', 'Age',

'Marital\_Status', 'State', 'Zone', 'Occupation', 'Product\_Category',

'Orders', 'Amount'],

dtype='object')

In [16]: ax **=** sns**.**countplot(x**=**'Marital\_Status', data**=** df)

sns**.**set(rc**=**{'figure.figsize':(7,5)})

**for** bars **in** ax**.**containers:

ax**.**bar\_label(bars)

In [87]: sales\_marital **=** df**.**groupby(['Marital\_Status','Gender'], as\_index**=False**)['Amount']**.**sum()**.**sort\_values(by**=**'Amount', ascending**=False**)

sales\_marital

Out[87]:

**Marital\_Status Gender**

**Amount**

43786646

30549207

18338738

13574538

**0**

**2**

**1**

**3**

0

1

0

1

F

F

M

M

In [88]: sns**.**barplot(x**=**'Marital\_Status', y **=** 'Amount', hue**=**'Gender', data**=**sales\_marital)

Out[88]: <Axes: xlabel='Marital\_Status', ylabel='Amount'>

\***From the above graphs we can see that most of the buyers are married(Women) and have high purchasing power**\*

Occupation

In [17]: df**.**columns

Out[17]: Index(['User\_ID', 'Cust\_name', 'Product\_ID', 'Gender', 'Age Group', 'Age',

'Marital\_Status', 'State', 'Zone', 'Occupation', 'Product\_Category',

'Orders', 'Amount'],

dtype='object')

In [24]: ax **=** sns**.**countplot(x**=**'Occupation', data**=**df)

sns**.**set(rc**=**{'figure.figsize':(20,5)})

**for** bars **in** ax**.**containers:

ax**.**bar\_label(bars)

In [17]: sales\_occup **=** df**.**groupby(['Occupation'],as\_index**=False**)['Amount']**.**sum()**.**sort\_values(by**=**'Amount', ascending**=False**)

sales\_occup

Out[17]:

**Occupation**

**Amount**

**10**

**8**

IT Sector 14755079

Healthcare 13034586

Aviation 12602298

Banking 10770610

**2**

**3**

**7**

Govt

Hospitality

Media

8517212

6376405

6295832

5368596

5297436

4981665

4783170

4070670

3597511

3204972

2593087

**9**

**12**

**1**

Automobile

Chemical

**4**

**11**

**13**

**6**

Lawyer

Retail

Food Processing

Construction

Textile

**5**

**14**

**0**

Agriculture

Product Category

In [ ]: df**.**columns

In [26]: sns**.**barplot(x**=**'Occupation', y**=**'Amount', data**=**sales\_occup)

Out[26]: <Axes: xlabel='Occupation', ylabel='Amount'>

**From the above graph we can see that most of the buyers are from IT Sector, Healthcare, Aviation, Banking and Govt.**

In [22]: ax **=** sns**.**countplot(x**=**'Product\_Category', data**=**df)

sns**.**set(rc**=**{'figure.figsize':(20,5)})

**for** bars **in** ax**.**containers:

ax**.**bar\_label(bars)

In [28]: sales\_prod **=** df**.**groupby(['Product\_Category'], as\_index**=False**)['Amount']**.**sum()**.**sort\_values(by**=**'Amount', ascending**=False**)**.**head(10)

sales\_prod

Out[28]:

**Product\_Category**

**Amount**

**6**

**3**

Food 33933883

Clothing & Apparel 16495019

Electronics & Gadgets 15643846

Footwear & Shoes 15575209

**5**

**7**

**8**

Furniture

Games & Toys

Sports Products

Beauty

5440051

4331694

3635933

1959484

1958609

1676051

**9**

**14**

**1**

**0**

Auto

**15**

Stationery

In [27]: sns**.**barplot(x**=**'Product\_Category', y **=** 'Amount', data **=** sales\_prod)

Out[27]: <Axes: xlabel='Product\_Category', ylabel='Amount'>

**From the above graph we can see that most of the sold products are Food, Clothing & Apparel, Electronics & Gadgets and Footwear & shoes..**

Conclusion

Married Adults from Uttar Pradesh, Magarashtra, Kaenatka and Delhi working in IT Sector, Healthcare, Aviation, Banking and Govt are more likely to buy a product from Food, Clothing & Apparel, Electronics &

Gadgets and Footwear & shoes.

