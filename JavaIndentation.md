# Rules for Indentation in a code

## Variable Name


+ The variable names should be valid to the point.


> Eg :-

```  
String name 		(It is valid attribute name for the class Company)
String companyname 	(It is invalid attribute name for the class Company)
```
Because since we are creating a class for Company it’s obvious that the name variable defined in the scope of the class company contains the name of the company.

+ The variable names should be in Camel-Case :


> Eg :-

```
int errorCode 				is valid. 
int errorcode,ErrorCode,Errorcode 	are invalid.
```

## Class Name

+ The class name should follow “JAVA naming conventions” (In every new word in the class name the first character should be an upper-case).



> Eg :- For class containing “Company detail” the class name should be

```java
public class CompanyDetail {
/*
Class body
*/
}
```

+ The class name should be same as your file name.

## Method Name 

+ The method names should be relevant to the scenario and should be written in Camel-Case.


> Eg :-	For a method to create company.

```java
void createCompany() { //valid name	
/* method body */
}	

void CreateCompany() { //invalid name	
/* method body */
}     
```



## Proper Java Indentation

### Import statements :

+ Should add setting in editor to alphabetically sort the importing statements.


+ Should import same packages in contiguous lines without an interrupting blank space. 	


> Like :

```java
import com.krishagni.CRM.rest.Company;
import com.krishagni.CRM.rest.Factory;
import com.krishagni.CRM.rest.Dao.CompanyDao;
```

> Unlike :

```java
import com.krishagni.CRM.rest.Company;

import com.krishagni.CRM.rest.Factory;
import com.krishagni.CRM.rest.Dao.CompanyDao;
```

### Curly braces :


+ The curly braces used in any Class, Method, Loops and Statements should be in proper format for enhancing the readability of the code.



> Sample code showing proper curly brace usage
```
public String getName() {
return name;
}
```


> Sample code showing improper curly brace usage
```
public String getName() 
{
   	 Return name;
}
```


### Alignment :


+ The code must be aligned in the proper way keeping 4 spaces before any method or variables.


> Sample code with proper alignment

```java 	
public class Company {
    CompanyDao dao;
    Company comp = new Company();    
    
    public Factory getAddcomp() {
	        return addcomp;
    }
}
```

There should be proper spacing before and after an operator.


> Like :
int name = 10; 



> Unlike:
int name=10;



### Remove unwanted Spaces :


+ Spaces which are not needed should not be used, the code should be kept in compact size and in readable format.



### Line Length :


+ Maximum characters in a line should not be more than 120.



## XML, HTML Indentation


+ Before every tag two spaces need to be given to make it in standard format.


> Like :

```xml
<bean id = "dao" class = "com.krishagni.CRM.rest.Dao.CompanyDaoImpl">
  <property name = "sessionFactory" ref = "sessionFactory"> </property>
</bean>
```

> Unlike :

```xml
<bean id = "dao" class = "com.krishagni.CRM.rest.Dao.CompanyDaoImpl">
   	 <property name="sessionFactory" ref = "sessionFactory"></property>
</bean>
```


### For Hbm file :


+ While integrating the hibernate file with database the database name, table name, column name need to be in upper-case so that it can be differentiated with java object properties.  


> Something like this 

```xml
<id name = "id" type = "int">
  <column name = "ID" />
</id>
```

### Which helps us understand that id (java object property) is different from ID (Database column name)

