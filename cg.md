# Practical-1
**Study and implement various graphic functions and VGA standards.**

## 1. Circle()
- **Description:** Draws a circle with center at (x, y) and given radius.
- **Syntax:** `circle(x, y, radius);`
- **Example:** `circle(250, 200, 50);`

---

## 2. Rectangle()
- **Description:** Draws a rectangle on the screen. (x1, y1) are the lower-left coordinates, and (x2, y2) are the upper-right coordinates.
- **Syntax:** `rectangle(x1, y1, x2, y2);`
- **Example:**
    ```cpp
    int main() {
        int gd = DETECT, gm;
        initgraph(&gd, &gm, "");
        rectangle(100, 100, 300, 200);
        closegraph();
        return 0;
    }
    ```

---

## 3. Ellipse()
- **Description:** Draws an ellipse with specified start angle, end angle, x-radius, and y-radius.
- **Syntax:** `void ellipse(int x, int y, int startAngle, int endAngle, int xRadius, int yRadius);`
- **Example:**
    ```cpp
    #include <graphics.h>
    int main() {
        int gd = DETECT, gm;
        initgraph(&gd, &gm, "");
        ellipse(200, 150, 0, 360, 100, 50);
        closegraph();
        return 0;
    }
    ```

---

## 4. Arc()
- **Description:** Draws an arc.
- **Syntax:** `void arc(int x, int y, int startAngle, int endAngle, int radius);`
- **Example:**
    ```cpp
    #include <graphics.h>
    int main() {
        int gd = DETECT, gm;
        initgraph(&gd, &gm, "");
        arc(200, 150, 0, 90, 50);
        closegraph();
        return 0;
    }
    ```

---

## 5. Floodfill()
- **Description:** Fills a closed object (like a circle or rectangle) with color.
- **Syntax:** `floodfill(x, y, boundary_color);`
- **Example:** `floodfill(100, 100, BLUE);`

---

## 6. Getpixel()
- **Description:** Gets the color of a specified pixel.
- **Syntax:** `getpixel(x, y);`
- **Example:** `color = getpixel(100, 100);`

---

## 7. Initgraph()
- **Description:** Initializes the graphics system by loading a graphics driver from disk and putting the system into graphics mode.
- **Syntax:** `void initgraph(int *graphdriver, int *graphmode, char *pathtodriver);`
- **Example:**
    ```cpp
    #include <graphics.h>
    #include <stdlib.h>
    #include <stdio.h>
    #include <conio.h>

    int main(void) {
        int gdriver = DETECT, gmode, errorcode;
        initgraph(&gdriver, &gmode, "");
    }
    ```

---

## 8. Closegraph()
- **Description:** Deallocates all memory allocated by the graphics system and restores the screen to the mode it was in before calling initgraph.
- **Syntax:** `void closegraph(int wid = ALL_WINDOWS);`
- **Example:**
    ```cpp
    int main() {
        closegraph();
        return 0;
    }
    ```

---

## 9. Detectgraph()
- **Description:** Detects your system's graphics adapter and chooses the mode with the highest resolution for that adapter.
- **Syntax:** `void detectgraph(int *graphdriver, int *graphmode);`
- **Example:**
    ```cpp
    #include <graphics.h>
    #include <stdlib.h>
    #include <stdio.h>
    #include <conio.h>

    char *dname[] = { "requests detection", "a CGA" };

    int main(void) {
        int gdriver, gmode, errorcode;
        detectgraph(&gdriver, &gmode);
    }
    ```

---

## 10. Graphresult()
- **Description:** Returns the error code for the last graphics operation that reported an error and resets the error level to grOk.
- **Syntax:** `int graphresult(void);`
- **Example:**
    ```cpp
    #include <graphics.h>
    #include <stdlib.h>
    #include <stdio.h>
    #include <conio.h>

    int main(void) {
        int gdriver = DETECT, gmode, errorcode;
        initgraph(&gdriver, &gmode, "");
        errorcode = graphresult();
    }
    ```

