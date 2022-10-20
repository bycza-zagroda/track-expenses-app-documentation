
## 1
>The primitive types are much faster and require much less memory. Therefore, we might want to prefer using them.
> On the other hand, current Java language specification doesn’t allow usage of primitive types in the parameterized 
> types (generics), in the Java collections or the Reflection API.
>
> When our application needs collections with a big number of elements, we should consider using arrays with as more 
> “economical” type as possible.

[Baeldung - java-primitives-vs-objects](https://www.baeldung.com/java-primitives-vs-objects)


## 2
> In Joshua Bloch's - _Effective Java_, Item 5: "Avoid creating unnecessary objects", he posts the following code 
> example:

```java
    public static void main(String[] args) {
        Long sum = 0L; // uses Long, not long
        for (long i = 0; i <= Integer.MAX_VALUE; i++) {
            sum += i;
        }
        System.out.println(sum);
    }
```

>and it takes 43 seconds to run. Taking the Long into the primitive brings it down to 6.8 seconds... If that's any 
> indication why we use primitives.

>The lack of native value equality is also a concern (.equals() is fairly verbose compared to ==)

>for biziclop:

```java
class Biziclop {

    public static void main(String[] args) {
        System.out.println(new Integer(5) == new Integer(5));
        System.out.println(new Integer(500) == new Integer(500));

        System.out.println(Integer.valueOf(5) == Integer.valueOf(5));
        System.out.println(Integer.valueOf(500) == Integer.valueOf(500));
    }
}
```

>Results in:

```java
    false
    false
    true
    false
```

>Why does (3) return true and (4) return false?
>
>Because they are two different objects. The 256 integers closest to zero [-128; 127] are cached by the JVM, so they return the same object for those. Beyond that range, though, they aren't cached, so a new object is created. To make things more complicated, the JLS demands that at least 256 flyweights be cached. JVM implementers may add more if they desire, meaning this could run on a system where the nearest 1024 are cached and all of them return true... #awkward

> [Joshua Bloch's Effective Java](https://lubimyczytac.pl/ksiazka/4859222/java-efektywne-programowanie-wydanie-iii)


>I don't think there's a single correct answer. A few suggestions:

>   The biggest difference I see between long and Long in this context is that Long may be null. If there's a possibility you might have missing values, the Long object will be helpful as null can indicate missing values. If you're using primitives, you'll have to use some special value to indicate missing, which is probably going to be a mess. Speed or size is not likely to be an issue unless you're planning on making an array of a million of these things and then serializing.

>    My preference for validation logic is to throw some sort of custom ValidationException at the point at which the thing could fail. If you're just creating these things with a constructor, the simplest thing would be just to validate there, e.g.

```java
     public ClientInput(Long userid, Long clientid, Map<String, String> parameterMap, Long timeout_ms, boolean debug) throws ValidationException {          

          if (userid == null) throw new ValidationException("UserId is required"); 
                ...etc, etc...
    }
```
>Ultimately, the ValidationException is only useful if you can catch it at a point where you can do something useful with it - echo it back to a user or whatever.



## 4
[long-vs-integer-long-vs-int-what-to-use-and-when])(https://doraprojects.net/questions/5857812/long-vs-integer-long-vs-int-what-to-use-and-when)