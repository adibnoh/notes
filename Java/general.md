# General

## Public

public means that the method will be visible from classes in other packages.

## Static

static means that the method is not attached to a specific instance, and it has no "this". It is more or less a function.

## Void

void is the return type. It means "this method returns nothing".

## Meaning of three dot

Can receive more than one object/String/int or etc

```java

public void myMethod(String... strings){
    for(String whatever : strings){
        // do what ever you want
    }

    // the code above is is equivalent to
    for( int i = 0; i < strings.length; i++){
        // classical for. In this case you use strings[i]
    }
}

```