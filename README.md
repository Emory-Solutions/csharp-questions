# C# Questions

### 1.
```c#
public string BuildReport(List<string> logs) {
    string report = "";
    foreach (var log in logs) {
        report += log + "\n";
    }
    return report;
}
```
Question: If logs contains 10,000 entries, why is this code inefficient? What tool should you use instead?

---

### 2.
```c#
var items = dbContext.Products.Where(p => p.Price > 100);
if (CheckCondition()) {
    items = items.OrderBy(p => p.Name);
}
var finalResult = items.ToList();
```
Question: When is the SQL query actually executed against the database? How many times is the database hit?

---

### 3.
```c#
try {
    ProcessData();
}
catch (Exception ex) {
    Log(ex);
    throw ex; 
}
```
Question: What will be the StackTrace when throw ex; is called?

---

### 4.
```c#
public async Task ProcessData() {
    var data = FetchDataAsync(); 
    Console.WriteLine(data.Result);
}
```
Question: Identify two issues with how the asynchronous method is being consumed here.

---

### 5.
```c#
public class User {
    public int Id { get; set; }
    public string Name { get; set; }
}
// ... later ...
var set = new HashSet<User>();
set.Add(new User { Id = 1, Name = "Alice" });
bool exists = set.Contains(new User { Id = 1, Name = "Alice" });
```
Question: What is the value of exists, and why?

---

### 6.
```c#
public struct LargeData {
    public decimal Price;
    public Guid Id;
    public DateTime Created;
    // ... 10 more fields ...
}

public void Process(LargeData data) { 
    /* logic */ 
}
```
Question: If this method is called millions of times in a loop, what is the performance concern? How would you optimize the parameter?

---

### 7.
```c#
private static readonly object _syncRoot = new object();

public async Task AccessSharedResource() {
    lock (_syncRoot) {
        await Task.Delay(100); // Do async work
    }
}
```
Question: Will this code compile?
