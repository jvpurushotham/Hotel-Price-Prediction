import streamlit as st
st.title("New York City Hotels Data Analysis")
st.write("This is my Data Analysis on Hotels of New York City")

import pandas as pd
df = pd.read_csv("/Users/jvpurushotham/Hotels_data.csv")
with st.expander("Dataframe Preview"):
    st.dataframe(df)

st.write("Shape of the data: ")
st.write(df.shape)

st.write("Info of the data")
if st.button('Show DataFrame Info'):
    from io import StringIO
    buffer = StringIO()
    df.info(buf=buffer)
    s = buffer.getvalue()
    st.text(s)

st.write("Describing the data for overall understanding: ")
button1 = st.button("Click here to view description about the data")
if button1:
    st.write(df.describe())

import plotly.express as px
st.write("scatter plot showing that when price is low then no of reviews are more")
st.write("### Price vs Number of Reviews")
scatter_plot = px.scatter(
    df,
    x="number_of_reviews",
    y="price",
    trendline="ols",
    title="Price vs Number of Reviews"
)
st.write(scatter_plot)

import matplotlib.pyplot as plt
st.write("Plotting histogram to check the price distribution")
plt.figure(figsize = (12, 8))
plt.xscale('log')
plt.yscale('log')
st.write("### Price Distribution (Log Scale)")

plt.figure(figsize=(12, 8))
plt.xscale('log')
plt.yscale('log')
df.price.hist(bins=100, color="blue", edgecolor="black", linewidth=1.5)

plt.title("Price Distribution (Log Scale)", fontsize=16)
plt.xlabel("Price (log scale)", fontsize=14)
plt.ylabel("Frequency (log scale)", fontsize=14)
st.pyplot(plt)
st.write("""### Insights from the Log-Log Histogram of Price Distribution

1. **Price Range and Distribution**: The log scale effectively captures a wide range of prices, highlighting trends across both high and low price points.  
2. **Presence of Outliers**: A long right-hand "tail" indicates exceptionally high prices, suggesting the presence of outliers.  
3. **Distribution Shape**: A peak on the left suggests a predominance of low-priced items, typical in consumer goods.  
4. **Data Spread**: The bin width reflects price variation; wider bins indicate diverse price ranges, while narrower bins suggest clustering within specific ranges.  
""")

st.write("### Consecutive histograms for understanding the each column's distribution more clearly")
st.write(df.hist(color = "green", edgecolor = "red", linewidth = 1.2, figsize = (30, 30)))
st.pyplot(plt)

st.write("""This set of histograms provides a quick overview of each column's distribution,
highlighting where values cluster and indicating any skewness or outliers in the data.
It helps identify patterns across variables, such as concentration ranges and variability within each feature.""")


import seaborn as sns
st.write("## Countplots")
col1, col2 = st.columns(2)
with col1:
    st.write("### Countplot for License Column")
    fig1, ax1 = plt.subplots()
    sns.countplot(df, x="license", ax=ax1)
    ax1.set_xlabel('License')
    ax1.set_ylabel('Number of Hotels')
    ax1.set_title('Hotels with License')
    st.pyplot(fig1)

with col2:
    st.write("### Countplot for Neighbourhood Group")
    fig2, ax2 = plt.subplots()
    sns.countplot(data=df, x='neighbourhood_group', palette='rocket', ax=ax2)
    ax2.set_title('Neighbourhood Group')

    # Adding labels above the bars
    for p in ax2.patches:
        ax2.annotate(
            int(p.get_height()),
            (p.get_x() + p.get_width() / 2, p.get_height() + 5),
            ha='center'
        )
    st.pyplot(fig2)

st.write("""From the above graph-1, we can find that the hotels which doesn't have license are more.
The count of the hotels which have licese are 3189 and which doesn't have license are 17569. 
The countplot reveals the distribution of listings across different neighborhood groups,
showing which areas have higher or lower concentrations of listings.
The annotated counts on top of each bar provide precise values, 
making it easy to compare neighborhood popularity directly.""")

st.write("## Countplots for Room Types")

col1, col2 = st.columns(2)

with col1:
    st.write("### Countplot for Room Type")
    fig3, ax3 = plt.subplots()
    sns.countplot(data=df, x='room_type', palette="magma", ax=ax3)
    ax3.set_title('Restaurants with Different Room Types')

    for p in ax3.patches:
        ax3.annotate(
            int(p.get_height()),
            (p.get_x() + p.get_width() / 2, p.get_height() + 5),
            ha='center'
        )
    st.pyplot(fig3)

