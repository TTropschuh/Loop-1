## Midterm (But it doesn't work)
```javascript
let player;
let aim;
let plusPoints;
let minusPoints;


function setup() {
  createCanvas(700, 700);
  player = new Player(width / 2, height / 9, 10, color("#FFA500"));
  aim = new Aim(width / 2, height - 100, 50, color("#FFA500"));
  plusPoints = new points(0, 200, 10, color("#008000"));
  minusPoints = new points(0, 0, 10, color('red'));
}

function draw() {
  background('#0059FF');
  player.checkBounds();

  if (player.containsm(minusPoints)) {
    player.eatPoison(minusPoints);
    print("You hit me!");
  } else {
    print("You didnt hit me");
  }

  if (player.containsp(plusPoints)) {
    player.eatFood(plusPoints);
    print("I got eaten");
  } else {
    print("I am still alive!");
  }


  for (this.x = 0; this.x < 300; this.x++) {
    player.draw();
  }
  minusPoints.draw();
  plusPoints.draw();
  aim.draw();


  fill(255);
  textSize(36);
  text(player.score, 30, height - 40);
}

function keyPressed() {
  if (keyCode == LEFT_ARROW) {
    player.moveLeft();
  } else if (keyCode == RIGHT_ARROW) {
    player.moveRight();
  }

  if (keyCode == UP_ARROW) {
    player.moveUp();
  } else if (keyCode == DOWN_ARROW) {
    player.moveDown();
  }
}

class Player {
  constructor(x, y, r, c) {
    this.x = x;
    this.y = y;
    this.r = r;
    this.c = c;
    this.speed = 10;
    this.score = 0;
  }


  moveUp() {
    this.y -= this.speed;
  }

  moveDown() {
    this.y += this.speed;
  }

  moveLeft() {
    this.x -= this.speed;
  }

  moveRight() {
    this.x += this.speed;
  }


  checkBounds() {
    if (this.y < 0) {
      this.y = 10;
    }
    if (this.y > height) {
      this.y = height - 10;
    }
    if (this.x < 0) {
      this.x = 10;
    }
    if (this.x > width) {
      this.x = width - 10;
    }
  }

  containsp(aFood) {
    if (dist(this.x, this.y, aFood.x, aFood.y) < this.r / 2) {
      return true;
    } else {
      return false;
      print("I am false");
    }
  }

  eatFood(aFood) {
    aFood.eaten = true;
    aFood.x = -1000;
    aFood.y = -1000;
    this.score = this.score + 1;
  }

  containsm(aPoison) {
    if (dist(this.x, this.y, aPoison.x, aPoison.y) < this.r / 2) {
      return true;
    } else {
      return false;
      print("I am flase");
    }
  }

  eatPoison(aPoison) {
    aPoison.eaten = true;
    aPoison.x = -1000;
    aPoison.y = -1000;
    this.score = this.score - 1;
  }

  draw() {
    noStroke();
    fill(this.c);
    ellipse(this.x, this.y, this.r, this.r);
  }
}


class points {
  constructor(x, y, r, c) {
    this.x = x;
    this.y = y;
    this.r = r;
    this.c = c;
    this.eaten = true;
    this.theta = 0;
  }

  draw() {
    if (this.eaten) {
      push();
      translate(width / 2, height / 2);
      let num = 20;
      this.theta += 0.01;
      for (let i = 0; i < TWO_PI; i += TWO_PI / num) {
        push();
        rotate(this.theta + i);
        translate(100, 0);
        noStroke();
        fill('red');
        ellipse(this.x, this.y, this.r, this.r);
        pop();
      }
      pop();

    }

  }

  disappear() {
    this.eaten = false;
  }

}

class Aim {
  constructor(x, y, r, c) {
    this.x = x;
    this.y = y;
    this.r = r;
    this.c = c;
  }

  draw() {
    noStroke();
    fill(this.c);
    ellipse(this.x, this.y, this.r, this.r);
  }


}
```

## Working "Play" Sketch 

I managed to make a game with key inputs, a minus point and a pluspoint. I worked with classes and added a counter. So far so good.

