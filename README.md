networkmanager
==============

## Library for Android projects

This library offers an easy way to use asynchronous HTTP GET and POST
requests in your Android projects in Eclipse.

## Documentation

### NetworkManager

```java
public void makeRequest(final ResponseCallback responseCallback,
                        final String url,
                        final String jsonData);
```

Performs either a POST or a GET request.

__responseCallback__: An object that implements the ResponseCallback interface.  
__url__: The url to make the request to. E.g. "http://my-server.com/database/users".  
__jsonData__: The JSON data to send with the request. This value may be `null`.
              If `jsonData` is `null`, the request will be a GET request. If `jsonData`
              is an actual JSON string, the request will be a POST request with the
              JSON data as the POST body.

### ResponseCallback

```java
public void onSuccessCallback(int statusCode, String response);
```

Fired when the request was successfull.

__statusCode__: The status code of the response.  
__response__: The body of the response.

```java
public void onFailureCallback(int statusCode, String response);
```

Fired when the request failed.

__statusCode__: The status code of the response.  
__response__: The body of the response.


## Importing

 - Copy the jar file into the 'libs' or 'lib' folder. If it doesn't exist, create it in the root of your project.
 - Right click the jar file -> Build Path -> Add to Build Path

That's it!

## Usage

An example of how to use this library.

```java
import com.ocb.network.NetworkManager;
import com.ocb.network.ResponseCallback;

public class MainActivity extends Activity implements ResponseCallback {

    @Override
    public void onCreate(Bundle savedInstanceState) {
        // The usual.
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Create a NetworkManager instance.
        NetworkManager networkManager = new NetworkManager();

        // Make a POST request.
        networkManager.makeRequest(this,
                                   "http://my-server.com/database/users",
                                   "{\"name\":\"OCB\"}");

        // Make a GET request.
        networkManager.makeRequest(this,
                                   "http://my-server.com/database/users/OCB",
                                   null);
    }

    @Override
    public void onSuccessCallback(int statusCode, String response) {
        //TODO: implement.
    }

    @Override
    public void onFailureCallback(int statusCode, String response) {
        //TODO: implement.
    }
}
```
