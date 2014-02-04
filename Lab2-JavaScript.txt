var directionDisplay;
var directionsService = new google.maps.DirectionsService();    
var map2;
var Source;
var dest;

function initialize()
{
    var Source = document.getElementById("i1").value;
    var dest = document.getElementById("i2").value;
    if(Source==""&& Destination=="")
    {
        
    }
else
{
    document.getElementById("map_view").hidden = false;
    directionsDisplay = new google.maps.DirectionsRenderer();        
    var center = new google.maps.LatLng(0, 0);     
    var myOptions =
    {
            zoom:7,
            mapTypeId: google.maps.MapTypeId.ROADMAP,
            center: center
    }
    map2 = new google.maps.Map(document.getElementById("map_view"), myOptions);
    directionsDisplay.setMap(map2);

    var request =
    {
            origin:Source,
            destination:dest,
            travelMode: google.maps.DirectionsTravelMode.DRIVING         
    };
    directionsService.route(request, function(response, status)
    {
            if (status == google.maps.DirectionsStatus.OK) 
            {
            directionsDisplay.setDirections(response);         
            }
    });
}
}

var button = document.getElementById('button');

var onClick = function() { 
    initialize();
};

button.addEventListener('click', onClick, false);

var clbutton = document.getElementById('clbutton');

var onClClick=function(){
    document.getElementById("map_view").hidden = true;
    document.getElementById("i1").value="";
    document.getElementById("i2").value="";
   
};

clbutton.addEventListener('click', onClClick, false);


