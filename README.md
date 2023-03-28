# -Netflix-EDA-and-Visualization
In [1]: #import pandas import pandas as pd
Import Data
There are two methods for uploading data, which are listed below.
1. We can specify the file's absolute path. The code is as it is described here. We shall use the letter "r" at the beginning to prevent a Unicode code error.
Example:pd.read_csv(r"C:\Users\Satya\Downloads\projects\Netflix\netflix_titles.csv")
"An absolute path is a path that describes the location of a file or folder regardless of the current working directory; in fact, it is relative to the root directory."
1. The second method of data uploading involves passing relevant information, as seen below.
Example:pd.read_csv("netflix_titles.csv")
"A relative path is a path that describes the location of a file or folder in relative to the current working directory."
Khillar, S. (2018, May 15). Difference Between Absolute and relative path.
Differencebetween.net; Difference Between.
http://www.differencebetween.net/technology/difference-between-absolute-and-relativepath/
Vaibhav. (2021, December 18). Fix the Unicode Error found in a file path in python. Delft
Stack. https://www.delftstack.com/howto/python/unicode-error-python/
In [2]: #upload the data dataset=pd.read_csv("netflix_titles.csv")
Getting some basic information about the dataset
In [3]: #To show top-5 record of the dataset dataset.head()
Out[3]:	show_id	type	title	director	cast	country	date_added	release_year	rating	dur
 
Dick
	Kirsten	United	September
	0	s1	Movie	Johnson Is	NaN	2020	PG-13	9
	Johnson	States	25, 2021
Dead
1	s2	TV
Show	Blood &
Water	NaN	Ama
Qamata,
Khosi
Ngema,
Gail
Mabalane, Thaban...	South
Africa	September
24, 2021	2021	TV-
MA	Se
2	s3	TV
Show	Ganglands	Julien
Leclercq	Sami
Bouajila,
Tracy
Gotoas,
Samuel
Jouy, Nabi...	NaN	September
24, 2021	2021	TV-
MA	1 S
3	s4	TV
Show	Jailbirds
New
Orleans	NaN	NaN	NaN	September
24, 2021	2021	TV-
MA	1 S
4	s5	TV
Show	Kota
Factory	NaN	Mayur
More,
Jitendra
Kumar,
Ranjan
Raj, Alam
K...	India	September
24, 2021	2021	TV-
MA	Se
 
#To show bottom-5 record of the dataset dataset.tail()
In [4]:
Out[4]:	show_id	type	title	director	cast	country	date_added	release_year	rating
 
Mark
Ruffalo,
Jake
	David	United	November
	8802	s8803	Movie	Zodiac	Gyllenhaal,	2007	R
	Fincher	States	20, 2019
Robert
Downey
J...
8803	s8804	TV
Show	Zombie
Dumb	NaN	NaN	NaN	July 1, 2019	2018	TV-Y7
8804	s8805	Movie	Zombieland	Ruben
Fleischer	Jesse
Eisenberg,
Woody
Harrelson,
Emma
Stone, ...	United
States	November
1, 2019	2009	
8805	s8806	Movie	Zoom	Peter
Hewitt	Tim Allen,
Courteney
Cox,
Chevy
Chase, Kate Ma...	United
States	January 11,
2020	2006	PG
8806	s8807	Movie	Zubaan	Mozez
Singh	Vicky
Kaushal,
Sarah-
Jane Dias,
Raaghav Chanan...	India	March 2,
2019	2015	TV-14
R
 
In [5]: #To show the number of rows and columns dataset.shape
Out[5]:	(8807, 12)
In [6]: #To show the total elements in the dataset dataset.size
Out[6]:	105684
In [7]: #To shoe each column name dataset.columns
Index(['show_id', 'type', 'title', 'director', 'cast', 'country', 'date_added', Out[7]:
       'release_year', 'rating', 'duration', 'listed_in', 'description'],       dtype='object')
In [8]: #To show the datatypes of each column dataset.dtypes
show_id         object
Out[8]:	type            object title           object director        object cast            object country         object date_added      object release_year     int64 rating          object duration        object listed_in       object description     object dtype: object
In [9]: #To show number of columns, column labels, column data types, memory usage, range i #and the number of cells in each column (non-null values) at once. dataset.info()
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 8807 entries, 0 to 8806 Data columns (total 12 columns):
 #   Column        Non-Null Count  Dtype ---  ------        --------------  ----- 
