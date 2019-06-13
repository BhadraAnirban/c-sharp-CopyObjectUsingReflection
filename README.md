
# In C#, Copy all the property values of an object to another object using Reflection and Generics

## You have to call the CopyGenericEntity method and pass your old and new object.
## All the values of all the properties in old object will be copied into new object.

Class MyClass {
  public string Name {get; set;}
  public int Age {get; set;}
}

### public void GetNewObject()
{
  MyClass oldEntity = new MyClass();
  oldEntity.Name = "PMKJ";
  oldEntity.Age = 26;
  
  MyClass newEntity = new MyClass();
  newEntity = CopyGenericEntity<MyClass>(oldEntity, newEntity);
}



public T CopyGenericEntity<T>(T oldObject, T newObject)
{
    var pi = typeof(T).GetProperties();
    foreach(var prop in pi)
    {
        PropertyInfo propertyInfo = newObject.GetType().GetProperty(prop.Name);
        propertyInfo.SetValue(newObject, prop.GetValue(oldObject, null));
    }
    return newObject;
}
###
