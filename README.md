Day 01- 12 jan,2025
Weather app 

create index.html, style.css

give body has background that is #222.

in index.html-->create a div with class named "card" in body after that create again a div with class named "search" for this again a nested with input as type "text" and placeholder "enter city name" and spellcheck="false" then need button tag also get that button image for serach use src with img location.button tag and insite write img tag

css for all that *{} and margin & padding is 0 and font-family is 'Poppins', san-serif and box-sizing is border-box.

give css to card class that is width of 90%, max-width of 470px, background is linear-gradienty(135 deg, #00feba, #5b548a) and color is #fff and margin is 100px auto 0, border radius 20px, padding 40px 35px and text-align center.

now css for search class where width is 100%, display is flex and align-item is center and justify-content is space-between.        

ccs for search input button that is selected by .search input with border is 0, outline is 0, background is #ebfffc, color is #555, padding 10px 25px, height is 60px, border-radius is 30px, flex is 1, margin-right 16px and font size is 18px  

css for button : .serach button then with border is 0, outline is 0, background is #ebfffc, border radius 50% and width 60px height 60px cursor is pointer

ccs for .search button img : width 16px

then create new div class named "weather" in which img tag class named "weather-icon then src rain.png then need to display temperature using h1 tag class named "temp" write 22 degree c in that h1 tag. then h2 tag class named "city" write New York name in it. then again new div class named "details". 
In detail class we need two clomun so again div in it class named "col". In this col class, we adding imag tag with src humidity.png and again a div for p tag class named "humidity" and written 50% in it and again p tag Humidity written in it. Then we need to copy this whole div class named col and update image name as wind.png and class wind with written 15 km/h and again wind Speed in p tag.

css for .weather-icon where width is 170px and margin-top 30px then css for .weather h1 with font-size 80px and font-weight is 500 then same goes to .weather h2 with font-size 45px, font-weight is 400, margin0top is -10px

css for details where display is flex, align-item is center, justify-content is space-between, padding is 0 20px, margin-top 50px

css for icon block that is .col where display is flex, align-item is center, text-align is left

css for .col img where width is 40px, margin-right is 10px.

we need css for text humidity and wind for that selecting .humidity, wind where font-size is 28px, margin-top is -6px.

Now, we want API, when we eneter any city name, we need to have details.
https://home.openweathermap.org/api_keys

https://api.openweathermap.org/data/2.5/weather?q={city name}&appid={API key}
below is with city name and token key
https://api.openweathermap.org/data/2.5/weather?q=germany&appid=52b26f2701fe49d6fe78d686d7b2408c

°C is a metric unit and if we paste above url in browser it will give data in jason format where unit is by default satandard and we need it in metric 
so use ' &units=metric '

https://api.openweathermap.org/data/2.5/weather?q=germany&appid=52b26f2701fe49d6fe78d686d7b2408c&units=metric

In this tutorial he added script tag for js code, where in script tag , we have created a variable apiKey like const apiKey=""; also another variable apiUrl and paste the our URL. also, in apiUrl delete apiid and paste in apiKey also delete city
then, it looks like below
https://api.openweathermap.org/data/2.5/weather?units=metric
then again we have website then unit and need to add city name that is '&q=bangalore'.

Then we need async function and named it as checkWeather() and in that function declare a variable response that is 'const response = await fetch()'

The fetch() method starts the process of fetching a resource from a server.
The fetch() method returns a Promise that resolves to a Response object.

for this fetch, we need apiUrl and api key that it given by back tick " `` "  ,so in it like fetch(apiUrl + ``)
in that back tick we need api key, it is decalred by `&appid=${apiKey}`. Then we need data and data is getting just need to declare a variable for it that is var data is equal to await response.json()

let us ust view this data then it console.log(data)
then call the function checkWeather(), if you inspect website and view the console, you will get data in json, main--temp,humidity , name, weather- array1 - index 0 has main - cloud, wind and windspeed

we have to update city, temp, humidity and wind information according to the data coming from api. So we are importing all first city by using document.querySelector(".city").innerHTML = data.name

same get other data using data.main.temp , data.main.humidity , data.wind.speed

after this web page display our values now we need units for all. So, for temp add ' + "°C" ', for humidity add ' + "%" ' and for wind add ' + "km/h" '
Now, we need roundoff value for temp then use Math.round() and in parethisis put data.main.temp

so delete city name in URL and add parameter in checkWeather function that is 'city'. so in that function after apiUrl add ' + city + ' 

until now we are using value which is enter in default url so we need result for input city so 
when you click on search button our clickWeather fuction must me exceuted. for that import search and botton using const searchBox is equal to queryselector to ".search input" and const searchBtn is equal to query selector to ".search button". 
and we need eventListner here so, searchBtn.addEventListener("click", ()=> {}) and in this arrow function put the checkWeather() function. so in parameter we need to add value that is searchBox.value.

Now, we need to change images according to weather condtion clear,clouds,dizzle,mist,rain(already created),snow

just in our async function , write in it if statment that weather is equal == to "Clouds" then weatherIcon.src is equal to source file clouds, also import that weather-icon img tag in it and name as const weatherIcon. same make else statment write for all Clear,Rain,Drizzle,Mist.

in data, for weather there are 2 index choose zero for that weather[0]

by defauly we are getting the info, now need to hide info. and it will be only displayed when input is filled. For that it is weather class so go to css make its display none, it will hidden that part of class so after info is filled we need this display attribute as block so. make it like slecting that tag by querySelector then .style.display = "block".

next we need to add one more thing, if we enter wrong city name, it should display error msg.
for that we adding div after serach div, then class named as error and in it givig p tag with writing 'Invalid city name'.
now giving css to error that is text-align is left, margin-left  is 10px, font-size is 14px, margin-top is 10px and now if you save it is showing by deault so make display none now when wrong city enetered we want that display as block so go to js file
after response is declared use if statment that response.status is equal to 404 then that error tag .style.display is equal to block. and also weather info should not be visible so for that weather tag display should be none(write in code). then else statment out whole remeaning code will be there and one more thing if that error msg is coming then in else statment write at last that error tag's style.display will be none.


-------------
------------ dom manipulation
var data="https://api.openweathermap.org/data/2.5/weather?q=germany&appid=52b26f2701fe49d6fe78d686d7b2408c&units=metric";
const response = await fetch(data)
var info= await response.json();
console.log(info);

--------------------------
---------------