0	show_id       8807 non-null   object
1	type          8807 non-null   object
2	title         8807 non-null   object
3	director      6173 non-null   object 4   cast          7982 non-null   object
5	country       7976 non-null   object
6	date_added    8797 non-null   object
7	release_year  8807 non-null   int64  8   rating        8803 non-null   object
9	duration      8804 non-null   object
10	listed_in     8807 non-null   object 11  description   8807 non-null   object dtypes: int64(1), object(11) memory usage: 825.8+ KB
To determine whether any values are duplicates. If so, those duplicate values will be eliminated.
In [10]: #To display duplicate rows dataset[dataset.duplicated()]
Out[10]:	show_id	type	title	director	cast	country	date_added	release_year	rating	duration	listed_i
 
#To drop duplicates we will be using below function.However we dont have any duplic dataset.drop_duplicates()
In [11]:
Out[11]:	show_id	type	title	director	cast	country	date_added	release_year	rating
 
Dick
	Kirsten	United	September
	0	s1	Movie	Johnson Is	NaN	2020	PG-13
	Johnson	States	25, 2021
Dead
1	s2	TV
Show	Blood &
Water	NaN	Ama
Qamata,
Khosi
Ngema,
Gail
Mabalane, Thaban...	South
Africa	September
24, 2021	2021	TV-
MA
2	s3	TV
Show	Ganglands	Julien
Leclercq	Sami
Bouajila,
Tracy
Gotoas,
Samuel
Jouy, Nabi...	NaN	September
24, 2021	2021	TV-
MA
3	s4	TV
Show	Jailbirds
New
Orleans	NaN	NaN	NaN	September
24, 2021	2021	TV-
MA
4	s5	TV
Show	Kota
Factory	NaN	Mayur
More,
Jitendra
Kumar,
Ranjan
Raj, Alam
K...	India	September
24, 2021	2021	TV-
MA
...	...	...	...	...	...	...	...	...	..
8802	s8803	Movie	Zodiac	David
Fincher	Mark
Ruffalo,
Jake
Gyllenhaal,
Robert
Downey
J...	United
States	November
20, 2019	2007	
8803	s8804	TV
Show	Zombie
Dumb	NaN	NaN	NaN	July 1, 2019	2018	TV-Y7
8804	s8805	Movie	Zombieland	Ruben
Fleischer	Jesse
Eisenberg,
Woody
Harrelson,
Emma
Stone, ...	United
States	November
1, 2019	2009	
8805	s8806	Movie	Zoom	Peter
Hewitt	Tim Allen,
Courteney
Cox, Chevy	United
States	January 11,
2020	2006	PG
R
R
	show_id	type	title	director	cast	country	date_added	release_year	rating
					Chase, Kate Ma...				
8806	s8807	Movie	Zubaan	Mozez
Singh	Vicky
Kaushal,
Sarah-
Jane Dias,
Raaghav Chanan...	India	March 2,
2019	2015	TV-14
	8807	12	l
#We will set inplace to True to permanently eliminate the duplicate rows.
dataset.drop_duplicates(inplace=True)
	
#We can determine whether or not the changes replicated in the dataset.
dataset.shape	
(8807, 12)
Finding any null values in the dataset.					
#To check null values dataset.isnull()					
	show_id	type	title	director	cast	country	date_added	release_year	rating	duration
In [12]:
In [13]:
Out[13]:
In [14]:
Out[14]:l
	0	False	False	False	False	True	False	False	False	False	False
1	False	False	False	True	False	False	False	False	False	False
2	False	False	False	False	False	True	False	False	False	False
3	False	False	False	True	True	True	False	False	False	False
4	False	False	False	True	False	False	False	False	False	False
...	...	...	...	...	...	...	...	...	...	...
8802	False	False	False	False	False	False	False	False	False	False
8803	False	False	False	True	True	True	False	False	False	False
8804	False	False	False	False	False	False	False	False	False	False
8805	False	False	False	False	False	False	False	False	False	False
8806	False	False	False	False	False	False	False	False	False	False
8807 rows × 12 columns
 
#To check null values count by each column dataset.isnull().sum()
In [15]:
show_id            0
Out[15]:	type               0 title              0 director        2634 cast             825 country          831 date_added        10 release_year       0 rating             4 duration           3 listed_in          0 description        0 dtype: int64
#import seaborn library to visulize the data import seaborn as sns import matplotlib.pyplot as plt		
		
