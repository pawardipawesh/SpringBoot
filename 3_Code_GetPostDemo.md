# MvcArgPassingApplication.java
```
package com.spring.training.MVCArgPassing;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class MvcArgPassingApplication {

	public static void main(String[] args) {
		SpringApplication.run(MvcArgPassingApplication.class, args);
	}
}
```

# LoginController.java
```
package com.spring.training.MVCArgPassing.Controller;

import org.springframework.stereotype.Controller;
import org.springframework.ui.ModelMap;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.RequestParam;

@Controller
public class LoginController {
	@RequestMapping(value="/login", method = RequestMethod.GET)
	public String login(ModelMap model){
		
		return "login";
	}
	
	@RequestMapping(value="/login", method = RequestMethod.POST)
	public String loginPost(ModelMap model,@RequestParam String name,@RequestParam String password){
		
		model.put("name", name);
		
		if(password.equals("Kavita"))
			return "welcome";
		else
			return "error";
	}
}
```

# src\main\resources\application.properties
```
spring.mvc.view.prefix=/WEB-INF/jsp/
spring.mvc.view.suffix=.jsp
logging.level.spring.framework.web=debug
```

# src\main\webapp\WEB-INF\jsp\login.jsp
```
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Welcome Page</title>
</head>
<body>
<form method="post">
	Name : <input type ="text" name = "name"/>
	Password : <input type = "password" name ="password"/>
	<input type = "submit" />
	</form>
</body>
</html>
```

# src\main\webapp\WEB-INF\jsp\welcome.jsp
```
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Welcome Page</title>
</head>
<body>
welcome ${name}</body>
</html>
```

# \src\main\webapp\WEB-INF\jsp\error.jsp
```
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Error Page</title>
</head>
<body>
Something went wrong!
 </body>
</html>
```

