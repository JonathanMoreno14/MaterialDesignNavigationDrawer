# MaterialDesignNavigationDrawer
An exmaple of a navigation drawer using Material Design for Android


![materialdesignnavdrawer](https://cloud.githubusercontent.com/assets/11635523/20128011/6e504e82-a60a-11e6-8563-c31c6d1d111f.gif)


Currently there is only 1 activity for demonstration purposes. To add new acticities you will need to add them to the package **androidproject.com.materialdeisgnnavigationdrawer.activities**

The current activity is **Experience**

```java

   public class Experience extends AppCompatActivity {

      @Override
      protected void onCreate(Bundle savedInstanceState) {
          super.onCreate(savedInstanceState);
          setContentView(R.layout.activity_experience);
          getSupportActionBar().setDisplayHomeAsUpEnabled(true);
          getSupportActionBar().setDisplayShowTitleEnabled(true);
          getSupportActionBar().setTitle("Experience");

      }


      @Override
      public boolean onOptionsItemSelected(MenuItem item) {
          switch (item.getItemId()) {
              case android.R.id.home:
                  // app icon in action bar clicked; go home
                  Intent intent = new Intent(this, MainActivity.class);
                  intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
                  startActivity(intent);
                  return true;
              default:
                  return super.onOptionsItemSelected(item);
          }
      }


  }

```
To be more efficient I decided to use a *switch case* on the **MainActivity**

```java

   switch (item.getItemId()){

            case R.id.nav_about:

                return true;
            case  R.id.nav_experience:
                Intent myIntent = new Intent(MainActivity.this, Experience.class);
                startActivity(myIntent);

                return true;
            case R.id.nav_skill:

                return true;
            case R.id.nav_social:

                return true;
        }

```

For the *content_main* I added a **NestedScrollView** to the **app_bar_main.xml** this will allow the user to scroll up if there is more content to be viewed

```xml

    <android.support.v4.widget.NestedScrollView
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        app:layout_behavior="@string/appbar_scrolling_view_behavior"
        >

        <LinearLayout android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical">

            <include layout="@layout/content_main" />

        </LinearLayout>

    </android.support.v4.widget.NestedScrollView>

```

### Dependencies

```gradle

    compile 'com.android.support:appcompat-v7:23.4.0'
    compile 'com.android.support:design:23.4.0'
    compile 'com.android.support:cardview-v7:25.0.0'
    compile 'de.hdodenhof:circleimageview:2.1.0'

```


