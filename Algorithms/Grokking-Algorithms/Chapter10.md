- [K-nearest Neighbor](#k-nearest-neighbor)
    - [Clasification](#clasification)
    - [Regresion](#regresion)
    - [Cosine Similarity](#cosine-similarity)
    - [Picking good features](#picking-good-features)
- [Excercise Answers](#excercise-answers)

## K-nearest Neighbor
- Used for clasification and regresion problems, you look at known datapoints which are closely related to your current datapoint and then you decide which classification to give it
- In order to clasify the objects, you need to do **feature extraction**
    - feature extraction is getting adjectives that describe the objects, like size, redness, etc
- You then convert the data points into coordinates of a graph
- You use Pythagorean formula to find the distance between to coordinates and know how similar or difference they are
$$\sqrt{(x_1 - x_2)^2 + (y_1 - y_2)^2}$$
- It is k-nearest neighbor because you can decide the number of nearest neighbors you want to search for = k.

### Clasification
- Once you get the nearest neighbor you clasify your new datapoint to the same clasification the nearest neighbor has

### Regresion
- Here what you'll do is get the some of the nearest neighbors results and then take an average to predict the result of you current input
    - Ex: You have a bakery and want to predict how many loaves of bread you should make today. For this you have 3 features: weather on a scale from 1 to 5, if it is weekend or holiday or a normal day, 1 and 0, and if there's a sports game, again 1 and 5. So you score the current day and then compare it with past days, getting the nearest neighbors to you current day. Each of the past days has how many loaves of breath you sold. So you take the average of the this days to predict how many bread you should sell today.

### Cosine Similarity
- Is another way to measure how clsoe are two datapoints related, but it is used to measure the angle between the two vectors, instead of the distance, so the values of the rating don't affect that much. 
    - Ex: If someone rates movies only with 1 or 5 and other is more careful and uses all numbers, then their distance could be really far, but the angle won't vary that much.

### Picking good features
- Pick features that:
    - directly correlate to whaat you are trying to recomend
    - don't have a bias


## Excercise Answers
- **10.1 In the Netflix example, you calculated the distance between two different users using the distance formula. But not all users rate movies the same way. Suppose you have two users, Yogi and Pinky, who have the same taste in movies. But Yogi rates any movie he likes as a 5, whereas Pinky is choosier and reserves the 5s for
only the best. They’re well matched, but according to the distance algorithm, they aren’t neighbors. How would you take their different rating strategies into account?**

Mine: Do a normalization method

Real: You could use something called normalization. You look at the average rating for each person and use it to scale their ratings. For example, you might notice that Pinky’s average rating is 3, whereas Yogi’s average rating is 3.5. So you bump up Pinky’s ratings a little, until her average rating is 3.5 as well. Then you can compare their ratings on the same scale.

- **10.2 SupposeNetflixnominatesagroupof“influencers.”Forexample, Quentin Tarantino and Wes Anderson are influencers on Netflix, so their ratings count for more than a normal user’s. How would you change the recommendations system so it’s biased toward the ratings of influencers?**

Mine: I would add an importance feature to the user or a factor of importance for which you would multiply the ratigns of the influencers so they affect more on the average

Real: You could give more weight to the ratings of the influencers when using KNN. Suppose you have three neighbors: Joe, Dave, and Wes Anderson (an influencer). They rated Caddyshack a 3, a 4, and a 5, respectively. Instead of just taking the average of their ratings (3 + 4 + 5 / 3 = 4 stars), you could give Wes Anderson’s rating more weight: 3 + 4 + 5 + 5 + 5 / 5 = 4.4 stars.

- **10.3 Netflixhasmillionsofusers.Theearlierexamplelookedatthefive closest neighbors for building the recommendations system. Is this too low? Too high?**
It’s too low. If you look at fewer neighbors, there’s a bigger chance that the results will be skewed. A good rule of thumb is, if you have N users, you should look at sqrt(N) neighbors.