# General (JAVA)

### Utility class -> Local Extension

If you have to extend an existing class to add extra operations, you may be tempted to use an utility class with static methods. 

For example DateUtils to perform formatting operations, or get the startOfDay of one concrete Date instance, etc...

Instead of using a utility class, consider using a Local Extension.

[Refactoring - Local Extension](http://refactoring.com/catalog/introduceLocalExtension.html)

### Number of returns

### Use Static Factory methods instead of Constructors

Item 1 in Effective Java
Example in class PenyaInfo.fromPenya(Penya penya)
