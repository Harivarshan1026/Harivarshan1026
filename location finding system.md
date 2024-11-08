!pip install geopy folium
# Import libraries
import folium
from geopy.geocoders import Nominatim
from geopy.distance import geodesic

# Initialize geolocator
geolocator = Nominatim(user_agent="location_tracking_system")

# Function to get location data
def get_location(address):
    location = geolocator.geocode(address)
    return (location.latitude, location.longitude) if location else None

# Function to calculate distance between two locations
def calculate_distance(loc1, loc2):
    return geodesic(loc1, loc2).kilometers

# List to store location data
location_data = []

# Adding some sample locations
addresses = ["New York, USA", "Los Angeles, USA", "Chicago, USA"]
for address in addresses:
    loc = get_location(address)
    if loc:
        location_data.append({"address": address, "coordinates": loc})


# Import libraries
import folium
from geopy.geocoders import Nominatim
from geopy.distance import geodesic

# Initialize geolocator
geolocator = Nominatim(user_agent="location_tracking_system")

# Function to get location data
def get_location(address):
    location = geolocator.geocode(address)
    return (location.latitude, location.longitude) if location else None

# Function to calculate distance between two locations
def calculate_distance(loc1, loc2):
    return geodesic(loc1, loc2).kilometers

# List to store location data
location_data = []

# Adding some sample locations
addresses = ["New York, USA", "Los Angeles, USA", "Chicago, USA"]
for address in addresses:
    loc = get_location(address)
    if loc:
        location_data.append({"address": address, "coordinates": loc})


# List to store location data
location_data = []

# Adding some sample locations
addresses = ["New York, USA", "Los Angeles, USA", "Chicago, USA"]
for address in addresses:
    loc = get_location(address)
    if loc:
        location_data.append({"address": address, "coordinates": loc})

# Print the collected location data to verify
location_data


# Create a map centered around the first location
map_center = location_data[0]["coordinates"]
mymap = folium.Map(location=map_center, zoom_start=5)

# Add markers for each location
for loc in location_data:
    folium.Marker(location=loc["coordinates"], popup=loc["address"]).add_to(mymap)

# Save the map to an HTML file
mymap.save("location_tracking_map.html")

print("Map has been created and saved as 'location_tracking_map.html'")


mymap