with col2:
    st.write("### Countplot for Room Type")
    df_rating = df[df['rating'] == 5.0]
    fig4, ax4 = plt.subplots()
    sns.countplot(data=df_rating, x='room_type', palette="magma", ax=ax4)
    ax4.set_title('Restaurants with Different Room Types (Rating = 5.0)')

    for p in ax4.patches:
        ax4.annotate(
            int(p.get_height()),
            (p.get_x() + p.get_width() / 2, p.get_height() + 5),
            ha='center'
        )
    st.pyplot(fig4)


st.write("""This countplot-1 highlights the distribution of listings across different room types,
showing which type (e.g., entire home/apt, private room, hotel room, shared room) is most common.
The labeled counts on each bar make it easy to compare the popularity of each room type directly.
From this we can say that "Entire home/apt" is mostly popular among all of them from the above graph.
The countplot-2 shows the distribution of room types in the dataset,
revealing how different room types are represented across the data.
It helps identify the most and least common room types,
such as entire homes versus private rooms, in terms of frequency.
We observe the same as normal data while plotting data with 5 rating
"Entire home/apt" is again the popular room_type in 5 rating data also.""")

st.write("Plotting line chart between last_review and price")
if st.button("Click here to show line chart"):
    if not pd.api.types.is_datetime64_any_dtype(df['last_review']):
        df['last_review'] = pd.to_datetime(df['last_review'])

    plt.figure(figsize=(20, 8))
    sns.lineplot(data=df, x="last_review", y="price")
    st.pyplot(plt)
    st.write("""The line chart visualizes the relationship between last_review dates and price.
    It highlights how prices fluctuate over time, potentially revealing trends, seasonal effects, or changes in demand.
    Any sharp peaks or drops in the chart might indicate specific events or outliers affecting pricing.
    """)

st.write("### Plotting Scatter Chart Between Room Type, Bedrooms, and Price")
fig = px.scatter(
    df,
    x="bedrooms",
    y="price",
    color="room_type",
    animation_frame="room_type",
    title="Scatter Plot: Room Type, Bedrooms, and Price"
)
st.plotly_chart(fig)

st.write("""This scatter plot illustrates how price varies with the number of bedrooms across different room types,
revealing trends such as higher prices for listings with more bedrooms.
The animation by room type allows for easy comparison,
showing how price distribution differs between entire homes, private rooms, and other room types.""")

st.write("### Plotting Line Chart Between Bedrooms and Price")
plt.figure(figsize=(20, 8))
sns.lineplot(data=df, x="bedrooms", y="price")

plt.title("Line Plot Showing Relation Between Bedrooms and Price", fontsize=16)
plt.xlabel("Number of Bedrooms", fontsize=14)
plt.ylabel("Price", fontsize=14)
st.pyplot(plt)

st.write("""This line plot shows the relationship between the number of bedrooms and price,
indicating that as the number of bedrooms increases, the price generally trends upwards.
The plot may reveal pricing patterns and anomalies for properties with certain bedroom counts.""")

st.write("### Plotting Boxplot Between Availability 365 and Neighbourhood Group")
plt.figure(figsize=(10, 7))
sns.boxplot(data=df, x='neighbourhood_group', y='availability_365', palette='Paired')
plt.title("Distribution of Availability Across Neighborhood Groups", fontsize=14, fontweight='bold')
st.pyplot(plt)

st.write("""The boxplot illustrates the distribution of availability across different neighborhood groups,
showing variability in the number of days listings are available throughout the year.
It highlights potential outliers and differences in availability between neighborhoods,
with some groups having more consistent availability than others.""")

st.write("### Plotting Histogram for Price Distribution with Count")
df_rating = df[df['rating'] == 5.0]
plt.figure(figsize=(10, 5))
sns.histplot(data=df_rating, x='price', kde=True)
plt.title("Price Distribution Plot", size=15, weight='bold')
st.pyplot(plt)

st.write("""The histogram shows the distribution of prices with a kernel density estimate (KDE),
providing insights into the overall price range and its skewness.
It reveals whether the prices are normally distributed
or if there are more frequent low-priced listings compared to higher-priced ones.""")

st.write("### Plotting the Bar Graph to Find the Most Popular Neighbourhood")
data = df['neighbourhood'].value_counts()[:10]
x = list(data.index)
y = list(data.values)
x.reverse()
y.reverse()
fig = px.bar(
    x=y,
    y=x,
    orientation='h',
    title="Most Popular Neighbourhood",
    labels={'x': 'Number of Guests Who Host in this Area', 'y': 'Neighbourhood Area'},
    color=y,
    color_continuous_scale="Viridis"
)
fig.update_layout(
    xaxis_title="Number of Guests Who Host in this Area",
    yaxis_title="Neighbourhood Area",
    title_font_size=18
)
st.plotly_chart(fig)