---

## 11. Getmaxx()
- **Description:** Returns the maximum x-coordinate on the screen.
- **Syntax:** `getmaxx();`
- **Example:** `maxx = getmaxx();`

---

## 12. Getmaxy()
- **Description:** Returns the maximum y-coordinate on the screen.
- **Syntax:** `getmaxy();`
- **Example:** `maxy = getmaxy();`

---

## 13. Getcolor()
- **Description:** Returns the current drawing color.
- **Syntax:** `int getcolor(void);`
- **Example:**
    ```cpp
    int main() {
        int gd = DETECT, gm, drawing_color;
        char a[100];
        initgraph(&gd, &gm, "C:\\TC\\BGI");
        drawing_color = getcolor();
        sprintf(a, "Current drawing color = %d", drawing_color);
        outtextxy(10, 10, a);
        getch();
        closegraph();
        return 0;
    }
    ```

---

## 14. Outtextxy()
- **Description:** Prints text on the screen in graphics mode at specified coordinates.
- **Syntax:** `outtextxy(x, y, "text");`
- **Example:** `outtextxy(100, 100, "HELLO");`

---

## 15. Outtext()
- **Description:** Displays text on the screen at the current position.
- **Syntax:** `outtext(STRING);`
- **Example:** `outtext("HELLO");`

---

## 16. Settextstyle()
- **Description:** Sets the current text font, direction, and size.
- **Syntax:** `void settextstyle(int font, int direction, int charSize);`
- **Example:**
    ```cpp
    int main() {
        int gd = DETECT, gm;
        initgraph(&gd, &gm, "");
        settextstyle(DEFAULT_FONT, HORIZ_DIR, 2);
        outtextxy(100, 100, "Hello, World!");
        closegraph();
        return 0;
    }
    ```

---

## 17. Getgraphmode()
- **Description:** Returns the current graphics mode.
- **Syntax:** `int getgraphmode(void);`
- **Example:**
    ```cpp
    #include <graphics.h>
    #include <stdlib.h>
    #include <stdio.h>
    #include <conio.h>

    int main(void) {
        int gdriver = DETECT, gmode, errorcode;
        int midx, midy, mode;
        char numname[80], modename[80];

        initgraph(&gdriver, &gmode, "");
        errorcode = graphresult();
        if (errorcode != grOk) {
            printf("Graphics error: %s\n", grapherrormsg(errorcode));
            printf("Press any key to halt:");
            getch();
            exit(1);
        }

        midx = getmaxx() / 2;
        midy = getmaxy() / 2;

        mode = getgraphmode();
        sprintf(numname, "%d is the current mode number.", mode);
        sprintf(modename, "%s is the current graphics mode.", getmodename(mode));
    }
    ```


# Practical-2
## Write a program to draw a line, circle, ellipse, arc, sector, and bar using functions.

```c
#include <graphics.h>
#include <conio.h>

void main() {
    int graphicdriver = DETECT, graphicmode;
    
    // Initialize graphics mode
    initgraph(&graphicdriver, &graphicmode, "c:\\turboc3\\bgi");
    
    // Display program information
    outtextxy(10, 12 + 10, "Program to draw a circle, ellipse, arc, sector, bar, and line");
    outtextxy(5, 10, "Rohit Parit   00313702022");
    
    // Drawing various shapes
    arc(100, 250, 180, 0, 50); // Arc
    sector(250, 300, 0, 70, 100, 100); // Sector
    circle(100, 100, 50); // Circle
    ellipse(300, 110, 0, 360, 100, 50); // Ellipse
    bar(120, 350, 100, 550); // Bar (coordinates adjusted for proper display)
    line(350, 550, 350, 350); // Line

    // Wait for user input to close the graphics window
    getch();
    closegraph();
}
```
Output :

