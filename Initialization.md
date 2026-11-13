# Understanding general phone app market trends; target: android/google play store market. 

Analyse and visualize general trends leading to app sucess across the google play store 

Use generative AI to accelerate work; use good prompt engineering.

## Data understanding 
Factors showing success are ratings/reviews and installs 
Factors that may affec that sucess are size, type(paid or free), Niche(content rating), Genres, Android version 

# Business questions 
## Main Objective 
What factors are associated with app sucess on Google Play store?

### Questions
#### Price 
1. Are free apps more successful than paid apps (IS THERE A RLSHP BETWEEN PRICE AND INSTALLS)

#### Technical
1. Does the size of an app affect it's installtion
2. Does the rewuired android verion affSect the installation (what is the sweet spot for the android version)

#### User reviews and ratings 
1. Does having more reviews equate to having a higher rating (IS THERE A RLSHP BETWENE REVIEWS AND RATINGS)

#### Categories
1. Which categories have the highest ratings (NICHE)
2. How does content rating relate to ratings and popularity-- number of installs (NICHE)
3. Genres combining both high ratings and popularity--number of installs

### Question 1: App characteristics (price, size, Android version) associated with installs

Data requirements:

Installs (target variable — will need cleaning: remove "+" and commas, convert to numeric)
Price (clean "$" signs, convert to numeric)
Type (Free/Paid)
Size (clean "Varies with device," "M"/"k" suffixes, standardize to MB)
Android Ver (standardize inconsistent formats, e.g., "4.0.3 and up")

Analytical approaches:

Compare install distributions for Free vs. Paid apps (boxplot, median/mean comparison)
Bin Price into ranges (Free, $0.01–$1.99, $2–$4.99, etc.) and compare install trends across bins
Scatterplot or binned analysis of Size vs. Installs to check for a relationship
Group by minimum required Android Ver and compare average/median installs
Consider a correlation matrix or simple grouped bar charts to summarize all three factors together

Complexity: Medium. Requires the heaviest data cleaning (Installs, Size, and Android Ver are all messy text fields), but the analysis itself (grouping, comparing distributions) is straightforward.

### Question 2: Reviews vs. ratings relationship

Data requirements:

Reviews (convert to numeric)
Rating (already numeric, but check for nulls/outliers)

Analytical approaches:

Scatterplot of Reviews vs. Rating (consider log-transforming Reviews, since it's typically right-skewed)
Correlation coefficient (e.g., Pearson or Spearman) to quantify strength of relationship
Bin apps into review-volume tiers (e.g., low/medium/high engagement) and compare average ratings per tier

Complexity: Low. Minimal cleaning needed, and it's a two-variable relationship — one of the more direct analyses.

### Question 3: Installs and ratings across categories/genres

Data requirements:

Category and/or Genres (decide whether to use one or both — Genres is more granular and may need consolidation since some apps have multiple genres)
Installs
Rating

Analytical approaches:

Group by Category: compare average/median installs and ratings per category (bar charts, sorted)
Identify categories with high installs but lower ratings (potential saturation or quality gaps) vs. categories with high ratings but low installs (potential underserved opportunity)
Consider a scatterplot of average installs vs. average ratings per category to visually spot these patterns

Complexity: Medium. Category cleaning is manageable, but Genres may require splitting multi-value fields, and the "opportunity mapping" analysis (installs vs. ratings together) takes more interpretive work.

### Question 4: Content rating vs. installs and ratings

Data requirements:

Content Rating (check category counts — some values like "Adults only 18+" may have very few apps)
Installs
Rating

Analytical approaches:

Group by Content Rating: compare average/median installs and ratings
Bar charts for both metrics side by side across content rating categories
Flag categories with very small sample sizes so they're not over-interpreted

Complexity: Low–Medium. Straightforward grouping, but small sample sizes in some content-rating groups may limit how much can be confidently concluded.

### Prioritization (by business impact vs. complexity)
Priority	Question	Business Impact	Complexity	Rationale

1	Q3 – Category/genre	High	Medium	Directly answers "which market to enter" — likely the most decision-critical question for a company choosing what app to build
2	Q1 – Price/size/Android version	High	Medium	Once a category is chosen, this shapes how to build the app — pricing model, size, compatibility
3	Q4 – Content rating	Medium	Low–Medium	Useful for audience targeting, but a secondary decision relative to category and product design
4	Q2 – Reviews vs. ratings	Medium	Low	Interesting and easy to analyze, but more of a supporting insight (engagement/quality signal) than a standalone "what to build" decision