---
title: "Adapter Pattern"
weight: 40
pre: "8. "
---

{{% youtube Ibxsanf8DFc %}}

[Video Materials](video)

Another pattern is the **adapter pattern**. The [adapter pattern](https://en.wikipedia.org/wiki/Software_design_pattern), which is a structural pattern that is used to make an existing interface fit within a different interface. Just like we might use an adapter when traveling abroad to allow our appliances to plug in to different electrical outlets around the world, the adapter pattern lets us use one interface in place of another, similar interface.

![Adapter Pattern](/cc410/images/12/adapter.jpg)[^1]

[^1]: https://commons.wikimedia.org/w/index.php?title=File:W3sDesign_Adapter_Design_Pattern_UML.jpg&oldid=438698227

In the UML diagram above, we see two different approaches to using the adapter pattern. First, we see the **object adapter**, which simply stores an instance of the object to be adapted, and then translates the incoming method calls (or messages) to match the appropriate ones available in the object it is adapting.

The other approach is the **class adapter**, which typically works by subclassing or inheriting the class to be adapted, if possible. Then, our code can call the operations on the adapter class, which can then call the appropriate methods in its parent class as needed. 

Let's look at a quick example to see how we can use the adapter pattern in our code.

### Example

Let's assume we have a `Pet` class that is used to record information about our pets. However, the original class was written to use metric units, and we'd like our program to use the United States customary units system instead. In that case, we could use the adapter pattern to adapt this class for our use. 

To make it simple, we'll assume that our `Pet` class includes attributes `weight`, measured in kilograms, as well as `age`, measured in years. Each of those attributes includes getters and setters in the `Pet` class.

#### Object Adapter

First, let's look at the adapter pattern using the **object adapter** approach. In this case, our adapter will store an instance of the `Pet` class as an object, and then use its methods to access methods within the encapsulated object.

{{< tabs >}}

{{% tab name="Java" %}}

```java
import java.lang.Math;

public class PetAdapter{

    private Pet pet;
    
    public PetAdapter() {
        this.pet = new Pet();
    }
    
    public int getWeight() {
        // convert kilograms to pounds
        return Math.round(this.pet.getWeight() * 2.20462);
    }
    
    public void setWeight(int pounds) {
        // convert pounds to kilograms
        this.pet.setWeight(Math.round(pounds * 0.453592));
    }
    
    public int getAge() {
        // no conversion needed
        return this.pet.getAge();
    }
    
    public void setAge(int years) {
        // no conversion needed
        this.pet.setAge(years);
    }

}
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
class PetAdapter:
    
    def __init__(self) -> None:
        self.__pet = Pet()
        
    @property
    def weight(self) -> int:
        # convert kilograms to pounds
        return round(self.__pet.weight * 2.20462)
    
    @weight.setter
    def weight(self, pounds: int) -> None:
        # convert pounds to kilograms
        self.__pet.weight = round(pounds * 0.453592)
        
    @property
    def age(self) -> int:
        # no conversion needed
        return self.__pet.age
    
    @age.setter
    def age(self, years: int) -> None:
        # no conversion needed
        self.__pet.age = years
```

{{% /tab %}}

{{< /tabs >}}

As we can see, we can easily write methods in our `PetAdapter` class that perform the conversions needed and call the appropriate methods in the `Pet` object contained in the class.

#### Class Adapter

The other approach we can use is the **class adapter** approach. Here, we'll inherit from the `Pet` class itself, and implement any updated methods. 

{{< tabs >}}

{{% tab name="Java" %}}

```java
import java.lang.Math;

public class PetAdapter extends Pet{
    
    public PetAdapter() {
        super();
    }
    
    @Override
    public int getWeight() {
        // convert kilograms to pounds
        return Math.round(super.getWeight() * 2.20462);
    }
    
    @Override
    public void setWeight(int pounds) {
        // convert pounds to kilograms
        super.setWeight(Math.round(pounds * 0.453592));
    }
    
    // Age methods are already inherited and don't need adapted

}
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
class PetAdapter(Pet):
    
    def __init__(self) -> None:
        super().__init__()
        
    @property
    def weight(self) -> int:
        # convert kilograms to pounds
        return round(super().weight * 2.20462)
    
    @weight.setter
    def weight(self, pounds: int) -> None:
        # convert pounds to kilograms
        super().weight = round(pounds * 0.453592)
        
    # Age methods are already inherited and don't need adapted
```

{{% /tab %}}

{{< /tabs >}}

In this approach, we override the methods that need adapted in our subclass, but leave the rest of them alone. So, since the `age` getter and setter can be inherited from the parent `Pet` class, we don't need to include them in our adapter class. 
