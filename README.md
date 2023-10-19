cake.html

<!doctype html>
<html lang="en">
  <head>
    <title>Cake World</title>
    <link rel="stylesheet" href="style_cake.css">
    <script>
      function myfun() {
        var total = 0;
        total+=parseInt(document.getElementById("i1").value)*450;
        total+=parseInt(document.getElementById("i2").value)*500;
        total+=parseInt(document.getElementById("i3").value)*750;
        total+=parseInt(document.getElementById("i4").value)*550;
        document.getElementById("total").value = '$'+total;
      }
    </script>
  </head>
  <body>
    <div class="header">Cake World</div>
    <div class="menu">
      <div class="item"><img src="src/1.webp" alt=""><div class="caption">Chocolate : $450</div></div>
      <div class="item"><img src="src/2.webp" alt=""><div class="caption">Butterscotch : $500</div></div>
      <div class="item"><img src="src/3.webp" alt=""><div class="caption">Half ChocoVanilla : $750</div></div>
      <div class="item"><img src="src/4.webp" alt=""><div class="caption">Kitkat : $550</div></div>
    </div>
    <div class="header">Order</div>
    <div class="order">
      <div>
        <label for="c">Chocolate</label>
        <input id="i1" type="text" name="c" size="95" value=0>
      </div>
      <div>
        <label for="b">Butterscotch</label>
        <input id="i2" type="text" name="b" size="95" value=0>
      </div>
      <div>
        <label for="cv">ChocoVanilla</label>
        <input id="i3" type="text" name="cv" size="95" value=0>
      </div>
      <div>
        <label for="k">Kitkat</label>
        <input id="i4" type="text" name="k" size="95" value=0>
      </div>
      <input type="button" value="Place Order" onclick="myfun()">
      <div class="total">
        <label for="total">Total : </label>
        <input type="text" name="total" id="total" size="10" style="border: none; background-color:rgb(252, 200, 200);" value="$0">
      </div>
    </div>
  </body>
</html>



cal.js

<!DOCTYPE html>
<html lang="en">
    <head>
        <title>EMI Calculator</title>
        <link rel="stylesheet" href="style_cal.css">
        <script>
            function myfun(){
                var la, ai, t, total;
                p = parseInt(document.getElementById("i1").value);
                r = parseInt(document.getElementById("i2").value)/12/100;
                n = parseInt(document.getElementById("i3").value);
                document.getElementById("s1").innerHTML= "Loan Amount : "+p;
                document.getElementById("s2").innerHTML="Total Interest : "+p*r*n;
                document.getElementById("s3").innerHTML= "EMI : "+ ((p*r*Math.pow((1+r),n))/Math.pow((1+r),n)-1);
                document.getElementById("s4").innerHTML= "Total Repayment : "+eval(p+(p*r*n));
            }
        </script>
    </head>
    <body>
        <div class="cal">
            <div class="title">Loan EMI Calculator</div>
            <label for="la">Loan Amount : </label>
            <input type="text" value="0" id="i1" name="la">
            <label for="ai">Annual Interest Rate : </label>
            <input type="text" value="0" id="i2" name="ai" >
            <label for="t">Tenure : </label>
            <input type="text" value="0" id="i3" name="t" onkeyup="myfun()">
            <div class="res" id="s1">Loan Amount : </div>
            <div class="res" id="s2">Total Interest : </div>
            <div class="res" id="s3">EMI : </div>
            <div class="res" id="s4">Total Repayment : </div>
        </div>
    </body>
</html>


color 

