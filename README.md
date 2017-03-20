# Factory method, Transfer Object Pattern


 factory method  defines an interface for creating an object, but let subclasses decide which class to instantiate. Factory Method lets a    class defer instantiation to subclasses.
Defining a "virtual" constructor.

### Lets think about a problem :
A framework needs to standardize the architectural model for a range of applications, but allow for individual applications to define their own domain objects and provide for their instantiation.


### Some discussion:
Factory Method is to creating objects as Template Method is to implementing an algorithm. A superclass specifies all standard and generic behavior (using pure virtual "placeholders" for creation steps), and then delegates the creation details to subclasses that are supplied by the client.

Factory Method makes a design more customizable and only a little more complicated. Other design patterns require new classes, whereas Factory Method only requires a new operation.

## Structure :

The implementation of Factory Method discussed in the Gang of Four (below) largely overlaps with that of Abstract Factory. For that reason, the presentation in this chapter focuses on the approach that has become popular since

![1](https://cloud.githubusercontent.com/assets/25975155/24093340/929e1f3c-0d7d-11e7-8b7e-63c0b8241ab5.png) <br>

### Code Examples :

public interface ImageReader { <br>
    public DecodedImage getDecodedImage(); <br>
}<br>

public class GifReader implements ImageReader { <br>
    public GifReader( InputStream in ) { <br>
        // check that it's a gif, throw exception if it's not, then if it is decode it. <br>
    }<br>

    public DecodedImage getDecodedImage() { <br>
       return decodedImage; <br>
    }<br>
}<br>

public class JpegReader implements ImageReader { <br>
    //... <br>
}<br>

## Transfer Object Pattern :

The Transfer Object pattern is used when we want to pass data with multiple attributes in one shot from client to server. Transfer object is also known as Value Object. Transfer Object is a simple POJO class having getter/setter methods and is serializable so that it can be transferred over the network. It does not have any behavior. Server Side business class normally fetches data from the database and fills the POJO and send it to the client or pass it by value. For client, transfer object is read-only. Client can create its own transfer object and pass it to server to update values in database in one shot. Following are the entities of this type of design pattern.

Business Object - Business Service fills the Transfer Object with data.

Transfer Object - Simple POJO having methods to set/get attributes only.

Client - Client either requests or sends the Transfer Object to Business Object


## Implementation :

TransferObjectPatternDemo, our demo class, is acting as a client here and will use StudentBO and Student to demonstrate Transfer Object Design Pattern.
![transferobject_pattern_uml_diagram](https://cloud.githubusercontent.com/assets/25975155/24093500/5165297e-0d7e-11e7-8f7d-157e90ea2b78.jpg)

### Examples :

public class StudentVO { <br>
   private String name; <br>
   private int rollNo; <br>

   StudentVO(String name, int rollNo){ <br>
      this.name = name; <br>
      this.rollNo = rollNo; <br>
   }

   public String getName() { <br>
      return name; <br>
   }

   public void setName(String name) { <br>
      this.name = name; <br>
   }

   public int getRollNo() { <br>
      return rollNo; <br>
   }

   public void setRollNo(int rollNo) { <br>
      this.rollNo = rollNo; <br>
   }<br>
} <br>

