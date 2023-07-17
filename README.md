# Matrix-8x8-Using-Arduino

![Copy of NAME USING 8x8 LED Matrix](https://github.com/M7moodalhayes/Matrix-8x8-Using-Arduino/assets/79692306/15107ee2-d2cb-4965-9a2f-179118381310)


the code to make ♡

#define ROW1 13
#define ROW2 12
#define ROW3 11
#define ROW4 10
#define ROW5 9
#define ROW6 8
#define ROW7 7
#define ROW8 6

#define COL1 5
#define COL2 4
#define COL3 3
#define COL4 2
#define COL5 A4
#define COL6 A3
#define COL7 A2
#define COL8 A1

const int row[] = {ROW1, ROW2, ROW3, ROW4, ROW5, ROW6, ROW7, ROW8};
const int col[] = {COL1, COL2, COL3, COL4, COL5, COL6, COL7, COL8};

int heart[8][8] = {
  {0, 1, 1, 0, 0, 1, 1, 0},
  {1, 1, 1, 1, 1, 1, 1, 1},
  {1, 1, 1, 1, 1, 1, 1, 1},
  {0, 1, 1, 1, 1, 1, 1, 0},
  {0, 0, 1, 1, 1, 1, 0, 0},
  {0, 0, 0, 1, 1, 0, 0, 0},
  {0, 0, 0, 0, 0, 0, 0, 0},
  {0, 0, 0, 0, 0, 0, 0, 0}
};

void setup() {
  Serial.begin(9600);
  for (int i = 2; i <= 13; i++) {
    pinMode(i, OUTPUT);
    digitalWrite(i, LOW);
  }
  pinMode(A4, OUTPUT);
  digitalWrite(A4, LOW);
  pinMode(A3, OUTPUT);
  digitalWrite(A3, LOW);
  pinMode(A2, OUTPUT);
  digitalWrite(A2, LOW);
  pinMode(A1, OUTPUT);
  digitalWrite(A1, LOW);
}

void loop() {
  led(heart);
  delay(1500);
}

void led(int matrix[8][8]) {
  for (int i = 0; i < 50; i++) {
    for (int c = 0; c < 8; c++) {
      digitalWrite(col[c], HIGH);
      for (int r = 0; r < 8; r++) {
        digitalWrite(row[r], matrix[r][c]);
      }
      for (int r = 0; r < 8; r++) {
        digitalWrite(row[r], HIGH);
      }
      digitalWrite(col[c], LOW);
    }
    if (i == 49) {
      break;
    }
  }
}