```javascript

let player;
let aim;
let plusPoints;
let minusPoints;


function setup() {
  createCanvas(700, 700);
  player = new Player(width / 2, height / 9, 10, color("#FFA500"));
  aim = new Aim(width / 2, height - 100, 50, color("#FFA500"));
  plusPoints = new points(width / 3, height / 2, 10, color("#008000"));
  minusPoints = new points(width / 2, height / 2, 10, color('red'));
}

function draw() {
  background('#0059FF');
  player.checkBounds();

  if (player.contains(minusPoints)) {
    player.eatPoison(minusPoints);
    print("You hit me!");
  } else {
    print("You didnt hit me");
  }

  if (player.contains(plusPoints)) {
    player.eatFood(plusPoints);
    print("I got eaten");
  } else {
    print("I am still alive!");
  }


  for(this.x = 0; this.x < 300; this.x++){
    player.draw();
  }
  minusPoints.draw();
  plusPoints.draw();
  aim.draw();


  fill(255);
  textSize(36);
  text(player.score, 30, height - 40);

}

function keyPressed() {
  if (keyCode == LEFT_ARROW) {
    player.moveLeft();
  } else if (keyCode == RIGHT_ARROW) {
    player.moveRight();
  }

  if (keyCode == UP_ARROW) {
    player.moveUp();
  } else if (keyCode == DOWN_ARROW) {
    player.moveDown();
  }
}

class Player {
  constructor(x, y, r, c) {
    this.x = x;
    this.y = y;
    this.r = r;
    this.c = c;
    this.speed = 10;
    this.score = 0;
  }


  moveUp() {
    this.y -= this.speed;
  }

  moveDown() {
    this.y += this.speed;
  }

  moveLeft() {
    this.x -= this.speed;
  }

  moveRight() {
    this.x += this.speed;
  }


  checkBounds() {
    if (this.y < 0) {
      this.y = 10;
    }
    if (this.y > height) {
      this.y = height - 10;
    }
    if (this.x < 0) {
      this.x = 10;
    }
    if (this.x > width) {
      this.x = width - 10;
    }
  }

  contains(aFood) {
    if (dist(this.x, this.y, aFood.x, aFood.y) < this.r / 2) {
      return true;
    } else {
      return false;
      print("I am false");
    }
  }

  eatFood(aFood) {
    aFood.eaten = true;
    aFood.x = -1000;
    aFood.y = -1000;
    this.score = this.score + 1;
  }

  contains(aPoison) {
    if (dist(this.x, this.y, aPoison.x, aPoison.y) < this.r / 2) {
      return true;
    } else {
      return false;
      print("I am flase");
    }
  }

  eatPoison(aPoison) {
    aPoison.eaten = true;
    aPoison.x = -1000;
    aPoison.y = -1000;
    this.score = this.score - 1;
  }

  draw() {
    noStroke();
    fill(this.c);
    ellipse(this.x, this.y, this.r, this.r);
  }
}


class points {
  constructor(x, y, r, c) {
    this.x = x;
    this.y = y;
    this.r = r;
    this.c = c;
    this.eaten = true;
  }

  draw() {
    if (this.eaten) {
        noStroke();
        fill(this.c);
        ellipse(this.x, this.y, this.r, this.r);
    }

  }

  disappear() {
    this.eaten = false;
  }

}

class Aim {
  constructor(x, y, r, c) {
    this.x = x;
    this.y = y;
    this.r = r;
    this.c = c;
  }

  draw() {
    noStroke();
    fill(this.c);
    ellipse(this.x, this.y, this.r, this.r);
  }


}
```

## Working "MinusPoints and PlusPoints" Sketch

Here I finally found a way to get those "points" into a for loop so that they keep rotating. Also works fine. 

```javascript
let theta = 0;

function setup() {
  createCanvas(480, 720);
}

function draw() {
  background(255);
  rotatingCircle(100);
  
}

function rotatingCircle(){
  translate(width / 2, height / 2);
  let num=20;
  theta += 0.01;
  for (let i = 0; i < TWO_PI; i += TWO_PI / num) {
    push();
    rotate(theta + i);
    translate(100, 0);
    noStroke();
    fill('red');
    ellipse(0, 0, 10, 10);
    pop();
  }

}
```

