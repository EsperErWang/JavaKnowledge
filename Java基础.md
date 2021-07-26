### Java基础

1. OOD: Encapsulation(封装), inheritance(继承), Polymorphism(多态), abstraction(抽象).

2. Boolean: 1, byte: 8, char: 16, short: 16, int: 32, float: 32, long: 64, double: 64. (bits)

3. Class instance = object.

4. Class: **Field**, **method**, **constructor**.

5. **Overload**, methods' argument lists must be different(number, type).

6. **override**, 

   1. @override can help to check if the super class has this method.  
   2. The override method name and argument lists should be the same as superclass's methods. 
   3. override methods' Access Modifiers should equal or larger than superclass methods, like superclass method is public, subclass's method must be public too.
   4. If a superclass's method Access Modifier is **private/static/ final**, it cannot be override.
   5. Constructor cannot be override.

7. **Encapsulation**(封装):

   1. The fields in class use **private**, and use get or set methods to change them.
   2. In one class, some methods are private, and other public methods use this private method. 

8. UML图：+public, -private, #protected 

9. In the constructor, **this** and **super** keyword must be the **first** line,  so can only choose one of them.

10. MVC: model(process data), view(show data), control(logic processing).

11. shallow clone means only copy the reference, deep clone means create a new instance and copy the content of the old object.

12. **inheritance**(继承): 

    1. subclass extend superclass. if superclass has fields which are private, subclass should use get or set to use them, if methods are private, subclass can not use them.
    2. subclass can only extends one superclass, a superclass can have multiple subclasses. But subclass can implement more interfaces.
    3. all classes are subclasses of Object class.

13. **Polymorphism**(多态):  Superclass's reference points to the subclass's Objects. 

    1. Can only use the methods in superclass, but the **methods** will execute subclass's **override** **methods**.  However, the **fields** will be the **superclass's**. **fields** will **not** be extended.
    2. A **same** method can have **different** implementation and behavior in subclass's objects. 
    3. **Polymorphism** is a running action, when JVM run to a method, then knows run which method(superclass's or subclass's) in subclass.
    4. abstract class and interface all express Polymorphism.

14. ==: address comparison: memory location. **Not care** about the types (float 51 == double 51 return true).

    Equals: content comparison: values in the objects. **Equals method must override**, because in Object class, equals method (return this == object;). toString() also need override, otherwise the output will be the object's memory address.

    ```java
    String a = new String("ab"); // a 为一个引用
    String b = new String("ab"); // b为另一个引用,对象的内容一样
    String aa = "ab"; // 放在常量池中
    String bb = "ab"; // 从常量池中查找
    aa == bb; // true
    a == b; // false，非同一对象
    a.equals(b);// true
    42 == 42.0; // true
    ```

15. The wrapper classes of  primitive types most implement constant pool technology and cache data in the range of [-128, 127].

    ```java
    Integer i1 = 33;
    Integer i2 = 33;
    i1 == i2; // true
    
    Integer i1 = 128;
    Integer i2 = 128;
    i1 == i2; // false
    
    Integer i1 = 33;
    Integer i2 = new Integer(33);
    i1 == i2; // false
    ```

    **So the comparison between  all integer wrapper objects, we need to use equals method** to check if the values are equals

16. **static**:

    1. for field, different objects for one class has **only one** same field. If change this field in one object, other objects will also be changed.
    2. non-static field will create when **object** create, static field will load when **class** **load**. static field belong to class but not objects, so do not need to create an object to use it.
    3. In static methods, can only use static methods and static fields, because it not depends on objects, **the method will load when class load, but non-static fields will exist after new a instance**. Or, already have other objects, then use objects' methods. 

17. **this and super belongs to object, static belongs to class, so in static method, we cannot use this and super.**

18. **code Block**: 

    1. Static block will run when class is loaded, usually run one time. Non-static block will run when object is created, can run several times.
    2. when create an object, **static** things(after all static things finish) -> **block** -> **constructor**, **superclass** -> **subclass**.  

19. **final keyword**:

    1. primitive field cannot be changed, other field cannot change reference to another object.
    2. the class cannot be extended.
    3. the method cannot be override.

20. **abstraction**: cannot initialize instance, but also has constructor and can has normal methods, subclass must override abstract methods.

