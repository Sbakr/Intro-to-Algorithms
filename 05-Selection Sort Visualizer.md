
<img width="443" alt="screen shot 2017-10-11 at 10 18 35 pm" src="https://user-images.githubusercontent.com/31697395/31476029-3bcbbf74-aed2-11e7-8c62-0d51548ed19c.png">

//set background for colours
background(32, 33, 77);
    var x = 50; var y = 20;

//displays the numbers and circles  
var displayArray = function(array, min, swatching) {
    stroke(0, 0, 0);
    textSize(15);
    for(var i=0; i<array.length;i++) {
        text(array[i], x, y);
        x+=30;
        if (array[i] === array[min]) {
            stroke(224, 38, 38);
            noFill();
            ellipse(x-22,y-25,20,20);
        }  
        
        if (array[i] === swatching) {
            stroke(212, 149, 32);
            noFill();
            ellipse(x-22,y-5,20,20);
        }
    }
    y+=20;
    x=50;
};

//swaps the placements to get the lower number come first  
var swap = function(array, firstIndex, secondIndex) {
    var temp = array[firstIndex]; 
    array[firstIndex] = array[secondIndex]; 
    array[secondIndex] = temp;
};  

//finds the smallest number in the array  
var indexOfMinimum = function(array, startIndex) {
    var minValue = array[startIndex]; 
    var minIndex = startIndex; 
    for(var i = minIndex + 1 ; i < array.length; i++) {
        if(array[i] < minValue) { 
            minIndex = i; 
            minValue = array[i];
        }
    } 
    return minIndex;
}; 

//makes sure that there are no smaller numbers in array  
var selectionSort = function(array) {
    var min;
    for(var i = 0; i < array.length; i++) {
        //println(min);  
        //println(array[min]);  
        //println("HEYYYYYY");  
        //println(i);  
        var swatching = array[i];
        //println(swatching);
        displayArray(array, min, swatching);
        min = indexOfMinimum(array, i);
        swap(array, i, min);
        
    }
};

//assertions and startup arrays  
var array = [22, 11, 99, 9, 88];
selectionSort(array);
Program.assertEqual(array, [9, 11, 22, 88, 99]);

text("________________________", x-15, y-15);
var array = [23,15, 2, 0, 9];
selectionSort(array);
Program.assertEqual(array, [0, 2, 9, 15, 23]);

text("________________________", x-15, y-15);
var array = [5, 4, 2, 1,];
selectionSort(array);
Program.assertEqual(array, [1,2,4,5]);

text("________________________", x-15, y-15);
var array = [5, 63, 90, 2, 3];
selectionSort(array);
Program.assertEqual(array, [2, 3, 5, 63, 90]);