## Not working Sketch

Here I tried to combine those two sketches and put the for loop from the sketch before into the "Points" Class. But when I run it the translate command makes things weird. Where do I have to put the this "rotating" for loop? In the normal draw function? Or do I need to make a seperate function in the class itself?


```javascript
let player;
let aim;
let plusPoints;
let minusPoints;


function setup() {
  createCanvas(700, 700);
  player = new Player(width / 2, height / 9, 10, color("#FFA500"));
  aim = new Aim(width / 2, height - 100, 50, color("#FFA500"));
  plusPoints = new points(width / 3, height / 2, 10, color("#008000"));
  minusPoints = new points(width / 2, height / 2, 10, color('red'));
}

function draw() {
  background('#0059FF');
  player.checkBounds();

  if (player.contains(minusPoints)) {
    player.eatPoison(minusPoints);
    print("You hit me!");
  } else {
    print("You didnt hit me");
  }

  if (player.contains(plusPoints)) {
    player.eatFood(plusPoints);
    print("I got eaten");
  } else {
    print("I am still alive!");
  }


  for (this.x = 0; this.x < 300; this.x++) {
    player.draw();
  }

  minusPoints.draw();
  plusPoints.draw();
  aim.draw();


  fill(255);
  textSize(36);
  text(player.score, 30, height - 40);

}

function keyPressed() {
  if (keyCode == LEFT_ARROW) {
    player.moveLeft();
  } else if (keyCode == RIGHT_ARROW) {
    player.moveRight();
  }

  if (keyCode == UP_ARROW) {
    player.moveUp();
  } else if (keyCode == DOWN_ARROW) {
    player.moveDown();
  }
}

class Player {
  constructor(x, y, r, c) {
    this.x = x;
    this.y = y;
    this.r = r;
    this.c = c;
    this.speed = 10;
    this.score = 0;
    this.theta = 0;
  }


  moveUp() {
    this.y -= this.speed;
  }

  moveDown() {
    this.y += this.speed;
  }

  moveLeft() {
    this.x -= this.speed;
  }

  moveRight() {
    this.x += this.speed;
  }


  checkBounds() {
    if (this.y < 0) {
      this.y = 10;
    }
    if (this.y > height) {
      this.y = height - 10;
    }
    if (this.x < 0) {
      this.x = 10;
    }
    if (this.x > width) {
      this.x = width - 10;
    }
  }

  contains(aFood) {
    if (dist(this.x, this.y, aFood.x, aFood.y) < this.r / 2) {
      return true;
    } else {
      return false;
      print("I am false");
    }
  }

  eatFood(aFood) {
    aFood.eaten = true;
    aFood.x = -1000;
    aFood.y = -1000;
    this.score = this.score + 1;
  }

  contains(aPoison) {
    if (dist(this.x, this.y, aPoison.x, aPoison.y) < this.r / 2) {
      return true;
    } else {
      return false;
      print("I am flase");
    }
  }

  eatPoison(aPoison) {
    aPoison.eaten = true;
    aPoison.x = -1000;
    aPoison.y = -1000;
    this.score = this.score - 1;
  }

  draw() {


    //noStroke();
    //fill(this.c);
    //ellipse(this.x, this.y, this.r, this.r);
  }
}



class points {
  constructor(x, y, r, c) {
    this.x = x;
    this.y = y;
    this.r = r;
    this.c = c;
    this.eaten = true;
  }

  draw() {
    if (this.eaten) {

      translate(width / 2, height / 2);
      let num = 20;
      this.theta += 0.01;
      for (let i = 0; i < TWO_PI; i += TWO_PI / num) {
        push();
        rotate(this.theta + i);
        translate(100, 0);
        noStroke();
        fill('red');
        ellipse(0, 0, 10, 10);
        pop();
      }
    }
  }



  disappear() {
    this.eaten = false;
  }

}

class Aim {
  constructor(x, y, r, c) {
    this.x = x;
    this.y = y;
    this.r = r;
    this.c = c;
  }

  draw() {
    noStroke();
    fill(this.c);
    ellipse(this.x, this.y, this.r, this.r);
  }


}
```
