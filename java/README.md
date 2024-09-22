# Java CheatSheet

## Array
### Stdout
1. print each item
    ```java
    list.forEach(System.out::println);
    ```
2. Use Stream to search and print

    Ex: 
    ```java
     public void printList(){
        Utils.clear();
        Utils.show("\n\t\t\t---------------------------------- IT Students ----------------------------------");
        String format = "%-10s | %-25s | %-20s | %-20s | %-20s | %-15s | %-7s | %-7s | %-10s";
        Utils.show(String.format(format, "ID", "FullName", "Street", "District", "City", "Country", "Java", "CSS", "AVG"));
        String separator = "+----------+--------------------------------+-----------------+----------------------+----------------------+-----------------+---------+---------+----------";
        Utils.show(separator);
        StudentList.stream()
                    .filter(student -> student.getId().toLowerCase().startsWith("it"))
                    .forEach(System.out::println);

        System.out.println("\n\n\t\t\t---------------------------------- Biz Students ----------------------------------");
        Utils.show(String.format(format, "ID", "FullName", "Street", "District", "City", "Country", "ACC", "MKT", "AVG"));
        Utils.show(separator);
        StudentList.stream()
                    .filter(student -> student.getId().toLowerCase().startsWith("bz"))
                    .forEach(System.out::println);
    }
    ```


### Find
1. Find Obj and save new ArrayList
    ```java
    public ArrayList<Object> find(Predicate<Object> obj){
        return list.stream()
                          .filter(obj)
                          .collect(Collectors.toCollection(ArrayList::new));
    }
    ```
2. Find object using loop and return the first match
    ```java
    public Object findFirst(Predicate<Object> predicate) {
        for (Object obj : list) 
            if (predicate.test(obj)) 
                return obj;
            
        return null; 
    }
    ```
3. Find <strong>all</strong> matches and return in a List without using streams
    ```java
    public ArrayList<Object> findAll(Predicate<Object> predicate) {
        ArrayList<Object> results = new ArrayList<>();
        for (Object obj : list) {
            if (predicate.test(obj)) {
                results.add(obj);
            }
        }
        return results;
    }
    ```
4. Find an object using binary search <strong>(List must be sorted)</strong>
    ```java
    public int findWithBinarySearch(Comparable<Object> key) {
        Collections.sort(list);
        return Collections.binarySearch(list, key);
    }
    ```
5. You can use the <strong>Stream API</strong> to implement complex filters and allow variable data
    ```java
    public List<Object> complexSearch(Predicate<Object> filter, Comparator<Object> comparator, Function<Object, Object> mapper) {
        return list.stream()
                .filter(filter)
                .sorted(comparator)
                .map(mapper)
                .collect(Collectors.toList());
    }
    ```

### Sort
1. Collections.sort() Function
    ```java
    public static <T> void sortListWithComparator(List<T> list, Comparator<T> comparator) {
        Collections.sort(list, comparator);
    }
    
    or

    public static <T> void sortListDirectly(List<T> list, Comparator<T> comparator) {
        list.sort(comparator);
    }
    ```
2. You can use the <strong>Stream API</strong> to implement complex filters and sorted data
    ```java
    public List<Object> complexSearch(Predicate<Object> filter, Comparator<Object> comparator, Function<Object, Object> mapper) {
        return list.stream()
                .filter(filter)
                .sorted(comparator)
                .map(mapper)
                .collect(Collectors.toList());
    }


