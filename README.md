<!DOCTYPE html>
<html>
<head>
    <title>Andrew Phone Solutions</title>
</head>
<body>
    <h1>Welcome to Andrew Phone Solutions</h1>
    <p>Address:  Court Rd, 965-40100 , Kisumu, Kenya</p>
    <p>Phone: +254 715 847 894</p>
    <p>Email: info@mundiaandrew001@gmail.com</p>

    <!-- Map to display the location -->
    <div id="map"></div>

    <!-- Load the Google Maps JavaScript API -->
    <script src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&callback=initMap" async defer></script>

    <script>
        // Initialize the map
        function initMap() {
            var location = {lat:-0.10496327950014803, lng: 34.7542885425657}; 
            var map = new google.maps.Map(document.getElementById('map'), {
                zoom: 15,
                center: location
            });

            var marker = new google.maps.Marker({
                position: location,
                map: map,
                title: 'Andrew Phone Solutions'
            });
        }
    </script>
</body>
</html>