21. **Interface**: 

    1. Can only has public final static fields or abstract methods.
    2. Cannot have constructors. 
    3. If a class not override all abstract methods when implement a interface, it should be an abstract class.

22. **abstraction** vs **Interface**:

    1. both cannot be initialized.
    2. both can be extended.
    3. all abstract methods need override
    4. abstract class must has instructor, interface can not has instructor.
    5. can only extend one abstract class but can implement more interfaces. 

23. Exception: 

    1. use try to pack code may throw exception, and the exception will only into the first catch part which matched. So the subclass should be written before superclass.
    2. finally part will always run even if catch parts have exceptions or **return** in try part and catch part. return in try part and catch part will run **after** all code in finally part is run.  so if finally part has return, cannot return try and catch parts things.
    3. exception can be solved by computer by catch part, but error cannot be solved. 

24. Program, process, thread:

    1. when a program is running, the running thing is process, one process can have multiple threads. 
    2. every thread has it's own virtual machine stack and  program counter register.
    3. for all thread, use only one method area and heap in a process.
    4. one core CPU can only run one thread in a time.

25. concurrency(并发) vs parallel(并行)：concurrency means one CPU do multiple things,  parallel means multiple CPUs do multiple things.

26. Threads safe: **synchronized** or **lock**. all locks must be the same lock. one lock can control multiple methods. synchronized methods will release the lock automatically, but lock should written by programmer. 

27. ways of **implementing thread**: 

    1. extends Thread class. not good. can only extend one class.  
    2. implement Runnable interface. Instantiating an interface gives a cleaner separation between your code and the implementation of threads.

28. **Thread Pool**: implement Runnable interface and then put the tasks in the pool, the pool can be created by Executors's subclass that is ThreadPoolExecutor. there are four kinds of pools, The Cached Thread Pool is normal, it's more flexible.  

29. thread communicate with each other by method notify() or notifyAll().

30. **thread life**: initialization, ready to run, running, block, dead.

31. deadlock: different threads occupy sources which other threads need and not give up the lock. 

32. **sleep** vs **wait**: 

    1. both can block threads.
    2. sleep is in thread class, wait is in object class.
    3. wait must be used in synchronized method or synchronized code block.
    4. wait will release the lock.
    5. 如何实现

