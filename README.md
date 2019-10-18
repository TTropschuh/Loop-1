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