#Using heat map we will show the null values sns.heatmap(dataset.isnull())		
<AxesSubplot:>
 
How to locate all the information based on a specific element.		
#To find out the details of title "FullMetal Alchemist". dataset[dataset['title'].isin(['FullMetal Alchemist'])]		
	show_id	type	title	director	cast	country	date_added	release_year	rating	d
In [16]:
In [17]:
Out[17]:
In [18]:
Out[18]:
Ryosuke
Yamada,
Tsubasa
	FullMetal	Fumihiko	February 19,
	5033	s5034	Movie	Honda,	Japan	2017	TV-PG	1
	Alchemist	Sori	2018
Dean
Fujioka, M...
 
#We can also find the relavent information of an element by using str.contains func dataset[dataset['title'].str.contains('FullMetal Alchemist')]
In [19]:
Out[19]:	show_id	type	title	director	cast	country	date_added	release_year	rating	d
 
Ryosuke
Yamada,
Tsubasa
	FullMetal	Fumihiko	February 19,
	5033	s5034	Movie	Honda,	Japan	2017	TV-PG	1
	Alchemist	Sori	2018
Dean
Fujioka, M...
 
Year wise analysis
In [20]: #Will check whether the movie release date is mentioned in date format or not dataset.dtypes
Out[20]:	show_id         object type            object title           object director        object cast            object country         object date_added      object release_year     int64 rating          object duration        object listed_in       object description     object dtype: object
In [21]: #Will change the release_year data type to datetime by creating new column. dataset['New_Release_Date']=pd.to_datetime(dataset['release_year'],format='%Y')
In [22]: #We can verify the data type of new column. dataset.dtypes
show_id                     object
Out[22]: type                        object title                       object director                    object cast                        object country                     object date_added                  object release_year                 int64 rating                      object duration                    object listed_in                   object description                 object New_Release_Date    datetime64[ns] dtype: object
In [23]: #Will calculate the year wise movie count
dataset['New_Release_Date'].dt.year.value_counts()
2018    1147 Out[23]:
2017    1032 2019    1030
2020     953
2016     902         ... 1959       1
1925       1
1961       1
1947       1
1966       1
Name: New_Release_Date, Length: 74, dtype: int64
In [24]: #Will create a new column to get the year alone. dataset['New_Release_Year']=dataset['New_Release_Date'].dt.year
In [25]: plt.figure(figsize=(12,10)) sns.countplot(y="New_Release_Year", data=dataset[(dataset['type']=='Movie')], palet plt.xlabel("Movie Count")
Text(0.5, 0, 'Movie Count') Out[25]:
 
In 2018 highest number of Movies were released .
plt.figure(figsize=(12,10))
sns.countplot(y="New_Release_Year", data=dataset[(dataset['type']=='TV Show')], plt.xlabel("TV Show Count")
In [26]: pal
Text(0.5, 0, 'TV Show Count') Out[26]:
 
In 2020 highest number of TV Shows were released .
Analysis of Movies vs TV Shows.
In [27]: #Analysis of Movies vs TV Shows. dataset.groupby('type').type.count()
Out[27]:	type
Movie      6131
TV Show    2676
Name: type, dtype: int64
In [28]: #sns countplot sns.countplot(dataset['type'])
C:\Users\Satya\anaconda3\lib\site-packages\seaborn\_decorators.py:36: FutureWarnin g: Pass the following variable as a keyword arg: x. From version 0.12, the only va lid positional argument will be `data`, and passing other arguments without an exp licit keyword will result in an error or misinterpretation.
  warnings.warn(
<AxesSubplot:xlabel='type', ylabel='count'> Out[28]:
 
According to the data, Netflix has released more movies than TV series.
dataset.head()							
	show_id	type	title	director	cast	country	date_added	release_year	rating	dur
In [29]:
Out[29]:
Dick
	Kirsten	United	September
	0	s1	Movie	Johnson Is	NaN	2020	PG-13	9
	Johnson	States	25, 2021
Dead
1	s2	TV
Show	Blood &
Water	NaN	Ama
Qamata,
Khosi
Ngema,
Gail
Mabalane, Thaban...	South
Africa	September
24, 2021	2021	TV-
MA	Se
2	s3	TV
Show	Ganglands	Julien
Leclercq	Sami
Bouajila,
Tracy
Gotoas,
Samuel
Jouy, Nabi...	NaN	September
24, 2021	2021	TV-
MA	1 S
3	s4	TV
Show	Jailbirds
New
Orleans	NaN	NaN	NaN	September
24, 2021	2021	TV-
MA	1 S
4	s5	TV
Show	Kota
Factory	NaN	Mayur
More,
Jitendra
Kumar,
Ranjan
Raj, Alam
K...	India	September
24, 2021	2021	TV-
MA	Se
 
Top 10 directors
In [30]: #Filtering top 10 values by using value counts and head. dataset['director'].value_counts().head(10)
Out[30]:	Rajiv Chilaka             19
Raúl Campos, Jan Suter    18
Marcus Raboy              16 Suhas Kadav               16
Jay Karas                 14
Cathy Garcia-Molina       13
Martin Scorsese           12 Youssef Chahine           12
Jay Chapman               12
Steven Spielberg          11
Name: director, dtype: int64
In [31]:
#Creating top 10 directors list by assigning the filtered data to a data frame. count_of_movies_Tvshows=dataset['director'].value_counts().sort_values(ascending= count_of_movies_Tvshows=pd.DataFrame(count_of_movies_Tvshows)
Top_directors=count_of_movies_Tvshows[0:10] Top_directors
Fa
Out[31]:	director
 
	Rajiv Chilaka	19
Raúl Campos, Jan Suter	18
Marcus Raboy	16
Suhas Kadav	16
Jay Karas	14
Cathy Garcia-Molina	13
Youssef Chahine	12
Jay Chapman	12
Martin Scorsese	12
Steven Spielberg	11
According to the data,Rajiv Chilaka has directed more movies .
Top 10 countries for content release analysis
In [32]:
#By adding the filtered data to a data frame, the top 10 countries list is created count_of_movies_Tvshows=dataset['country'].value_counts().sort_values(ascending= count_of_movies_Tvshows=pd.DataFrame(count_of_movies_Tvshows)
Top_directors=count_of_movies_Tvshows[0:10] Top_directors
Fal
Out[32]:	country
 
	United States	2818
India	972
United Kingdom	419
Japan	245
South Korea	199
Canada	181
Spain	145
France	124
Mexico	110
Egypt	106
#using plotly to create a funnel diagram of the top 10 content-releasing countries import plotly.express as px data = dict(
    number=[2818,972,419,245,199,181,145,124,110,106],
    country=["United States", "India", "United Kingdom", "Japan",'South Korea',"Can fig = px.funnel(data, x='number', y='country') fig.show()
In [33]:
 
h
Movie ratings analysis¶
In [34]: #cheking the values of ratings. dataset['rating'].value_counts().sort_values(ascending=False)
Out[34]:	TV-MA       3207
TV-14       2160
TV-PG        863 R            799
PG-13        490
TV-Y7        334
TV-Y         307 PG           287
TV-G         220
NR            80
G             41 TV-Y7-FV       6
NC-17          3
UR             3
74 min         1 84 min         1
66 min         1
Name: rating, dtype: int64
#we will replace three values which are mentioned in minutes to NA. As its only thr
dataset['rating'] = dataset['rating'].replace(['74 min'], 'NA') dataset['rating'] = dataset['rating'].replace(['84 min'], 'NA') dataset['rating'] = dataset['rating'].replace(['66 min'], 'NA')
In [35]:
In [36]: #cross checking whether those minutes are replaced with NA or not. dataset['rating'].value_counts().sort_values(ascending=False)
Out[36]:	TV-MA       3207
TV-14       2160
TV-PG        863 R            799
PG-13        490
TV-Y7        334
TV-Y         307 PG           287
TV-G         220
NR            80
G             41 TV-Y7-FV       6
NC-17          3
NA             3
UR             3
Name: rating, dtype: int64
In [37]: plt.figure(figsize=(12,10)) sns.set(style="darkgrid") ax = sns.countplot(x="rating", data=dataset, palette="husl", order=dataset['rating
 
Movies with a "TV-MA" rating account for the majority of productions.."TV-MA is a rating that is given to television programs to indicate that it’s for “Mature Audiences”. This means that the show may contain graphic violence (V), strong sexual activity (S), and/or crude language (L). Due to the type of content in these shows, they are not suitable for children under the age of 17."
Second largest are "TV-14"."The TV-14 rating means that the show is unsuitable for children under the age of 14. Programming with this rating will often have content that contains highly suggestive dialogue (D), strong coarse language (L), intense situations of a sexual nature (S), or intense violence (V)."
