---
title: "Usar correcciones de compatibilidad (shim) para aislar la aplicación de otros ensamblados para la prueba unitaria | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: d9df35f6ace396d1f2859ea7f5a16033c1739b16
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing"></a>Usar correcciones de compatibilidad (shim) para aislar la aplicación de otros ensamblados para la prueba unitaria
Los **tipos de correcciones de compatibilidad (shim)** son una de las dos tecnologías que usa el marco Microsoft Fakes para permitir aislar fácilmente del entorno los componentes que se están probando. Las correcciones de compatibilidad desvían las llamadas a métodos específicos hacia el código que se escribe como parte de la prueba. Muchos métodos devuelven resultados diferentes según las condiciones externas, pero una corrección de compatibilidad está bajo el control de la prueba y puede devolver resultados coherentes en cada llamada. De esta forma, es mucho más fácil escribir las pruebas.  
  
 Utilice las correcciones de compatibilidad para aislar el código de los ensamblados que no forman parte de la solución. Para aislar los componentes de la solución, se recomienda que use códigos auxiliares.  
  
 Para obtener una visión general y una guía de inicio rápido, vea [Aislar el código probado con Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).  
  
 **Requisitos**  
  
-   Visual Studio Enterprise  
  
 Vea un [vídeo (1 h 16 min): Testing Un-testable Code with Fakes in Visual Studio 2012](http://go.microsoft.com/fwlink/?LinkId=261837) (Comprobación de código difícil de comprobar con Fakes en Visual Studio 2012)  
  
## <a name="in-this-topic"></a>En este tema  
 En este tema obtendrá información sobre lo siguiente:  
  
 [Ejemplo: El error Y2K](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Example__The_Y2K_bug)  
  
 [Usar correcciones de compatibilidad (shim)](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Fakes_requirements)  
  
-   [Agregar ensamblados de Fakes](#AddFakes)  
  
-   [Usar ShimsContext](#ShimsContext)  
  
-   [Escribir pruebas con correcciones de compatibilidad (shim)](#WriteTests)  
  
 [Correcciones de compatibilidad (shim) para los diferentes tipos de métodos](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Shim_basics)  
  
-   [Métodos estáticos](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Static_methods)  
  
-   [Métodos de instancia (para todas las instancias)](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Instance_methods__for_all_instances_)  
  
-   [Métodos de instancia (para una instancia en tiempo de ejecución)](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Instance_methods__for_one_instance_)  
  
-   [Constructores](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Constructors)  
  
-   [Miembros base](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Base_members)  
  
-   [Constructores estáticos](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Static_constructors)  
  
-   [Finalizadores](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Finalizers)  
  
-   [Métodos privados](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Private_methods)  
  
-   [Interfaces de enlace](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Binding_interfaces)  
  
 [Cambiar el comportamiento predeterminado](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Changing_the_default_behavior)  
  
 [Detectar accesos al entorno](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Detecting_environment_accesses)  
  
 [Simultaneidad](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Concurrency)  
  
 [Llamar al método original desde el método de la corrección de compatibilidad (shim)](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Calling_the_original_method_from_the_shim_method)  
  
 [Limitaciones](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Limitations)  
  
##  <a name="BKMK_Example__The_Y2K_bug"></a> Ejemplo: El error Y2K  
 Consideremos un método que produce una excepción el 1 de enero de 2000:  
  
```csharp  
// code under test  
public static class Y2KChecker {  
    public static void Check() {  
        if (DateTime.Now == new DateTime(2000, 1, 1))  
            throw new ApplicationException("y2kbug!");  
    }  
}  
  
```  
  
 Comprobar este método es especialmente problemático, ya que el programa depende de `DateTime.Now`, un método que depende del reloj del equipo, un método dependiente del entorno y no determinista. Además, `DateTime.Now` es una propiedad estática, por lo que no se puede usar aquí un tipo de código auxiliar. Este problema es síntoma de un problema de aislamiento en las pruebas unitarias: es difícil realizar pruebas unitarias con programas que llaman directamente a las API de base de datos, se comunican directamente con los servicios web y similares, porque su lógica depende del entorno.  
  
 En estos casos es donde se deben usar tipos de corrección de compatibilidad. Los tipos de corrección de compatibilidad proporcionan un mecanismo para desviar cualquier método .NET a un delegado definido por el usuario. Los tipos de corrección de compatibilidad se generan por código mediante el generador de Fakes y usan delegados, lo que llamamos tipos de corrección de compatibilidad, para especificar nuevas implementaciones del método.  
  
 Las siguientes pruebas muestran cómo usar el tipo de corrección de compatibilidad, `ShimDateTime`, para proporcionar una implementación personalizada de DateTime.Now:  
  
```csharp  
//unit test code  
// create a ShimsContext cleans up shims   
using (ShimsContext.Create()  
    // hook delegate to the shim method to redirect DateTime.Now  
    // to return January 1st of 2000  
    ShimDateTime.NowGet = () => new DateTime(2000, 1, 1);  
    Y2KChecker.Check();  
}  
  
```  
  
##  <a name="BKMK_Fakes_requirements"></a> Cómo usar correcciones de compatibilidad (shim)  
  
###  <a name="AddFakes"></a> Agregar ensamblados de Fakes  
  
1.  En el Explorador de soluciones, expanda **Referencias** en el proyecto de prueba unitaria.  
  
    -   Si está trabajando en Visual Basic, debe seleccionar **Mostrar todos los archivos** en la barra de herramientas del Explorador de soluciones para ver la lista de referencias.  
  
2.  Seleccione el ensamblado que contiene las definiciones de clases para las que desea crear las correcciones de compatibilidad. Por ejemplo, si desea realizar una corrección de compatibilidad para DateTime, seleccione System.dll  
  
3.  En el menú contextual, seleccione **Agregar ensamblado de Fakes**.  
  
###  <a name="ShimsContext"></a> Usar ShimsContext  
 Al utilizar tipos de corrección de compatibilidad en un marco de pruebas unitarias, debe contener el código de prueba en un `ShimsContext` para controlar la duración de las correcciones de compatibilidad. Si no incluyéramos este requisito, sus correcciones de compatibilidad durarían hasta el cierre de AppDomain. La manera más fácil de crear un `ShimsContext` es usar el método estático `Create()`, tal como se muestra en el código siguiente:  
  
```csharp  
//unit test code  
[Test]  
public void Y2kCheckerTest() {  
  using(ShimsContext.Create()) {  
    ...  
  } // clear all shims  
}  
  
```  
  
 Esto es fundamental para eliminar correctamente el contexto de cada corrección de compatibilidad. Como regla general, llame siempre a `ShimsContext.Create` dentro de una instrucción `using` para asegurarse de borrar correctamente las correcciones de compatibilidad registradas. Por ejemplo, puede registrar una corrección de compatibilidad para un método de prueba que reemplaza el método `DateTime.Now` con un delegado que siempre devuelve el uno de enero de 2000. Si se olvida de borrar la corrección de compatibilidad registrada en el método de prueba, el resto de la ejecución de prueba devolverá siempre el uno de enero de 2000 como valor de DateTime.Now. Esto puede tener efectos inesperados y sorprendentes.  
  
###  <a name="WriteShims"></a> Escribir pruebas con correcciones de compatibilidad (shim)  
 En el código de prueba, inserte un *desvío* para el método que quiera imitar. Por ejemplo:  
  
```csharp  
[TestClass]  
public class TestClass1  
{   
        [TestMethod]  
        public void TestCurrentYear()  
        {  
            int fixedYear = 2000;  
  
            using (ShimsContext.Create())  
            {  
              // Arrange:  
                // Detour DateTime.Now to return a fixed date:  
                System.Fakes.ShimDateTime.NowGet =   
                () =>  
                { return new DateTime(fixedYear, 1, 1); };  
  
                // Instantiate the component under test:  
                var componentUnderTest = new MyComponent();  
  
              // Act:  
                int year = componentUnderTest.GetTheCurrentYear();  
  
              // Assert:   
                // This will always be true if the component is working:  
                Assert.AreEqual(fixedYear, year);  
            }  
        }  
}  
  
```  
  
```vb  
<TestClass()> _  
Public Class TestClass1  
    <TestMethod()> _  
    Public Sub TestCurrentYear()  
        Using s = Microsoft.QualityTools.Testing.Fakes.ShimsContext.Create()  
            Dim fixedYear As Integer = 2000  
            ' Arrange:  
            ' Detour DateTime.Now to return a fixed date:  
            System.Fakes.ShimDateTime.NowGet = _  
                Function() As DateTime  
                    Return New DateTime(fixedYear, 1, 1)  
                End Function  
  
            ' Instantiate the component under test:  
            Dim componentUnderTest = New MyComponent()  
            ' Act:  
            Dim year As Integer = componentUnderTest.GetTheCurrentYear  
            ' Assert:   
            ' This will always be true if the component is working:  
            Assert.AreEqual(fixedYear, year)  
        End Using  
    End Sub  
End Class  
```  
  
 Los nombres de clase Shim se componen anteponiendo `Fakes.Shim` al nombre de tipo original.  
  
 Las correcciones de compatibilidad funcionan mediante la inserción de *desvíos* en el código de la aplicación sometida a prueba. Siempre que se produce una llamada al método original, el sistema de Fakes realiza un desvío para que, en lugar de llamar al método real, se llame al código de la corrección de compatibilidad.  
  
 Observe que los desvíos se crean y se eliminan en tiempo de ejecución. Siempre debe crear un desvío durante la vida de un `ShimsContext`. Cuando se elimina, se quitan las correcciones de compatibilidad que creó mientras estaba activo. La mejor manera de hacerlo es dentro de una instrucción `using`.  
  
 Es posible que vea un error de compilación que indica que el espacio de nombres de Fakes no existe. Este error puede aparecer cuando hay otros errores de compilación. Corrija los demás errores y desaparecerá.  
  
##  <a name="BKMK_Shim_basics"></a> Correcciones de compatibilidad (shim) para los diferentes tipos de métodos  
 Los tipos de corrección de compatibilidad le permiten reemplazar cualquier método .NET, incluidos los métodos estáticos y los métodos no virtuales, con sus propios delegados.  
  
###  <a name="BKMK_Static_methods"></a> Métodos estáticos  
 Las propiedades para asociar las correcciones de compatibilidad a métodos estáticos se colocan en un tipo de corrección de compatibilidad. Cada propiedad tiene un solo establecedor que puede utilizarse para adjuntar un delegado al método de destino. Por ejemplo, dada una clase `MyClass` con un método estático `MyMethod`:  
  
```csharp  
//code under test  
public static class MyClass {  
    public static int MyMethod() {  
        ...  
    }  
}  
```  
  
 Podemos adjuntar a `MyMethod` una corrección de compatibilidad que devuelve siempre 5:  
  
```csharp  
// unit test code  
ShimMyClass.MyMethod = () =>5;  
```  
  
###  <a name="BKMK_Instance_methods__for_all_instances_"></a> Métodos de instancia (para todas las instancias)  
 Al igual que con los métodos estáticos, es posible corregir la compatibilidad de los métodos de instancia para todas las instancias. Las propiedades para asociar estas correcciones de compatibilidad se colocan en un tipo anidado denominado AllInstances para evitar la confusión. Por ejemplo, dada una clase `MyClass` con un método de instancia `MyMethod`:  
  
```csharp  
// code under test  
public class MyClass {  
    public int MyMethod() {  
        ...  
    }  
}  
```  
  
 Puede adjuntar a `MyMethod` una corrección de compatibilidad que siempre devuelve 5, independientemente de la instancia:  
  
```csharp  
// unit test code  
ShimMyClass.AllInstances.MyMethod = () => 5;  
```  
  
 La estructura del tipo generado de ShimMyClass es similar al código siguiente:  
  
```csharp  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass> {  
    public static class AllInstances {  
        public static Func<MyClass, int>MyMethod {  
            set {  
                ...  
            }  
        }  
    }  
}  
```  
  
 Observe que, en este caso, Fakes pasa la instancia en tiempo de ejecución como primer argumento del delegado.  
  
###  <a name="BKMK_Instance_methods__for_one_instance_"></a> Métodos de instancia (para una instancia en tiempo de ejecución)  
 También se puede corregir la compatibilidad de los métodos de instancia por medio de diferentes delegados que se basan en el receptor de la llamada. Esto permite que el mismo método de instancia tenga distintos comportamientos para cada instancia del tipo. Las propiedades para configurar estas correcciones de compatibilidad son métodos de instancia del propio tipo de corrección de compatibilidad. Cada instancia del tipo de corrección de compatibilidad está también asociada con una instancia sin procesar de un tipo corregido para compatibilidad.  
  
 Por ejemplo, dada una clase `MyClass` con un método de instancia `MyMethod`:  
  
```csharp  
// code under test  
public class MyClass {  
    public int MyMethod() {  
        ...  
    }  
}  
```  
  
 Podemos configurar dos tipos de corrección de compatibilidad de MyMethod de tal forma que el primero de ellos devuelva siempre 5 y el segundo devuelva siempre 10:  
  
```csharp  
// unit test code  
var myClass1 = new ShimMyClass()  
{  
    MyMethod = () => 5  
};  
var myClass2 = new ShimMyClass { MyMethod = () => 10 };  
```  
  
 La estructura del tipo generado de ShimMyClass es similar al código siguiente:  
  
```csharp  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass> {  
    public Func<int> MyMethod {  
        set {  
            ...  
        }  
    }  
    public MyClass Instance {  
        get {  
            ...  
        }  
    }  
}  
```  
  
 Puede tener acceso a la instancia real del tipo corregido para compatibilidad a través de la propiedad Instance:  
  
```csharp  
// unit test code  
var shim = new ShimMyClass();  
var instance = shim.Instance;  
```  
  
 El tipo de corrección de compatibilidad también tiene una conversión implícita al tipo corregido para compatibilidad, por lo que, en general, podrá usar el tipo de corrección de compatibilidad tal cual:  
  
```csharp  
// unit test code  
var shim = new ShimMyClass();  
MyClass instance = shim; // implicit cast retrieves the runtime  
                         // instance  
```  
  
###  <a name="BKMK_Constructors"></a> Constructores  
 También es posible corregir para compatibilidad los constructores con el fin de adjuntar tipos de correcciones de compatibilidad para futuros objetos. Cada constructor se expone como un método estático Constructor en el tipo de corrección de compatibilidad. Por ejemplo, dada una clase `MyClass` con un constructor que toma un entero:  
  
```csharp  
// code under test  
public class MyClass {  
    public MyClass(int value) {  
        this.Value = value;  
    }  
    ...  
}  
```  
  
 Establecemos el tipo de corrección de compatibilidad del constructor para que todas las instancias futuras devuelvan -5 cuando se invoque el captador Value, independientemente del valor que exista en el constructor:  
  
```csharp  
// unit test code  
ShimMyClass.ConstructorInt32 = (@this, value) => {  
    var shim = new ShimMyClass(@this) {  
        ValueGet = () => -5  
    };  
};  
```  
  
 Tenga en cuenta que cada tipo de corrección de compatibilidad expone dos constructores. El constructor predeterminado debe utilizarse cuando se necesita una nueva instancia, mientras el constructor que toma una instancia corregida para compatibilidad como argumento debe utilizarse únicamente en correcciones de compatibilidad de constructor:  
  
```csharp  
// unit test code  
public ShimMyClass() { }  
public ShimMyClass(MyClass instance) : base(instance) { }  
```  
  
 La estructura del tipo generado de ShimMyClass es similar al código siguiente:  
  
```csharp  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass>  
{  
    public static Action<MyClass, int> ConstructorInt32 {  
        set {  
            ...  
        }  
    }  
  
    public ShimMyClass() { }  
    public ShimMyClass(MyClass instance) : base(instance) { }  
    ...  
}  
```  
  
###  <a name="BKMK_Base_members"></a> Miembros base  
 Para tener acceso a las propiedades de correcciones de compatibilidad de los miembros base, se puede crear una corrección de compatibilidad para el tipo base y pasar la instancia secundaria como parámetro al constructor de la clase base de la corrección de compatibilidad.  
  
 Por ejemplo, dada una clase `MyBase` con un método de instancia `MyMethod` y un subtipo `MyChild`:  
  
```csharp  
public abstract class MyBase {  
    public int MyMethod() {  
        ...  
    }  
}  
  
public class MyChild : MyBase {  
}  
  
```  
  
 Podemos configurar una corrección de compatibilidad de `MyBase` creando una nueva corrección de compatibilidad `ShimMyBase`:  
  
```csharp  
// unit test code  
var child = new ShimMyChild();  
new ShimMyBase(child) { MyMethod = () => 5 };  
```  
  
 Tenga en cuenta que el tipo de corrección de compatibilidad secundaria se convierte implícitamente en la instancia secundaria cuando se pasa como parámetro al constructor de correcciones de compatibilidad de base.  
  
 La estructura del tipo generado de ShimMyChild y ShimMyBase es similar al código siguiente:  
  
```csharp  
// Fakes generated code  
public class ShimMyChild : ShimBase<MyChild> {  
    public ShimMyChild() { }  
    public ShimMyChild(Child child)  
        : base(child) { }  
}  
public class ShimMyBase : ShimBase<MyBase> {  
    public ShimMyBase(Base target) { }  
    public Func<int> MyMethod  
    { set { ... } }  
}  
```  
  
###  <a name="BKMK_Static_constructors"></a> Constructores estáticos  
 Los tipos de corrección de compatibilidad exponen un método estático `StaticConstructor` realizar correcciones de compatibilidad del constructor estático de un tipo. Dado que los constructores estáticos se ejecutan una sola vez, debe asegurarse de que la corrección de compatibilidad esté configurada antes de que se tenga acceso a cualquier miembro del tipo.  
  
###  <a name="BKMK_Finalizers"></a> Finalizadores  
 Los finalizadores no se admiten en Fakes.  
  
###  <a name="BKMK_Private_methods"></a> Métodos privados  
 El generador de código de Fakes creará las propiedades de corrección de compatibilidad para los métodos privados que solo tienen tipos visibles en la firma, es decir, tipos de parámetros y tipo de valor devuelto visibles.  
  
###  <a name="BKMK_Binding_interfaces"></a> Interfaces de enlace  
 Cuando un tipo corregido para compatibilidad implementa una interfaz, el generador de código emite un método que le permite enlazar a la vez todos los miembros de esa interfaz.  
  
 Por ejemplo, dada una clase `MyClass` que implementa `IEnumerable<int>`:  
  
```csharp  
public class MyClass : IEnumerable<int> {  
    public IEnumerator<int> GetEnumerator() {  
        ...  
    }  
    ...  
}  
  
```  
  
 Podemos realizar correcciones de compatibilidad de las implementaciones de `IEnumerable<int>` de MyClass llamando al método Bind:  
  
```csharp  
// unit test code  
var shimMyClass = new ShimMyClass();  
shimMyClass.Bind(new List<int> { 1, 2, 3 });  
  
```  
  
 La estructura del tipo generado de ShimMyClass es similar al código siguiente:  
  
```csharp  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass> {  
    public ShimMyClass Bind(IEnumerable<int> target) {  
        ...  
    }  
}  
  
```  
  
##  <a name="BKMK_Changing_the_default_behavior"></a> Cambiar el comportamiento predeterminado  
 Cada tipo de corrección de compatibilidad generado contiene una instancia de la interfaz `IShimBehavior` mediante la propiedad `ShimBase<T>.InstanceBehavior`. El comportamiento se usa siempre que un cliente llama a un miembro de instancia que no se ha corregido para compatibilidad explícitamente.  
  
 Si el comportamiento no se ha establecido, se utiliza la instancia devuelta por la propiedad estática `ShimsBehaviors.Current`. De forma predeterminada, esta propiedad devuelve un comportamiento que genera una excepción `NotImplementedException`.  
  
 Se puede cambiar en cualquier momento este comportamiento estableciendo la propiedad `InstanceBehavior` en cualquier instancia de corrección de compatibilidad. Por ejemplo, el siguiente fragmento cambia la corrección de compatibilidad a un comportamiento que no hace nada o devuelve el valor predeterminado del tipo de valor devuelto, es decir, default(T):  
  
```csharp  
// unit test code  
var shim = new ShimMyClass();  
//return default(T) or do nothing  
shim.InstanceBehavior = ShimsBehaviors.DefaultValue;  
  
```  
  
 El comportamiento también se puede cambiar globalmente para todas las instancias corregidas para compatibilidad en las que la propiedad `InstanceBehavior` no se ha establecido explícitamente mediante la propiedad estática `ShimsBehaviors.Current`:  
  
```csharp  
// unit test code  
// change default shim for all shim instances  
// where the behavior has not been set  
ShimsBehaviors.Current =   
    ShimsBehaviors.DefaultValue;  
  
```  
  
##  <a name="BKMK_Detecting_environment_accesses"></a> Detectar accesos al entorno  
 Es posible adjuntar a todos los miembros, incluidos los métodos estáticos, un comportamiento de un tipo determinado mediante la asignación del comportamiento `ShimsBehaviors.NotImplemented` a la propiedad estática `Behavior` del tipo de corrección de compatibilidad correspondiente:  
  
```csharp  
// unit test code  
// assigning the not implemented behavior  
ShimMyClass.Behavior = ShimsBehaviors.NotImplemented;  
// shorthand  
ShimMyClass.BehaveAsNotImplemented();  
  
```  
  
##  <a name="BKMK_Concurrency"></a> Simultaneidad  
 Los tipos de corrección de compatibilidad se aplican a todos los subprocesos en AppDomain y no tienen afinidad de subprocesos. Este hecho es importante si piensa utilizar un ejecutor de pruebas que admita la simultaneidad: las pruebas de tipos de corrección de compatibilidad no se pueden ejecutar simultáneamente. El tiempo de ejecución de Fakes no impone esta propiedad.  
  
##  <a name="BKMK_Calling_the_original_method_from_the_shim_method"></a> Llamar al método original desde el método de la corrección de compatibilidad (shim)  
 Imagine que quisiéramos escribir el texto en el sistema de archivos después de validar el nombre de archivo que se ha pasado al método. En ese caso, querríamos llamar al método original mientras seguimos en el método de corrección de compatibilidad.  
  
 El primer enfoque para solucionar este problema consiste en encapsular una llamada al método original mediante un delegado y `ShimsContext.ExecuteWithoutShims()`, como en el código siguiente:  
  
```csharp  
// unit test code  
ShimFile.WriteAllTextStringString = (fileName, content) => {  
  ShimsContext.ExecuteWithoutShims(() => {  
  
      Console.WriteLine("enter");  
      File.WriteAllText(fileName, content);  
      Console.WriteLine("leave");  
  });  
};  
  
```  
  
 Otro enfoque consiste en establecer la corrección de compatibilidad como null, llamar al método original y restaurar la corrección de compatibilidad.  
  
```csharp  
// unit test code  
ShimsDelegates.Action<string, string> shim = null;  
shim = (fileName, content) => {  
  try {  
    Console.WriteLine("enter");  
    // remove shim in order to call original method  
    ShimFile.WriteAllTextStringString = null;  
    File.WriteAllText(fileName, content);  
  }  
  finally  
  {  
    // restore shim  
    ShimFile.WriteAllTextStringString = shim;  
    Console.WriteLine("leave");  
  }  
};  
// initialize the shim  
ShimFile.WriteAllTextStringString = shim;  
  
```  
  
##  <a name="BKMK_Limitations"></a> Limitaciones  
 Las correcciones de compatibilidad (shim) no se pueden usar en todos los tipos de las bibliotecas de clases base de .NET **mscorlib** y **System**.  
  
## <a name="external-resources"></a>Recursos externos  
  
### <a name="guidance"></a>Orientación  
 [Pruebas de entrega continua con Visual Studio 2012. Capítulo 2: Pruebas unitarias: Prueba del interior](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## <a name="see-also"></a>Vea también  
 [Aislar el código en pruebas con Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)   
 [Blog de Peter Provost sobre correcciones de compatibilidad (shim) de Visual Studio 2012](http://www.peterprovost.org/blog/2012/04/25/visual-studio-11-fakes-part-2)   
 [Vídeo (1 h 16 min): Testing Un-testable Code with Fakes in Visual Studio 2012](http://go.microsoft.com/fwlink/?LinkId=261837) (Comprobación de código difícil de comprobar con Fakes en Visual Studio 2012)