<!DOCTYPE html>
<html>
    <head>
        <title>Q1</title>
        <link rel="stylesheet" href="style.css">
        <script src="script.js"></script>
    </head>
    <body>
        <div id="box" style="height: 250px; width: 250px;"><p id="text">HELLO</p></div>
        <form>
            <fieldset>
                <label for="bg">Background Color : </label>
                <input type="color" name="bg" id="bg_color" onchange="change_bg()">
                <br><br>
                <label for="tc">Text Color : </label>
                <input type="color" name="tc" id="text_color" onchange="change_text_color()">
                <br><br>
                <label for="ts">Text Size : </label>
                <input type="number" name="ts" min="10" id="text_size" value="20" onkeyup="change_text_size()">
                <br><br>
                <label for="bw">Box Width : </label>
                <input type="number" name="bw" id="box_width" value="250" min="250" onkeyup="change_box_width()">
                <br><br>
                <label for="bh">Box Height : </label>
                <input type="number" name="bh" id="box_height" value="250" min="250" onkeyup="change_box_height()"> 
                <br><br>
                <label for="op">Opacity : </label>
                <input type="range" step="5" id="opacity" name="op" onchange="change_box_opacity()">
            </fieldset>
        </form>
    </body>
</html>


function change_bg(){
   document.getElementById('box').style.backgroundColor = document.getElementById('bg_color').value;
}
function change_text_color(){
   document.getElementById('text').style.color = document.getElementById('text_color').value;;
}
function change_text_size(){
   document.getElementById('text').style.fontSize = document.getElementById('text_size').value+"px";
}
function change_box_width(){
   document.getElementById('box').style.width = document.getElementById('box_width').value+"px";
}
function change_box_height(){
   document.getElementById('box').style.height = document.getElementById('box_height').value+"px";
}
function change_box_opacity(){
   document.getElementById('box').style.opacity = document.getElementById('opacity').value+"%";
}


jquery cal

<!DOCTYPE html>
<html lang="en">
    <head>
        <title>DEMO</title>
        <link rel="stylesheet" href="style.css">
        <script src="https://code.jquery.com/jquery-3.6.3.min.js"></script>
        <script>
            $(document).ready(function(){
                $("#bt1").click(function(){
                    var y = 0,d = 0,m = 0;
                    var c_date = new Date();
                    var date = new Date($("#i3").val()+ "-" + $("#i2").val() + "-" + $("#i1").val());
                    d = (Math.floor((c_date-date)/(1000 * 60 * 60 * 24)));
                    m = (Math.floor((d)/31));
                    y = (Math.floor((m)/12));
                    $("#h3").text("Age : "+y+" Years , "+m%12+" Months , "+d%31+" Days ");
        });
    });
        </script>
    </head>
    <body>
        <h1>Age Calculator</h1>
        <div id="box">
            <h2>Enter the Birth Date</h2>
            <div id="cal">
                <label for="day">Day</label>
                <input type="number" name="day" id="i1" >
                <label for="month">Month</label>
                <input type="number" name="month" id="i2" >
                <label for="Year">Year</label>
                <input type="number" name="year" id="i3">
            </div>
            <input type="button" value="Calculate" id="bt1">
        </div>
        <div id="out">
            <h3 id="h3">Age : </h3>
        </div>
    </body>
</html>

angular.js
<!DOCTYPE html>
<html>
  <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
  <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular-route.js"></script>
    <link
        href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css"
        rel="stylesheet">
        

    <body ng-app="myApp">
        <nav class="nav navbar-dark bg-dark row text-center">
            <a href="#/!" class="nav-item nav-link col text-white">About</a>
            <a href="#!acadamic_details" class="nav-item nav-link col text-white">Acadamic Details</a>
            <a href="#!project_details" class="nav-item nav-link col text-white">Project</a>
            <a href="#!sign_in" class="nav-link nav-item col text-white">Sign In</a>
            <a href="#!sign_up" class="nav-link nav-item col text-white">Sign Up</a>
        </nav>
        <div ng-view></div>
        <script>  
          var app = angular.module("myApp", ["ngRoute"]);
            app.config(function($routeProvider) {
              $routeProvider
              .when("/", {
                templateUrl : "main.html"
              })
              .when("/acadamic_details", {
                templateUrl : "acadamic_details.html"
              })
              .when("/project_details", {
                templateUrl : "project_details.html"
              })
              .when("/sign_in", {
                templateUrl : "sign_in.html"
              })
              .when("/sign_up", {
                templateUrl : "sign_up.html"
              });
            });
            </script>
      
              

      </body>
</html>
!!