33. String is a final class, String is a constant, cannot be changed, String saved in a **final** char array. when change a string, actually create a new string in method area. String s1 = "A" is different from String s1 = new String("A"), The second one create two new objects, one in heap, and reference to "A" in method area. first one reference to "A" directedly.  if method area already has "A", it will not create a new "A". if right part not directedly give the String(have variables like a + "A" (if a is final, it's a constant)), the left part will create a object in heap. 

34. String builder is thread unsafe but efficient than String buffer. both saved in a char array. array default capacity is 16, if need expand capacity, the capacity will be (old-capacity * 2) + 2.

    ```java
     String toLowerCase(); 
     String toUpperCase();
     String substring(int beginIndex, int endIndex);
     int indexOf(String str);
     String[] split(String regex);
     String[] toCharArray(); 
     String trim();(去除String前后空格)
    ```

35. ```java
    Arrays.sort(all, new Comparator() {
        @Override
        public int compare(Object o1, Object o2) {
            if (o1.getName() > o2.getName()) {
                return 1;
            }else if (o1.getName() < o2.getName()) {
                return -1;
            }else {
                return 0;
            }
        }
    });
    ```

36. Iterator can remove elements.(only in Set and List -> collection(interface),  not in map, all of them can use collections(tool class) methods). **Foreach loop use iterator to realize, but cannot use remove during loop.** Because foreach also use (while iter.hasNext(), iter.next()) to realize, but when remove element, it use **collections**' remove method but not **iterator's**, so the iterator does not know there is a element be deleted. then expectedModCount != modCount (修改次数, which means threads no safe, fail-fast), will throw ConcurrentModificationException. 

    ```java
    Iterator<Object> iter = coll.iterator();
    while(iter.hasNext()){
        Object obj = iter.next();
        if(obj.equals("Tom")){
            iter.remove();
        }
    }
    for (Iterator<Object> iter = coll.iterator(); iter.hasNext();) {
        Object obj = iter.next();
        if(obj.equals("Tom")){
            iter.remove();
        }
    }
    ```

37. For array, Iterator also use for loop to loop. but for(int a : A), the a is not in the A, it's a new variable, so change it will not change A's element. 

38. **ArrayList use array to realize; LinkedList use doubly linked list to realize**,both are thread no safe. Vector is thread safe. all of them implement List interface. 

    ```java
    Collections.sort(list, ());
    Collections.reverse(list);
    Arrays.sort(arr, ());
    Arrays.toString();
    ```

39. Both arraylist and linkedlist add or remove middle element, the time complexity is O(n), because arraylist should move elements, linkedlist should find the target.(except the first, arraylist is O(n), linkedlist is O(1));

40. ArrayList default capacity is 10, **and the 10 capacity is realize when add things into arraylist**, expand capacity will be old-capacity * 1.5, and copy all things into a new array.

41. list.remove(2) will delete element which index is 2, list.remove(new Integer(2)) will delete 2 in list.

42. Array vs ArrayList:

    1. array's length cannot change, arraylist will expand to 1.5 times when space is not enough.
    2. array can save primary type data and objects, arraylist can only save objects. 
    3. arraylist has more function like remove, add...array can only use index to get element, so array is more efficient.

43. Hashset use Hashmap to realize, for all key-value pair, value is a static new object. different object may has same hashcode, but same object(equals method return true, and all field used in equals method should all used in hashcode method too) must has same hashcode. **default capacity is 16, when surpass 0.75 * capacity, the capacity will * 2**.

44. **Hashmap first use key.hashcode() to get the position in the array, then use hashcode to compare, if their hashcode are same, then use equals method(TreeMap use compareTo method) compare all elements in that position, if not equals to any objects, it will save to that position's linked list's last position(or replace the value). So if want to put objects in these structure, must override hashcode method and equals or compare method of the class.** if we do not override the hashcode(), then two objects from this class will always have the different hashcode. 

45. HashMap and HashSet can both put null. HashMap and Hashtable both implement map interface, but hashmap is thread un safe but more efficient. Hashmap use **Entry[]** array to realize, if there is a confliction, it use linkedlist to save more elements; if linkedlist length > 8 and array length > 64, it will change to red-black tree.

46. In hashmap, keys are distinct, and the elements are Entry(in a set ) objects, which has key(in a **set**)-value(in a **collections**) pair. 

    ```JAVA
    key : map.keySet()			Collection<> map.values()			Map.Entry<> entry : map.entrySet()
    ```

47. wildcard(通配符) object can always read, but cannot write new things in it except null. List<?>.

48. the operation of connect database or read data from file, we need to close the connection manually, because JVM will not help us to close them.

49. If a class object want to transfer, this class need to implement **serializable** interface, and provide a static **serialVersionUID**, all object in this class also should be serializable. String already implement serializable. Cannot serialize fields which has static or transient.

50. IP and port: 端口, combine them to a socket; 

    Protocol：协议 ; 

    DNS：域名解析，map IP to Domain Name.

51. Arrays.asList() can only use to the array's type not primitive, like String[] array, but not int[] array.

    ```java
    String[] myArray = {"a", "b", "c"};
    List list = new ArrayList<>(Arrays.asList(myArray))
    ```

    Because the list obtained by Arrays.asList() is also a array, we cannot add things to this list directly, so we need to create a new list and put the content in it. 

52. There are two common method for keyboard to type in: Scanner or BufferedReader.

53. Character stream can avoid Garbled code(乱码, like transfer words), can instead byte stream(for pictures or videos).

54. A class loading to cash is also a object of Class class. when create a object, it always need use the constructor.

55. 反射总是需要获得Class类的一个对象class，方法有

    ```java
    一个具体的类：person.class; 
    已经得到某个类的实例：Object.getclass();
    已知一个类的类名：Class.forName(“java.lang.String”);
    ```

56. for **dynamic proxy**, 我们是为了实现代理被代理类的一些功能，所以功能可以写在接口里。然后利用反射得到被代理对象所实现的接口，代理类可以去动态的创建一个接口对象以实现被代理类的功能，代理对象执行的方法实际上就是通过invoke执行了目标对象对应的方法，传入的参数也是给了目标方法。p664