![image](https://github.com/user-attachments/assets/f8030ee7-3277-4bd9-9d41-eba0638be36d)


# Practical-3
## Write a program to implement functions and draw nested circles and rectangles.

```c
#include <conio.h>
#include <graphics.h>

void main() {
    int graphicdriver = DETECT, graphicmode;
    
    // Initialize graphics mode
    initgraph(&graphicdriver, &graphicmode, "c:\\turboc3\\bgi");
    
    // Display program information
    outtextxy(20, 30, "Program to draw nested circle and rectangle");
    outtextxy(10, 20, "Rohit Parit   00313702022");
    
    // Nested rectangles
    outtextxy(70, 260, "Nested Rectangle");
    rectangle(100, 100, 160, 160); // Inner rectangle
    setcolor(RED);
    rectangle(80, 80, 180, 180); // Second rectangle
    setcolor(BLUE);
    rectangle(60, 60, 200, 200); // Third rectangle
    setcolor(YELLOW);
    rectangle(40, 40, 220, 220); // Outer rectangle
    setcolor(GREEN);
    
    // Nested circles
    outtextxy(400, 290, "Nested Circle");
    circle(450, 150, 120); // Outer circle
    setcolor(RED);
    circle(450, 150, 100); // Second circle
    setcolor(BLUE);
    circle(450, 150, 80); // Third circle
    setcolor(YELLOW);
    circle(450, 150, 60); // Inner circle

    // Wait for user input to close the graphics window
    getch();
    closegraph();
}
```
Output:
![image](https://github.com/user-attachments/assets/f0efcf65-1f47-4d1f-86fc-9d7d3cbc8bcb)


# Practical-4
## Write a program to display an asterisk inside a circle on the screen.

```c
#include <graphics.h>
#include <conio.h>

void main() {
    int graphicdriver = DETECT, graphicmode;
    initgraph(&graphicdriver, &graphicmode, "c:\\turboc3\\bgi");
    
    // Draw a circle
    circle(300, 200, 75);
    
    // Display program information
    outtextxy(200, 30, "Program to draw an asterisk inside the circle");
    outtextxy(200, 10, "Rohit Parit   00313702022");
    
    // Draw an asterisk using lines
    line(225, 200, 375, 200); // Horizontal line
    line(300, 125, 300, 270); // Vertical line
    line(250, 150, 350, 250); // Diagonal line \
    line(350, 150, 250, 250); // Diagonal line /
    
    // Wait for user input to close the graphics window
    getch();
    closegraph();
}
```
Output:
![image](https://github.com/user-attachments/assets/cd91c868-5cef-4d99-a1db-4e499a49bb1d)



# Practical-5
## Write a program to display a coordinate axis.

```c
#include <conio.h>
#include <graphics.h>

void main() {
    int a, b, i;
    int gd = DETECT, gn;
    initgraph(&gd, &gn, "c:\\turboc3\\bgi");
    
    // Get maximum dimensions
    a = getmaxx();
    b = getmaxy();
    
    // Draw coordinate axes
    line(a / 2, 0, a / 2, b); // Y-axis
    line(0, b / 2, a, b / 2); // X-axis
    
    // Display program information
    outtextxy(5, 10, "Rohit Parit   00313702022");
    outtextxy(a - 50, b / 2.75, "x-axis");
    outtextxy(a / 2.75, b - 50, "y-axis");
    
    // Draw ticks on the axes
    for (i = 0; i < a; i += 35) {
        line(a / 2 + i, b / 2 - 10, a / 2 + i, b / 2 + 10);
        line(a / 2 - i, b / 2 + 10, a / 2 - i, b / 2 - 10);
        line(a / 2 + 10, b / 2 - i, a / 2 + 10, b / 2 + i);
        line(a / 2 - 10, b / 2 + i, a / 2 - 10, b / 2 - 10);
    }
    
    // Wait for user input to close the graphics window
    getch();
    closegraph();
}
```
Output :
![image](https://github.com/user-attachments/assets/d05773ab-c232-49e2-9278-dc3ad6964d2c)



# Practical-6
## Write a program to make a bar chart for students for five years.

```c
#include <conio.h>
#include <graphics.h>

void main() {
    int a, b;
    int gd = DETECT, gm;
    initgraph(&gd, &gm, "c:\\turboc3\\bgi");
    
    // Draw axes for bar chart
    line(80, 60, 80, 380);   // Y-axis
    line(80, 380, 550, 380); // X-axis
    
    // Display program information
    outtextxy(120, 30, "Write a program to make a bar chart for five years");
    outtextxy(120, 10, "Rohit Parit 00313702022");
    outtextxy(20, 70, "y-axis");
    outtextxy(570, 390, "x-axis");
    
    // Draw bars for each year
    setfillstyle(SOLID_FILL, 7);
    bar(120, 280, 170, 375); // 2017
    outtextxy(130, 390, "2017");
    
    setfillstyle(XHATCH_FILL, 6);
    bar(200, 120, 250, 375); // 2018
    outtextxy(210, 390, "2018");
    
    setfillstyle(HATCH_FILL, 8);
    bar(280, 320, 330, 375); // 2019
    outtextxy(290, 390, "2019");
    
    setfillstyle(WIDE_DOT_FILL, 9);
    bar(360, 200, 410, 375); // 2020
    outtextxy(370, 390, "2020");
    
    setfillstyle(LTBKSLASH_FILL, 10);
    bar(440, 100, 490, 375); // 2021
    outtextxy(450, 390, "2021");
    
    // Wait for user input to close the graphics window
    getch();
    closegraph();
}
```

Output :
![image](https://github.com/user-attachments/assets/99c98ae8-6c4a-488b-b76a-1875e8f69c1f)


# Practical-7
## Write a program to make a pie chart for students.

```c
#include <conio.h>
#include <graphics.h>

void main() {
    int gd = DETECT, gm;
    initgraph(&gd, &gm, "c:\\turboc3\\bgi");
    
    // Display program information
    outtextxy(210, 30, "Write a program to make a pie chart for students");
    outtextxy(210, 10, "Rohit Parit 00313702022");
    outtextxy(200, 100, "Pie Chart");
    
    // Draw pie slices
    setfillstyle(SOLID_FILL, 1);
    pieslice(100, 100, 0, 70, 75);
    
    setfillstyle(XHATCH_FILL, 2);
    pieslice(100, 100, 70, 150, 75);
    
    setfillstyle(HATCH_FILL, 12);
    pieslice(100, 100, 150, 250, 75);
    
    setfillstyle(WIDE_DOT_FILL, 9);
    pieslice(100, 100, 250, 300, 75);
    
    setfillstyle(INTERLEAVE_FILL, 6);
    pieslice(100, 100, 290, 360, 75);
    
    // Wait for user input to close the graphics window
    getch();
    closegraph();
}
```

Output :
![image](https://github.com/user-attachments/assets/b18e0c73-ca76-4025-9691-12aa923a8ed9)


# Practical 8
## Write a program to scan convert a line using DDA algorithm.

```c
#include<graphics.h>
#include<conio.h>
#include<stdio.h>
#include<math.h>

void main() {
    int gd = DETECT, gm;
    int x1, x2, y1, y2, length, dx, dy, x, y, i;
    clrscr();
    printf("Rohit Parit 0663702022");
    printf("Write a program to scan convert a line using DDA algorithm.");
    printf("\n Enter x1 and y1 coordinates:");
    scanf("%d%d", &x1, &y1);
    printf("\n Enter x2 and y2 coordinates:");
    scanf("%d%d", &x2, &y2);
    initgraph(&gd, &gm, "c:\\turboc3\\bgi");
    
    if (abs(x2 - x1) >= abs(y2 - y1)) {
        length = abs(x2 - x1);
    } else {
        length = abs(y2 - y1);
    }
    
    dx = (x2 - x1) / length;
    dy = (y2 - y1) / length;
    x = x1 + 0.5;
    y = y1 + 0.5;
    i = 1;
    
    while (i <= length) {
        putpixel(x, y, 2);
        x = x + dx;
        y = y + dy;
        i = i + 1;
    }
    
    getch();
    closegraph();
}
```
Output:
![image](https://github.com/user-attachments/assets/b0e85de6-be8e-463b-840b-777f6b650a9b)
![image](https://github.com/user-attachments/assets/c3c3ef68-f76d-4d4d-bc56-ed434944dcc7)


# Practical 9
## Write a program to scan convert a line using Bresenham’s algorithm.

```c
#include<graphics.h>
#include<conio.h>
#include<stdio.h>
#include<math.h>

void main() {
    int gd = DETECT, gm;
    int x1, x2, y1, y2, dx, dy, x, y, p;
    clrscr();
    printf("Write a program to scan convert a line using Bresenham's algorithm.");
    printf("\n Rohit Parit 00313702022");
    printf("\n Enter x1 and y1 coordinates: ");
    scanf("%d%d", &x1, &y1);
    printf("\n Enter x2 and y2 coordinates: ");
    scanf("%d%d", &x2, &y2);

    dx = x2 - x1;
    dy = y2 - y1;
    p = 2 * (dy) - (dx);
    x = x1;
    y = y1;
    initgraph(&gd, &gm, "c:\\turboc3\\bgi");
    putpixel(x, y, 2);
    
    while (x <= x2) {
        if (p < 0) {
            x = x + 1;
            y = y;
            p = p + 2 * (dy);
        } else {
            x = x + 1;
            y = y + 1;
            p = p + 2 * (dy - dx);
        }
        putpixel(x, y, 2);
    }
    
    getch();
    closegraph();
}
```

Output:
![image](https://github.com/user-attachments/assets/96ab08a6-aec5-454c-b53b-b996bc0032b0)
![image](https://github.com/user-attachments/assets/01f615ac-9e78-42d2-a9bc-bcd7cb2b9002)


# Practical 10
## Write a program to scan convert a circle using Bresenham’s algorithm.

```c
#include<graphics.h> 
#include<stdlib.h> 
#include<stdio.h> 
#include<conio.h> 
#include<math.h>

void EightWaySymmetricPlot(int xc, int yc, int x, int y) {
    putpixel(x + xc, y + yc, RED); 
    putpixel(x + xc, -y + yc, YELLOW); 
    putpixel(-x + xc, -y + yc, GREEN); 
    putpixel(-x + xc, y + yc, YELLOW); 
    putpixel(y + xc, x + yc, 12); 
    putpixel(y + xc, -x + yc, 14); 
    putpixel(-y + xc, -x + yc, 15); 
    putpixel(-y + xc, x + yc, 6);
}

void BresenhamCircle(int xc, int yc, int r) {
    int x = 0, y = r, d = 3 - (2 * r); 
    EightWaySymmetricPlot(xc, yc, x, y); 
    
    while (x <= y) {
        if (d <= 0) {
            d = d + (4 * x) + 6;
        } else {
            d = d + (4 * x) - (4 * y) + 10; 
            y = y - 1;
        }
        x = x + 1; 
        EightWaySymmetricPlot(xc, yc, x, y);
    }
}

int main(void) {
    int xc, yc, r, gdriver = DETECT, gmode, errorcode; 
    initgraph(&gdriver, &gmode, "C:\\TURBOC3\\BGI"); 
    errorcode = graphresult();
    
    if (errorcode != grOk) { /* an error occurred */
        printf("Graphics error: %s\n", grapherrormsg(errorcode)); 
        printf("Press any key to halt: ");
        getch();
        exit(1);
    }
    
    printf("\n Write a program to scan convert a circle using Bresenham's Algorithm");
    printf("\n Rohit Parit 00313702022");
    printf("\n Enter the value of xc and yc: "); 
    scanf("%d%d", &xc, &yc);
    printf("\n Enter the value of radius: "); 
    scanf("%d", &r); 
    BresenhamCircle(xc, yc, r);
    
    getch(); 
    closegraph();
}
```

Output :
![image](https://github.com/user-attachments/assets/f77dfe08-ca0d-4aa7-a88e-d4824d8219fc)



# Practical 11
#### Cohen Sutherland Line Clipping Algorithm
**Description:** Yeh program Cohen-Sutherland line clipping algorithm ka implementation karta hai. Isme clipping window ka coordinate aur line segment ke starting aur ending points ko input liya jata hai.

```c
#include <graphics.h>
#include <conio.h>
#include <stdio.h>
#include <math.h>

void main() {
    int rcode_begin[4] = {0, 0, 0, 0}, rcode_end[4] = {0, 0, 0, 0}, region_code[4];
    int W_xmax, W_ymax, W_xmin, W_ymin, flag = 0;
    float slope;
    int x, y, x1, y1, i, gr = DETECT, gm;

    initgraph(&gr, &gm, "c:\\turboc3\\bgi");
    printf("\nRohit Parit   00313702022");
    printf("\n\nCohen Sutherland Line Clipping Algorithm:- ");
    printf("\n\nEnter xmin and ymin:- ");
    scanf("%d%d", &W_xmin, &W_ymin);
    printf("\nEnter xmax and ymax:- ");
    scanf("%d%d", &W_xmax, &W_ymax);
    printf("\nEnter initial point x and y:- ");
    scanf("%d%d", &x, &y);
    printf("\nEnter final point x and y:- ");
    scanf("%d%d", &x1, &y1);
    
    cleardevice();
    rectangle(W_xmin, W_ymin, W_xmax, W_ymax);
    line(x, y, x1, y1);
    line(0, 0, 600, 0);
    line(0, 0, 0, 600);

    if (y > W_ymax) { rcode_begin[0] = 1; flag = 1; }
    if (y < W_ymin) { rcode_begin[1] = 1; flag = 1; }
    if (x > W_xmax) { rcode_begin[2] = 1; flag = 1; }
    if (x < W_xmin) { rcode_begin[3] = 1; flag = 1; }
    if (y1 > W_ymax) { rcode_end[0] = 1; flag = 1; }
    if (y1 < W_ymin) { rcode_end[1] = 1; flag = 1; }
    if (x1 > W_xmax) { rcode_end[2] = 1; flag = 1; }
    if (x1 < W_xmin) { rcode_end[3] = 1; flag = 1; }

    if (flag == 0) {
        printf("No need of clipping as it is already in window");
    } else {
        flag = 1;
        for (i = 0; i < 4; i++) {
            region_code[i] = rcode_begin[i] && rcode_end[i];
            if (region_code[i] == 1) {
                flag = 0;
            }
        }
        if (flag == 0) {
            printf("\nLine is completely outside the window");
        } else {
            slope = (float)(y1 - y) / (x1 - x);
            if (rcode_begin[2] == 0 && rcode_begin[3] == 1) {
                y = y + (float)(W_xmin - x) * slope;
                x = W_xmin;
            }
            if (rcode_begin[2] == 1 && rcode_begin[3] == 0) {
                y = y + (float)(W_xmax - x) * slope;
                x = W_xmax;
            }
            if (rcode_begin[0] == 1 && rcode_begin[1] == 0) {
                x = x + (float)(W_ymax - y) / slope;
                y = W_ymax;
            }
            if (rcode_begin[0] == 0 && rcode_begin[1] == 1) {
                x = x + (float)(W_ymin - y) / slope;
                y = W_ymin;
            }
            if (rcode_end[2] == 0 && rcode_end[3] == 1) {
                y1 = y1 + (float)(W_xmin - x1) * slope;
                x1 = W_xmin;
            }
            if (rcode_end[2] == 1 && rcode_end[3] == 0) {
                y1 = y1 + (float)(W_xmax - x1) * slope;
                x1 = W_xmax;
            }
            if (rcode_end[0] == 1 && rcode_end[1] == 0) {
                x1 = x1 + (float)(W_ymax - y1) / slope;
                y1 = W_ymax;
            }
            if (rcode_end[0] == 0 && rcode_end[1] == 1) {
                x1 = x1 + (float)(W_ymin - y1) / slope;
                y1 = W_ymin;
            }
        }
    }

    delay(1000);
    clearviewport();
    rectangle(W_xmin, W_ymin, W_xmax, W_ymax);
    line(0, 0, 600, 0);
    line(0, 0, 0, 600);
    setcolor(RED);
    line(x, y, x1, y1);
    getch();
    closegraph();
}
```

Output : 
![image](https://github.com/user-attachments/assets/d27e6a22-81e7-45e0-8b88-0f00964fe8bc)
![image](https://github.com/user-attachments/assets/21740680-ace8-4e2b-a9e3-221a3a06c726)



# Practical 12
#### Write a program to get translation vector from the user and translate triangle accordingly.
```c
#include<conio.h>
#include<graphics.h>
#include<stdio.h>

void main()
{
    int gd = DETECT, gm;
    int x, y, x1, y1, x2, y2, tx, ty;
    
    initgraph(&gd, &gm, "C:\\TURBOC3\\BGI");

    printf("\n Write a program to get translation vector from the user and translate triangle accordingly.");
    printf("\n Rohit Parit 00313702022");
    
    printf("\n Enter first coordinates of the triangle: ");
    scanf("%d %d", &x, &y);
    printf("\n Enter the second coordinates of the triangle: ");
    scanf("%d %d", &x1, &y1);
    printf("\n Enter the third coordinates of the triangle: ");
    scanf("%d %d", &x2, &y2);
    
    printf("\n Triangle Before & After Translation:- \n");
    // Draw the original triangle
    line(x, y, x1, y1);
    line(x1, y1, x2, y2);
    line(x2, y2, x, y);
    
    printf("\n Enter the translation Vector (tx ty): ");
    scanf("%d %d", &tx, &ty);
    
    // Set color for translated triangle
    setcolor(RED);
    // Draw the translated triangle
    line(x + tx, y + ty, x1 + tx, y1 + ty);
    line(x1 + tx, y1 + ty, x2 + tx, y2 + ty);
    line(x2 + tx, y2 + ty, x + tx, y + ty);
    
    getch();
    closegraph();
}
```
Output : 
![image](https://github.com/user-attachments/assets/21465372-f42e-4d62-9892-1ae362d45609)


# Practical 13
#### Write a program to get rotational angle from the user and rotate triangle accordingly.
```c
#include <stdio.h>
#include <conio.h>
#include <graphics.h>
#include <math.h>

void DrawTriangle(int x1, int y1, int x2, int y2, int x3, int y3, int color);
void RotateTriangle(int x1, int y1, int x2, int y2, int x3, int y3, float angle);

int main()
{
    int gd = DETECT, gm;
    int x1, y1, x2, y2, x3, y3;
    float angle;

    initgraph(&gd, &gm, "C:\\TURBOC3\\BGI");

    printf("\n Write a program to get rotational angle from the user and rotate triangle accordingly.");
    printf("\n\n Rohit Parit 00313702022");
    printf("\n\n Enter the 1st point for the triangle (x1 & y1): ");
    scanf("%d%d", &x1, &y1);
    printf("\n Enter the 2nd point for the triangle (x2 & y2): ");
    scanf("%d%d", &x2, &y2);
    printf("\n Enter the 3rd point for the triangle (x3 & y3): ");
    scanf("%d%d", &x3, &y3);

    // Draw the original triangle in white
    DrawTriangle(x1, y1, x2, y2, x3, y3, WHITE);

    printf("\n Enter the angle for the rotation (in degrees): ");
    scanf("%f", &angle);

    // Draw the rotated triangle in a different color (e.g., RED)
    RotateTriangle(x1, y1, x2, y2, x3, y3, angle);

    getch();
    closegraph();
    return 0;
}

void DrawTriangle(int x1, int y1, int x2, int y2, int x3, int y3, int color)
{
    // Set the color for drawing the triangle
    setcolor(color);

    // Draw the triangle
    line(x1, y1, x2, y2);
    line(x2, y2, x3, y3);
    line(x3, y3, x1, y1);
}

void RotateTriangle(int x1, int y1, int x2, int y2, int x3, int y3, float angle)
{
    int p = x2, q = y2; // Pivot point for rotation
    float radianAngle = (angle * 3.14) / 180.0;

    // Calculate the new coordinates after rotation
    int a1 = p + (x1 - p) * cos(radianAngle) - (y1 - q) * sin(radianAngle);
    int b1 = q + (x1 - p) * sin(radianAngle) + (y1 - q) * cos(radianAngle);
    int a2 = p + (x2 - p) * cos(radianAngle) - (y2 - q) * sin(radianAngle);
    int b2 = q + (x2 - p) * sin(radianAngle) + (y2 - q) * cos(radianAngle);
    int a3 = p + (x3 - p) * cos(radianAngle) - (y3 - q) * sin(radianAngle);
    int b3 = q + (x3 - p) * sin(radianAngle) + (y3 - q) * cos(radianAngle);

    // Draw the rotated triangle in RED
    DrawTriangle(a1, b1, a2, b2, a3, b3, RED);
}
```

Output : 
![image](https://github.com/user-attachments/assets/dea2baca-e3a9-46fc-9bd2-ca30be6c2c5a)


# Practical 14
#### Write a Program to get scaling vector from the user and scale triangle accordingly.
```c
#include<stdio.h>
#include<conio.h>
#include<graphics.h>
#include<process.h>
#include<math.h>

int x1, y1, x2, y2, x3, y3;
int a1, a2, a3, b1, b2, b3;

void draw();
void scale();

void main()
{
    int gd = DETECT, gm;
    initgraph(&gd, &gm, "C:\\TURBOC3\\BGI");

    printf("\n Write a program to get scaling vector from the user and scale triangle accordingly.");
    printf("\n\n Rohit Parit 00313702022");
    printf("\n\n Enter the 1st point for the triangle: ");
    scanf("%d%d", &x1, &y1);
    printf("\n Enter the 2nd point for the triangle: ");
    scanf("%d%d", &x2, &y2);
    printf("\n Enter the 3rd point for the triangle: ");
    scanf("%d%d", &x3, &y3);
    
    draw();
    scale();
}

void draw()
{
    line(x1, y1, x2, y2);
    line(x2, y2, x3, y3);
    line(x3, y3, x1, y1);
}

void scale()
{
    int x, y;
    int mx, my;
    printf("\n Enter the scaling factors (x & y): ");
    scanf("%d%d", &x, &y);
    
    // Calculate the centroid of the triangle
    mx = (x1 + x2 + x3) / 3;
    my = (y1 + y2 + y3) / 3;

    // Clear the screen
    cleardevice();

    // Calculate new coordinates after scaling
    a1 = mx + (x1 - mx) * x;
    b1 = my + (y1 - my) * y;
    a2 = mx + (x2 - mx) * x;
    b2 = my + (y2 - my) * y;
    a3 = mx + (x3 - mx) * x;
    b3 = my + (y3 - my) * y;

    // Draw the scaled triangle
    line(a1, b1, a2, b2);
    line(a2, b2, a3, b3);
    line(a3, b3, a1, b1);
    
    // Redraw the original triangle
    draw();
    getch();
    closegraph();
}
```

Output :
![image](https://github.com/user-attachments/assets/7437fc22-cca5-4e8e-9202-8c155e647512)
![image](https://github.com/user-attachments/assets/71dc411c-1801-4422-b787-5499968f1dbb)
