![recursive art](https://user-images.githubusercontent.com/31697395/35227560-6fe30a3a-ff5c-11e7-95ba-a6a2d293a07e.gif)

By using random numbers and if statements to create chance for each shape I created art using circles and squares.

var drawShape = function(x, y, radius) {
    //randomizing shape
    var randomNumber=round(random(1,2));
    //randomizing colour each layer
    fill(random(0,255), random(0,255), random(0,255));
    //if starement
    if(randomNumber===1){
    ellipse(x, y, radius, radius);
    
    }
    else if(randomNumber===2){
    rect(x, y, x, y);
    
    }
    
    //allowing pattern to continue to end of canvas
    var newRadius = radius/2;
    if (newRadius >= 2) {
        drawShape(x, y, newRadius);
        drawShape(x/2, y/2, newRadius);
    }
};

//calling functions
drawShape(width/2, height/2, 395);
