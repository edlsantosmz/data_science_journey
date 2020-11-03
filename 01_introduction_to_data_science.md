# Introduction

Data science enables us to take data and transform it into meaningful information that can help us make decisions. Data science is interdisciplinary and combines other well-known fields such as probability, statistics, analytics, and computer science.

# Statistics

Statistics is the practice of applying mathematical calculations to sets of data to derive meaning. Statistics can give us a quick summary of a dataset, such as the average amount or how consistent a dataset is

There are two types of statistics: descriptive statistics and inferential statistics. Descriptive statistics describe a dataset using mathematically calculated values, such as the mean and standard deviation. For instance, the graph below from FiveThirtyEight charts the wage gap between American men and women in 2014. An example of a descriptive statistic would be that at the 90th income percentile, women make 80.6% of what men make on average.
On the other hand, inferential statistics are statistical calculations that enable us to draw conclusions about the larger population. For instance, from looking at the graph we can infer that at the 99th income percentile, women make less than 78% of what men make on average. We can also infer that the reason why the wage gap is smallest at the 10th income percentile is because the minimum wage for men and women is the same.

# Probability

Probability is the mathematical study of what could potentially happen.
In data science, probability calculations are used to build models. Models are able to help us understand data that has yet to exist - either data we hadn’t previously collected or data that has yet to be created. Data scientists create models to help calculate the probability of a certain action and then they use that probability to make informed decisions.

```
import random


num_people_in_room = 40 			#Change This Number

#Simulate a room with a certain number of people
def simulate(num_people):
  birthdays = []
  print("Here's what our room looks like:\n")
  months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"]
	#Assign a random birthday to each person
  for i in range(0, num_people):
    #Choose a random month
    month_choice = random.choice(months)
    #Choose a random day based on month
    if month_choice == "February":
      day = random.randint(1, 29)
    elif month_choice == "April" or month_choice == "June" or month_choice == "September" or month_choice == "November":
      day = random.randint(1, 30)
    else:
      day = random.randint(1, 31)
    birthday = month_choice + " " + str(day)
    #Store the birthday
    birthdays.append(birthday)
    print("Person {0}'s birthday: {1}".format(i + 1, birthday))
  calculate_probability(num_people)
  match = False
  #Check for matching birthdays
  for i in range(len(birthdays)):
    if find_duplicates(birthdays, birthdays[i], i):
      match = True
      break
  if not match:
    print("\n\nIn our simulation, no two people have the same birthday")

#Calculate the probability of there being 2 people with the same birthday
def calculate_probability(num_people):
  #Check there is at least 2 people in the room
  if num_people < 2:
    print("\n\nNot enough people in the room!")
    return
  else:
    #Calculate the probability
    numerator = 365
    countdown = 364
    for i in range(2, num_people + 1):
      numerator = numerator * countdown
      countdown -= 1
    denominator = 365 ** num_people
    probability = 1 - numerator/float(denominator)
    #Change probability to percentage
    rounded = round(probability*100, 2)
    print("\n\nThe probability that two people in a room of {0} people have the same birthday is nearly {1}%".format(num_people, rounded))

    
#Find the same birthday within our list of birthdays
def find_duplicates(birthdays_list, birthday, index):
  people = []
  for i in range(len(birthdays_list)):
    if birthdays_list[i] == birthday and i != index:
      people.append(i + 1)
  if people:
    people.append(index + 1)
    print("\n\nIn our simulation, the following people have the same birthdays: ")
    for person in people:
      print("Person {0}".format(person))
    return True
  else:
    return False

simulate(num_people_in_room)
  
```

```
Here's what our room looks like:

Person 1's birthday: June 9
Person 2's birthday: June 21
Person 3's birthday: May 4
Person 4's birthday: December 2
Person 5's birthday: April 14


The probability that two people in a room of 5 people have the same birthday is nearly 2.71%


In our simulation, no two people have the same birthday
```

Probability is used for many applications in different fields and companies around the world.

One of the most common applications of data science is for advertisements. By using probability, companies determine what kinds of ads are most relevant for a user. For example, YouTube and Facebook ads.

Similarly, probability is also used for e-commerce companies like Amazon, to determine what items to present a user based on their purchase history.

The video-streaming site Netflix uses probability to match titles that you might watch, and will also change the artwork for shows to receive more clicks.

Probability is also fundamental to areas such as machine learning which is applied in applications such as Google Deepmind, AlphaGo, and self-driving cars.

