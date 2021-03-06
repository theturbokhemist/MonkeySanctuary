## Overview
The goal of this project is to help the Jungle Friends Primate Sanctuary upgrade from a paper-based record system to a computer-based one. Here I have designed and implement a digital animal inventory system that keeps track of the location and needs of each monkey in the sanctuary.

## Features List
1. Function that describes the location of each monkey in the sanctuary.
2. Function that describes the location of each species in the sanctuary.
3. Function that calculates the type and amount of daily food needed to feed all the monkeys.
4. Function that prints signs with identifying information (name, age, etc) about each monkey in each housing unit. 

## How To Run
In order to run the .jar file, execute the following command in a command-line window:

```bash
java -jar sanctuary.jar
```
## How to Use

Initialize the sanctuary with an isolation capacity.
```java
Sanctuary sanctuary = new Sanctuary(2)
```

Add some enclosures with your choice of capacity.
```java
sanctuary.addEnclosure(20)
sanctuary.addEnclosure(15)
```

Add some monkeys to the sanctuary.
```java
sanctuary.newMonkey(new Monkey("Newton", MonkeyEnum.SPIDER, 43, SexEnum.MALE, 50, Food.FRUITS));
sanctuary.newMonkey(new Monkey("Leibniz", MonkeyEnum.HOWLER, 46, SexEnum.MALE, 19, Food.EGGS));
```

Move some monkeys around.
```java
sanctuary.isolationToEnclosure(“Newton”);
sanctuary.isolationToEnclosure(“Leibniz”);
sanctuary.enclosureToIsolation("Newton");
sanctuary.transferMonkey("Newton"); 
```

Get some info about the monkeys

```java
System.out.println(sanctuary.getMonkeyLocations()); //get list of monkey locations
System.out.println(sanctuary.getSpeciesLocations()); //get list of species location
System.out.println(sanctuary.getShoppingList()); //get shopping list
System.out.println(sanctuary.getHousingInfo(“Isolation”)); //get info about specific housing unit
```

## Design Changes
Earlier designs of this records system used an abstract class and many unnecessary getter methods. The final design included an additional Enum class to select the monkey sex and an interface that the sanctuary class implemented. The abstract class was removed because there was not enough duplicate code between housing class implementations to justify it. Finally, many unnecessary methods were removed or consolidated to better reflect SOLID design principles.


## Assumptions
One of the assumptions I made is that a sanctuary won’t have more than one isolation unit.

## Limitations
My design and implementation has the following limitations:
1. Monkey information such as their age and size can’t be updated directly. One would have to first remove the monkey from the sanctuary and then add it again with the updated characteristics.
2. Users can’t specify which enclosure to move a monkey to. This is a feature I would plan to add in future versions.