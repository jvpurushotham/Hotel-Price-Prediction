# displaying the location of the hotels in the map
fig = px.scatter_mapbox(df, lat = 'latitude', lon = 'longitude', zoom = 8, height = 1000, width = 1000)
fig.update_layout(mapbox_style="open-street-map")
fig.update_layout(
    margin={"r": 0, "t": 0, "l": 0, "b": 0}
)
fig.show()
