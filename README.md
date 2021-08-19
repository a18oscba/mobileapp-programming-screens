To create an additional activity, after creating the class you have to add it to the manifest file by adding the following line of code.
```
  <activity android:name=".SecondActivity"></activity>
```
For the created activity an xml file is needed. The activity_second.xml is created and looks like.
```
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:paddingBottom="10dp"
    android:paddingTop="10dp"
    android:paddingLeft="10dp"
    android:paddingRight="10dp"

    tools:context=".SecondActivity"
    tools:showIn="@layout/activity_second">
```
The java file for the class looks like.
```
public class SecondActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_second);
    }

}
```
To use the second activity we have to get there.
An easy way to do that is creating a button which on click navigates you to the decided destination through actionlistener.
The activity_main.xml file for the button on the main page looks like the following.
```
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">


    <Button
        android:id="@+id/GoToActivity2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Open Activity"
        android:visibility="visible" />

</RelativeLayout>
```
The java file which has the actionlistener looks like.
```
protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        button = (Button) findViewById(R.id.GoToActivity2);
        button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                openActivity2();
            }
        });

    }
    public void openActivity2(){
        Intent intent = new Intent(this, SecondActivity.class);
        startActivity(intent);
    }
```
If the id of the button is GoToActivity2 which is the button I created, then we want to call the function openActivity2() which sends us to Secondactivity.class when executed.
Now to create the fragment in the SecondActivity we add it to the xml file connected to that class. The fragment code in activity_second.xml looks like.
```

    <androidx.fragment.app.FragmentContainerView
        android:id="@+id/fragment_view"
        android:name="com.example.screens.ActivityFragment"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        />
```
The tas was to add something to the fragment. fragment_activity is the xml file connected to thefragment. In there I simply add the widgets like I've done in previous tasks and the code looks liek the following.
```
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    tools:context=".ActivityFragment"
    android:background="@android:color/darker_gray">

    <!-- TODO: Update blank fragment layout -->
    <androidx.constraintlayout.widget.ConstraintLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        >


        <ProgressBar
            android:id="@+id/progressBar"
            style="?android:attr/progressBarStyleHorizontal"
            android:layout_width="150dp"
            android:layout_height="wrap_content"
            android:layout_margin="50dp"
            android:layout_marginTop="293dp"
            android:layout_marginEnd="211dp"
            android:layout_marginRight="211dp"
            android:layout_marginBottom="345dp"
            app:layout_constraintBottom_toTopOf="@+id/button"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toTopOf="parent" />

        <Button
            android:id="@+id/button"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="197dp"
            android:layout_marginBottom="272dp"
            android:text="Normal Button"
            app:layout_constraintBottom_toBottomOf="parent"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toBottomOf="@+id/progressBar" />

    </androidx.constraintlayout.widget.ConstraintLayout>

</FrameLayout>
```

