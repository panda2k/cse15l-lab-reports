# Lab Report 2
## Part 1: StringServer
### Code
```
import java.io.IOException;
import java.net.URI;
import java.lang.StringBuilder;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    StringBuilder sb = new StringBuilder();

    public String handleRequest(URI url) {
        if (url.getPath().contains("/add-message")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                sb.append(parameters[1]);
                sb.append("\n");
                return sb.toString();
            }
        } 

        return "404 Not Found!";
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
### Add Message Functionality
![Message 1](https://cdn.discordapp.com/attachments/639543567521415171/1068282498167078952/image.png)
`handleRequest` is called and it requires the `url` parameter and the stringbuilder
`sb` that is defined in the `Handler` class. At the time,
`sb` is empty. The `url` parameter has the path value of `add-message` and the query value of `s=hi1`.

The `url` parameter's `getQuery()` method is called to
extract the `s` parameter, which contains the string to add. `sb.append(parameters[1])` is called
which adds the string `hi1` to `sb`. It also adds a new line delimiter after. It then
returns the string representation of `sb` which contains the current and past 
strings. Since there are no previous strings, `sb.toString()` returns `hi1\n`

![Message 2](https://cdn.discordapp.com/attachments/639543567521415171/1068283538467733645/image.png)
`handleRequest` is called and it requires the `url` parameter and the stringbuilder
`sb` that is defined in the `Handler` class. At the time,
`sb` has the string `hi1\n`. The `url` parameter has the path value of `add-message` and the query value of `s=hi2`.

The `url` parameter's `getQuery()` method is called to
extract the `s` parameter, which contains the string to add. `sb.append(parameters[1])` is called
which adds the string `hi2` to `sb`. It also adds a new line delimiter after. It then
returns the string representation of `sb` which contains the current and past 
strings. Since the previous request added `hi1`, `sb.toString()` returns `hi1\nhi2\n`

## Part 2: Lab 3 Bugs:  `testReverseInPlace`
### Failure Inducing Input
```
@Test 
public void testReverseInPlace() {
    int[] input1 = { 3, 4, 5 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 5, 4, 3 }, input1);
}
```
### Working Input 
```
@Test
public void testReverseInPlace() {
    int[] input1 = {3};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
}
```
### Symptom
![Error](https://cdn.discordapp.com/attachments/639543567521415171/1068290096928919602/image.png)
Trying to reverse the array `[3,4,5]` returns `[5,4,5]`, but reversing the 
single element array `[3]` correctly returns `[3]`. It seems like arrays 
are reflected instead of reversed.
### The Bug
#### Code Before
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
        arr[i] = arr[arr.length - i - 1];
    }
}
```
Before, the function looped through the array and at each point in the array,
it set the current index to the reverse index's value. However, this doesn't
work because the index's original value is lost, causing any array with 
more than 1 element to become reflected instead of reversed.

#### Code After
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length / 2; i += 1) {
        int tmp = arr[i];
        arr[i] = arr[arr.length - i - 1];
        arr[arr.length - i - 1] = tmp; 
    }
}
```
I rewrote the function to swap array values and only loop through the first half
of the array. The original value gets saved as `tmp` and then each index and its
reverse index's value are swapped. I only need to loop through the first 
half of values because swapping only needs to be done once for each pair of
values.

## Part 3: What I learned
In week 2's lab, I learned how url queries worked. Before, I had no idea what 
the `?` in the url signified. Furthermore, I learned how to implement 
url queries for my own uses. For example, through my 
`SearchEngine` implementation, I learned how I could check for the url parameter
`s` and store its value in an arraylist. 