st.write("""The bar graph highlights the top 10 most popular neighborhoods
based on the number of guests who host in these areas,
with the data visualized in descending order.
It provides a clear view of neighborhood popularity,
showing which areas attract the most hosts and guests.""")

st.write("### Plotting Scatter Plot and Histogram Combined Using Plotly")
df_rating = df[df['rating'] == 5.0]
fig = px.scatter(
    df_rating,
    x="price",
    y="neighbourhood_group",
    marginal_x="histogram",
    marginal_y="rug",
    title="Scatter Plot of Price vs Neighbourhood Group with Marginals",
    labels={"price": "Price", "neighbourhood_group": "Neighbourhood Group"}
)
st.plotly_chart(fig)

st.write("""The combined scatter plot and histogram visualize the relationship between price and neighbourhood_group,
while also showing the price distribution and density.
The scatter plot highlights variations in pricing across different neighborhoods,
while the marginal histogram reveals the concentration of prices.
The rug plot further emphasizes price clustering or spread within specific neighborhoods.""")

st.write("### Scatter Plot Using Longitude, Latitude with Hue as Availability_365")
plt.figure(figsize=(10, 6))
sns.scatterplot(
    data=df,
    x='longitude',
    y='latitude',
    hue='availability_365',
    palette="coolwarm"
)
plt.title("Scatter Plot of Longitude vs Latitude with Availability as Hue", fontsize=14, weight='bold')
st.pyplot(plt)

st.write("""The scatter plot visualizes the geographical distribution of listings based on longitude and latitude,
with color indicating the availability throughout the year.
It shows how the availability of listings is spread across different locations,
highlighting areas with higher or lower availability.""")

st.write("### Plotting Line Chart Using Room Type, Rating, and Color as Room Type")
fig = px.line(
    df,
    x="room_type",
    y="rating",
    color="room_type",
    markers=True,
    title="Line Chart of Room Type vs Rating",
    labels={"room_type": "Room Type", "rating": "Rating"}
)
st.plotly_chart(fig)

st.write("""The line chart shows the variation in ratings across different room types,
highlighting how room types are rated differently by users.
It provides insights into which room types generally receive higher or lower ratings,
helping to identify trends in guest satisfaction based on the type of accommodation.""")

st.write("### Plotting Scatter Plot According to Last Review and Rating")
fig = px.scatter(
    df,
    x="last_review",
    y="rating",
    color="rating",
    title="Scatter Plot of Last Review vs Rating",
    labels={"last_review": "Last Review Date", "rating": "Rating"},
    color_continuous_scale="Viridis"
)
st.plotly_chart(fig)

st.write("""The scatter plot illustrates the relationship between the date of the last review and the ratings,
with color indicating the rating levels.
It reveals whether more recent reviews correlate with higher or lower ratings,
highlighting trends in guest feedback over time.""")

st.write("### Plotting Scatter Plot According to Last Review and Rating")
fig = px.scatter(
    df,
    x="last_review",
    y="rating",
    color="room_type",
    title="Scatter Plot of Last Review vs Rating",
    labels={"last_review": "Last Review Date", "rating": "Rating"},
    color_continuous_scale="Viridis"
)
st.plotly_chart(fig)

st.write("""The scatter plot shows the relationship between the date of the last review and the rating,
with points colored by room type.
It helps identify how different room types are rated over time,
revealing patterns in guest satisfaction and review frequency across room categories.
""")

st.write("Heatmap for the entire data")
image_path = '/Users/jvpurushotham/heatmap.png'
st.image(image_path, caption='Image', use_container_width=True)

st.write("""The heatmap visualizes the correlations between different numerical features
in the dataset using Kendall’s method, highlighting relationships between variables.
It helps identify which features are strongly or weakly correlated,
providing insights into potential dependencies and associations within the data.
From this heatmap we can notice that there is a strong between minimum_nights and license,
there is a relation between reviews_per_month and number_of_reviews_Itm,
there is a relation between beds and bedrooms, there is a relation between number_of_reviews and number_of_reviews_Itm,
""")


st.write("Do you like my work?")
like = st.checkbox("Yes")
if like:
    st.write("Thank you for your response.")
    st.write("Great to have you here!")
