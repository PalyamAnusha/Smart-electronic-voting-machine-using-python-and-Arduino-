# Smart-electronic-voting-machine-using-python-and-Arduino-
A cost-effective and accurate electronic voting machine project developed using Arduino and an LCD display. It simplifies the voting process, ensures transparency, and provides instant results. Features intuitive button-based voting and real-time vote tracking. Perfect for learning or small-scale applications.
# Smart Electronic Voting Machine Using Arduino

## Introduction
This project is a **Smart Electronic Voting Machine (EVM)** developed using **Arduino** and an **LCD display**. The device is designed to modernize the voting process by eliminating the traditional ballot papers and boxes, making it more efficient, accurate, and user-friendly. The system provides an intuitive interface for voters to select their preferred candidate, displays the votes on an LCD for confirmation, and calculates results automatically.

---

## Features
- **Simple and Efficient**: Streamlines the voting process.
- **Accurate Vote Recording**: Reduces errors in vote tallying.
- **Fast Results**: Instant calculation and display of results.
- **Cost-Effective**: Eliminates the need for paper ballots and reduces manual effort.

---

## Components Used
1. **Arduino UNO Board**
2. **16x2 LCD Display**
3. **Potentiometer (10K)**
4. **Push Button Switches**
5. **Connecting Wires**
6. **Breadboard**

---

## Block Diagram
![Block Diagram](evm_pic.png)


---

## Working of the Project
The Arduino microcontroller is the core of the system, managing all operations:
1. Reading input from the buttons assigned to candidates.
2. Incrementing vote counts.
3. Displaying votes and results on the LCD.
4. Ensuring transparency and efficiency.

The system includes:
- **Five Buttons**:
  - Four buttons for voting (Team A, Team B, Team C, NOTA).
  - One button for calculating and displaying results.

When a voter presses a button, the corresponding vote count is incremented. The result button calculates the total votes and displays the winner or notifies of a tie.

---

## Advantages
- **Resource Optimization**: Minimizes manual effort in counting.
- **High Accuracy**: Reduces chances of errors during vote tallying.
- **Speed**: Accelerates the voting and counting processes.
- **Cost-Effective**: Eliminates printing, transportation, and storage costs.

---

## Further Improvements
1. Implement a buzzer to sound after each vote is cast.
2. Cover the LCD during voting to prevent tampering or observation of vote counts.
3. Strengthen security measures for real-world applications.

---

## Architecture and Photos
### Architecture
![Architecture Diagram](images/architecture_diagram.jpg)

### Prototype Images
#### Front View
![Prototype Front View](images/front_view.jpg)

#### Code Snapshot
Here is a snapshot of the backend logic implemented in the `app.py` file:

```python
#include<LiquidCrystal.h>
LiquidCrystal lcd(13, 12, 11, 10, 9, 8);

#define S1 7
#define S2 6
#define S3 5
#define S4 4
#define S5 3
int vote1=0;
int vote2=0;
int vote3=0;
int vote4=0;
void setup()
{
pinMode(S1, INPUT);
pinMode(S2,INPUT);
pinMode(S3,INPUT);
pinMode(S4,INPUT);
pinMode(S5,INPUT);
lcd.begin(16, 2);
lcd.setCursor(2,0);
lcd.print(" Electronic ");
lcd.setCursor(0,1);
lcd.print(" Voting Machine ");
delay(3000);
digitalWrite(S1, HIGH);
digitalWrite(S2, HIGH);
digitalWrite(S3, HIGH);
digitalWrite(S4, HIGH);
digitalWrite(S5, HIGH);
lcd.clear();
lcd.setCursor(0,0);
lcd.print("BJP");
lcd.setCursor(4,0);
lcd.print("INC");
lcd.setCursor(8,0);
lcd.print("NCP");
lcd.setCursor(12,0);
lcd.print("NOTA");
}
void loop()
{
lcd.setCursor(0,0);
lcd.print("BJP");
lcd.setCursor(1,1);
lcd.print(vote1);
lcd.setCursor(4,0);
lcd.print("INC");
lcd.setCursor(5,1);
lcd.print(vote2);
lcd.setCursor(8,0);
lcd.print("NCP");
lcd.setCursor(9,1);
lcd.print(vote3);
lcd.setCursor(12,0);
lcd.print("NOTA");
lcd.setCursor(13,1);
lcd.print(vote4);
if(digitalRead(S1)==0)
vote1++;
while(digitalRead(S1)==0);
if(digitalRead(S2)==0)
vote2++;
while(digitalRead(S2)==0);
if(digitalRead(S3)==0)
vote3++;
while(digitalRead(S3)==0);
if(digitalRead(S4)==0)
vote4++;
while(digitalRead(S4)==0);
if(digitalRead(S5)==0)
{
int vote=vote1+vote2+vote3+vote4;
if(vote)
{
if((vote1 > vote2 && vote1 > vote3 && vote1 > vote4))
{
lcd.clear();
lcd.setCursor(1,0);
lcd.print("BJP is Winner");
delay(3000);
lcd.clear();
}
else if((vote2 > vote1 && vote2 > vote3 && vote2 > vote4))
{
lcd.clear();
lcd.setCursor(1,0);
lcd.print("INC is Winner");
delay(3000);
lcd.clear();
}
else if((vote3 > vote1 && vote3 > vote2 && vote3 > vote4))
{
lcd.clear();
lcd.setCursor(1,0);
lcd.print("NCP is Winner");
delay(3000);
lcd.clear();
}
else if(vote4 > vote1 && vote4 > vote2 && vote4 > vote3)
{
lcd.setCursor(0,0);
lcd.clear();
lcd.setCursor(1,0);
lcd.print("NOTA is Winner");
delay(3000);
lcd.clear();
}

else
{
lcd.clear();
lcd.setCursor(5,0);
lcd.print(" TIE ");
lcd.setCursor(2,1);
lcd.print(" No Result ");
delay(3000);
lcd.clear();
}

}
else
{
lcd.clear();
lcd.setCursor(2,0);
lcd.print("No Voting...");
delay(3000);
lcd.clear();
}
vote1=0;vote2=0;vote3=0;vote4=0,vote=0;
lcd.clear();
}

}
```

---

## Conclusion
This Smart Electronic Voting Machine improves the efficiency, accuracy, and transparency of the electoral process, making it a viable replacement for conventional voting systems. With additional features and enhanced security, it can be scaled for real-world use cases.

---

## How to Use
1. Clone this repository.
2. Upload the provided Arduino code to your Arduino UNO board.
3. Assemble the components as described in the documentation.
4. Run the system and start voting!

---

## License
This project is licensed under the [MIT License](LICENSE).


