# Inversion of Control (IoC)

```
The approach of outsourcing the construction and management of objects.
```

## Problem

In our application MyAPP, we have multiple coach such as BaseballCoach, TrackCoach and we wanted to use these coach from our application. Following is an implmentation.

_Coach.java_
```
package com.masterspringboot.springdemo;

public interface Coach {
	
	public String getDailyWorkout();
}
```

_BaseballCoach.java_
```
package com.masterspringboot.springdemo;

public class BaseballCoach implements Coach {
	
	@Override
	public String getDailyWorkout() {
		return "Spend 30 minutes on batting practice";
	}
}
````

_TrackCoach.java_
```
package com.masterspringboot.springdemo;

public class TrackCoach implements Coach {

	@Override
	public String getDailyWorkout() {
		return "Run a hard 5k";
	}

}
```

_MyApp.java_
```
package com.masterspringboot.springdemo;

public class MyApp {

	public static void main(String[] args) {
		
		// create the object
		Coach theCoach = new TrackCoach();
		
		// use the object
		System.out.println(theCoach.getDailyWorkout());
	}

}
```

**Here, MyApp isn't configurable and TrackCoach or BaseballCoach need to hardcode to create its instance**
 
## Solution

+ Spring provides an _object factory_ to create an object based on a configuration file or annotation. Spring will give the appropriate implementation.

