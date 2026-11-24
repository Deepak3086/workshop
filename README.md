# Addition of Two Numbers: Android App

A simple Android app that takes two numbers as input and displays their sum in a result text box.
Built with **Android Studio** and **Java** (Workshop 01).

## Features
- Accepts integers, decimals and negative numbers
- Displays the sum in a read-only result box
- Input validation (empty fields and invalid numbers)
- Whole-number results are shown without `.0` (e.g. `20` instead of `20.0`)

## Tech Stack
- Java
- XML (Views)
- Android Studio

## How to Run
1. Clone the repo:
   ```bash
   git clone <your-repo-url>
   ```
2. Open the folder in **Android Studio**.
3. Let Gradle sync finish.
4. Click **Run ▶** on an emulator or a USB-connected phone.

## Usage
1. Enter the first number.
2. Enter the second number.
3. Tap **Add** to see the result.

## Example
| Input 1 | Input 2 | Result |
|---------|---------|--------|
| 12      | 8       | 20     |
| 2.5     | 3.1     | 5.6    |
| -4      | 10      | 6      |

## Code 

## activity_xml:
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="24dp"
    android:gravity="center_horizontal">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Addition of Two Numbers"
        android:textSize="24sp"
        android:textStyle="bold"
        android:layout_marginBottom="32dp" />

    <EditText
        android:id="@+id/etNum1"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter first number"
        android:inputType="numberDecimal|numberSigned" />

    <EditText
        android:id="@+id/etNum2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter second number"
        android:inputType="numberDecimal|numberSigned"
        android:layout_marginTop="16dp" />

    <Button
        android:id="@+id/btnAdd"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Add"
        android:layout_marginTop="24dp" />

    <EditText
        android:id="@+id/etResult"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Result"
        android:focusable="false"
        android:cursorVisible="false"
        android:layout_marginTop="24dp" />

</LinearLayout>
```
## mainactivity.java

```
package com.example.additionapp;   // keep your own package name

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    EditText etNum1, etNum2, etResult;
    Button btnAdd;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        etNum1 = findViewById(R.id.etNum1);
        etNum2 = findViewById(R.id.etNum2);
        etResult = findViewById(R.id.etResult);
        btnAdd = findViewById(R.id.btnAdd);

        btnAdd.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String s1 = etNum1.getText().toString().trim();
                String s2 = etNum2.getText().toString().trim();

                if (s1.isEmpty() || s2.isEmpty()) {
                    Toast.makeText(MainActivity.this,
                            "Please enter both numbers", Toast.LENGTH_SHORT).show();
                    return;
                }

                try {
                    double a = Double.parseDouble(s1);
                    double b = Double.parseDouble(s2);
                    double sum = a + b;

                    // Show whole numbers without ".0"
                    if (sum == (long) sum) {
                        etResult.setText(String.valueOf((long) sum));
                    } else {
                        etResult.setText(String.valueOf(sum));
                    }
                } catch (NumberFormatException e) {
                    Toast.makeText(MainActivity.this,
                            "Invalid number", Toast.LENGTH_SHORT).show();
                }
            }
        });
    }
}
```

## Output:

<img width="1210" height="1125" alt="image" src="https://github.com/user-attachments/assets/89af9a69-ea10-40c4-9f46-e68634507448" />

