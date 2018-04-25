# Json - JavaScript Object Notation

Learning Json


* http://www.json.org/
* https://classroom.udacity.com/courses/ud843/lessons/1335cf7d-bb4f-48c6-8503-f14b127d2abc/concepts/cf8cd625-1fef-4d03-991b-2808a3ddb47c#
* https://www.w3schools.com/js/js_json_intro.asp
* [JSONObject Android Developers](https://developer.android.com/reference/org/json/JSONObject.html?utm_source=udacity&utm_medium=course&utm_campaign=android_basics)
* [JSONArray Android Developers](https://developer.android.com/reference/org/json/JSONArray.html?utm_source=udacity&utm_medium=course&utm_campaign=android_basics)
* [Android - JSON Parser](http://www.tutorialspoint.com/android/android_json_parser.htm)



### Curly Braces
You can see that everything in this JSON shoe example is enclosed in a set of curly braces, indicating the whole thing can be treated as an object.

### Commas
The keys and values are separated by a colon character, and each key/value pair is separated by a comma character. Highlight each bit of code as they are mentioned JSON supports the basic data types that you find in most programming languages, such as numbers, strings, booleans, arrays, and objects. You can see a few of those data types in this example:

### Size Code
The first key called "size" has a value of 9.5, and you can tell the value is a number because there are no quotation marks around it.

### Wide Code
The "wide" key has a value of true, with no quotation marks. This indicates that the value is a boolean. Highlight country of origin If the number had quotes around it, then it would be a string. And a string is exactly what we find in the second key value pair, where it says "country-of-origin" and then the value is set to "usa".

### Style
The next item is "style", and the value of it is represented as an object, as indicated by the curly braces.

### Nested Values.
Inside of the style object, we can find two nested values: One for categories, and one for color. Coordinates is represented as an array with three values in the array.

Groups of values can be nested in this way, by using objects and arrays, and then you can place different data types inside of those containers.


    public class MainActivity extends Activity {
        public void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            setContentView(R.layout.activity_main);

            TextView output = (TextView) findViewById(R.id.textView1);
            String strJson = "
            {
			\"Employee\" :[
                {
				\"id\":\"01\",
				\"name\":\"Gopal Varma\",
				\"salary\":\"500000\"
                },
                {
				\"id\":\"02\",
				\"name\":\"Sairamkrishna\",
				\"salary\":\"500000\"
                },
                {
				\"id\":\"03\",
				\"name\":\"Sathish kallakuri\",
				\"salary\":\"600000\"
                }
			]
            } ";

            String data = "";
            try {
                JSONObject jsonRootObject = new JSONObject(strJson);

                //Get the instance of JSONArray that contains JSONObjects
                JSONArray jsonArray = jsonRootObject.optJSONArray("Employee");

                //Iterate the jsonArray and print the info of JSONObjects
                for (int i = 0; i < jsonArray.length(); i++) {
                    JSONObject JSONObject = jsonArray.getJSONObject(i);

                    in id = Integer.parseInt(jsonObject.optString("id").toString());
                    String name = jsonObject.optString("name").toString();
                    float salary = Float.parseFloat(jsonObject.optString("salary").toString());

                    data += "Node" + i + " : \n id= " + id + " \n Name= " + name + " \n Salary= " + salary + " \n";
                }
                output.setText(data);
            } catch (JSONException e) {
                e printStackTrace ();
            }
        }
    }
