# Loop-Sketch 1

```javascript

function setup() {
  createCanvas(400, 400);
}

function draw() {

  background(40);


  drawCircle(width / 2, height / 2, 100, 5)

}

function drawCircle(x_pos, y_pos, size, num) {

  let steps = size / num;
  for (let i = 0; i < num; i++) {
    ellipse(x_pos, y_pos, size - i * steps, size - i * steps);

    noFill();
    strokeWeight(6);
    stroke(255);
  }
}
}
```

# Loop-Sketch 2

```javascript
function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(255);


  drawSquares(9);
}

function drawSquares(num) {
  for (let i = 0; i < num; i++) {
    let size = 55;
    let steps = size + 30;
    rect(width / 2 + i * steps, height / 2, size, size);

    rectMode(CENTER);
    fill(100, 200, 0);
  }
}

// do I need another for loop to get the rectangles on both sides?
```
