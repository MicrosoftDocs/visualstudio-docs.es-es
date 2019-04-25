---
title: Aislar el código en pruebas con Microsoft Fakes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: a03c2e83-a41f-4854-bcf2-fcaa277a819d
caps.latest.revision: 18
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 97f238b51e3f4ad3bbb32bdbdc134089c0cb7e99
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60099109"
---
# <a name="isolating-code-under-test-with-microsoft-fakes"></a>Aislar el código probado con Microsoft Fakes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft Fakes ayuda a aislar el código que se está probando mediante la sustitución de otras partes de la aplicación con *código auxiliar* o *correcciones de compatibilidad (shim)*. Se trata de pequeños fragmentos de código que están bajo el control de las pruebas. Al aislar código para pruebas, sabe que, en caso de error, la causa está localizada ahí y no en alguna otra parte. El código auxiliar y las correcciones de compatibilidad (shims) también permiten probar el código aunque no funcionen otras partes de la aplicación todavía.  
  
 Fakes tiene dos versiones:  
  
- El [código auxiliar](#stubs) reemplaza a una clase por un pequeño sustituto que implementa la misma interfaz.  Para utilizar código auxiliar, tiene que diseñar la aplicación para que cada componente dependa únicamente de interfaces y no de otros componentes. (Por "componente" se entiende una clase o grupo de clases diseñadas y actualizadas a la vez y que suelen estar contenidas en un ensamblado).  
  
- Una [corrección de compatibilidad (shim)](#shims) modifica el código compilado de la aplicación en tiempo de ejecución para que, en lugar de realizar una llamada de método especificada, ejecute el código shim que proporciona la prueba. Las correcciones de compatibilidad (shims) se pueden utilizar para reemplazar las llamadas a ensamblados que no se pueden modificar, como los ensamblados .NET.  
  
  ![Fakes reemplaza a otros componentes](../test/media/fakes-2.png "Fakes-2")  
  
  **Requisitos**  
  
- Visual Studio Enterprise  
  
## <a name="choosing-between-stub-and-shim-types"></a>Elegir entre código auxiliar y corrección de compatibilidad (shim)  
 Normalmente, un proyecto de Visual Studio se consideraría un componente, porque esas clases se desarrollan y actualizan al mismo tiempo. Puede considerar el uso de código auxiliar y correcciones de compatibilidad (shims) para las llamadas que el proyecto realice a otros proyectos de la solución o a otros ensamblados a los que el proyecto haga referencia.  
  
 Como directriz general, utilice código auxiliar para las llamadas dentro de la solución de Visual Studio y correcciones de compatibilidad (shims) para las llamadas a otros ensamblados a los que se hace referencia. El motivo es que, en su propia solución, es recomendable desacoplar los componentes definiendo las interfaces de la manera que el procesamiento con stub requiere. Sin embargo, los ensamblados externos, como System.dll, no se proporcionan normalmente con definiciones de interfaz independientes, por lo que en su lugar se deben utilizar correcciones de compatibilidad (shims).  
  
 Otras consideraciones son:  
  
 **Rendimiento.** Las correcciones de compatibilidad (shims) se ejecutan más lentamente porque reescriben el código en tiempo de ejecución. El código auxiliar no tiene esta sobrecarga de rendimiento y es tan rápido como los métodos virtuales.  
  
 **Métodos estáticos, tipos sellados.** Solo se puede utilizar código auxiliar para implementar interfaces. Por consiguiente, los tipos de código auxiliar no pueden utilizarse para los métodos estáticos, métodos no virtuales, métodos virtuales sellados, métodos de tipos sellados, etcétera.  
  
 **Tipos internos.** El código auxiliar y las correcciones de compatibilidad (shims) se pueden usar con los tipos internos que se hacen accesibles mediante el atributo de ensamblado <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.  
  
 **Métodos privados.** Las correcciones de compatibilidad (shims) pueden reemplazar llamadas a métodos privados si todos los tipos en la firma de método están visibles. El código auxiliar solo puede reemplazar métodos visibles.  
  
 **Interfaces y métodos abstractos.** El código auxiliar proporciona implementaciones de interfaces y métodos abstractos que se pueden utilizar en la prueba. Las correcciones de compatibilidad (shims) no pueden instrumentar interfaces y métodos abstractos, porque no tienen cuerpos de método.  
  
 Por lo general, nosotros recomendamos que se utilicen tipos de código auxiliar para aislar las dependencias del código base. Esto se puede conseguir ocultando los componentes en interfaces. Los tipos de corrección de compatibilidad (shim) pueden utilizarse para aislar los componentes de terceros que no proporcionan API comprobables.  
  
## <a name="stubs"></a> Introducción a los códigos auxiliares  
 Para obtener una descripción más detallada, vea [Usar stubs para aislar las partes de la aplicación entre sí para las pruebas unitarias](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).  
  
1. **Inyectar interfaces**  
  
     Para utilizar código auxiliar, tiene que escribir el código que desea probar de manera que no mencione clases en otro componente de la aplicación. Por "componente" se entiende una clase o clases que se desarrollan y se actualizan juntas, y que normalmente están contenidas en un proyecto de Visual Studio. Las variables y los parámetros que se deben declarar con interfaces e instancias de otros componentes deben pasarse en o crearse mediante un generador. Por ejemplo, si StockFeed es una clase de otro componente de la aplicación, se consideraría erróneo:  
  
     `return (new StockFeed()).GetSharePrice("COOO"); // Bad`  
  
     En su lugar, defina una interfaz que el otro componente pueda implementar y que también pueda implementar el código auxiliar con fines de evaluación:  
  
    ```csharp  
    public int GetContosoPrice(IStockFeed feed)  
    { return feed.GetSharePrice("COOO"); }  
  
    ```  
  
    ```vb  
    Public Function GetContosoPrice(feed As IStockFeed) As Integer  
     Return feed.GetSharePrice("COOO")  
    End Function  
  
    ```  
  
2. **Agregar un ensamblado de Fakes**  
  
    1. En el Explorador de soluciones, expanda la lista de referencia del proyecto de prueba. Si está trabajando en Visual Basic, debe seleccionar **Mostrar todos los archivos** para ver la lista de referencia.  
  
    2. Seleccione la referencia al ensamblado donde se define la interfaz (por ejemplo IStockFeed). En el menú contextual de esta referencia, seleccione **Agregar ensamblado de Fakes**.  
  
    3. Recompilar la solución.  
  
3. En las pruebas, cree instancias de código auxiliar y proporcione código para sus métodos:  
  
    ```csharp  
    [TestClass]  
    class TestStockAnalyzer  
    {  
        [TestMethod]  
        public void TestContosoStockPrice()  
        {  
          // Arrange:  
  
            // Create the fake stockFeed:  
            IStockFeed stockFeed =   
                 new StockAnalysis.Fakes.StubIStockFeed() // Generated by Fakes.  
                     {  
                         // Define each method:  
                         // Name is original name + parameter types:  
                         GetSharePriceString = (company) => { return 1234; }  
                     };  
  
            // In the completed application, stockFeed would be a real one:  
            var componentUnderTest = new StockAnalyzer(stockFeed);  
  
          // Act:  
            int actualValue = componentUnderTest.GetContosoPrice();  
  
          // Assert:  
            Assert.AreEqual(1234, actualValue);  
        }  
        ...  
    }  
    ```  
  
    ```vb  
    <TestClass()> _  
    Class TestStockAnalyzer  
  
        <TestMethod()> _  
        Public Sub TestContosoStockPrice()  
            ' Arrange:  
            ' Create the fake stockFeed:  
            Dim stockFeed As New StockAnalysis.Fakes.StubIStockFeed  
            With stockFeed  
                .GetSharePriceString = Function(company)  
                                           Return 1234  
                                       End Function  
            End With  
            ' In the completed application, stockFeed would be a real one:  
            Dim componentUnderTest As New StockAnalyzer(stockFeed)  
            ' Act:  
            Dim actualValue As Integer = componentUnderTest.GetContosoPrice  
            ' Assert:  
            Assert.AreEqual(1234, actualValue)  
        End Sub  
    End Class  
  
    ```  
  
     El toque mágico aquí lo pone la clase `StubIStockFeed`. Para cada interfaz del ensamblado al que se hace referencia, el mecanismo de Microsoft Fakes genera una clase de código auxiliar. El nombre de la clase de código auxiliar se deriva del nombre de la interfaz, con "`Fakes.Stub`" como prefijo y anexados los nombres de tipo de parámetro.  
  
     El código auxiliar también se genera para captadores y establecedores de propiedades, para los eventos y para métodos genéricos. Para más información, vea [Usar stubs para aislar las partes de la aplicación entre sí para las pruebas unitarias](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).  
  
## <a name="shims"></a> Introducción a las correcciones de compatibilidad (shim)  
 (Para obtener una descripción más detallada, vea [Usar correcciones de compatibilidad (shim) para aislar la aplicación de otros ensamblados para las pruebas unitarias](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)).  
  
 Supongamos que el componente contiene las llamadas a `DateTime.Now`:  
  
```csharp  
// Code under test:  
    public int GetTheCurrentYear()  
    {  
       return DateTime.Now.Year;  
    }  
  
```  
  
 Durante las pruebas, desea aplicar una corrección de compatibilidad (shim) a la propiedad `Now` porque la versión real devuelve de forma inapropiada un valor diferente en cada llamada.  
  
 Para utilizar correcciones de compatibilidad (shims) no tiene que modificar el código de aplicación o escribirlo de una forma determinada.  
  
1. **Agregar un ensamblado de Fakes**  
  
    En el Explorador de soluciones, abra las referencias del proyecto de prueba unitaria y seleccione la referencia al ensamblado que contiene el método que desee imitar. En este ejemplo, la clase `DateTime` está en **System.dll**.  Para ver las referencias en un proyecto de Visual Basic, seleccione **Mostrar todos los archivos**.  
  
    Seleccione **Agregar ensamblado de Fakes**.  
  
2. **Insertar una corrección de compatibilidad (shim) en ShimsContext**  
  
   ```csharp  
   [TestClass]  
   public class TestClass1  
   {   
           [TestMethod]  
           public void TestCurrentYear()  
           {  
               int fixedYear = 2000;  
  
               // Shims can be used only in a ShimsContext:  
               using (ShimsContext.Create())  
               {  
                 // Arrange:  
                   // Shim DateTime.Now to return a fixed date:  
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
  
    Los nombres de clase Shim se componen anteponiendo `Fakes.Shim` al nombre de tipo original. Los nombres de parámetro se anexan al nombre del método. (No es necesario agregar referencias de ensamblado a System.Fakes).  
  
   En el ejemplo anterior se utiliza una corrección de compatibilidad (shim) para un método estático. Para utilizar una corrección de compatibilidad (shim) para un método de instancia, escriba `AllInstances` entre el nombre del tipo y el nombre del método:  
  
```  
System.IO.Fakes.ShimFile.AllInstances.ReadToEnd = ...  
```  
  
 (No hay ningún ensamblado 'System.IO.Fakes' al que hacer referencia. El espacio de nombres lo genera el proceso de creación de correcciones de compatibilidad (shim), pero puede usar 'using' o 'Import' de la manera habitual).  
  
 También puede crear correcciones de compatibilidad (shims) para instancias concretas, para constructores y para propiedades. Para más información, vea [Usar correcciones de compatibilidad (shim) para aislar la aplicación de otros ensamblados para las pruebas unitarias](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).  
  
## <a name="in-this-section"></a>En esta sección  
 [Usar stubs para aislar las partes de la aplicación entre sí para la prueba unitaria](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md)  
  
 [Usar correcciones de compatibilidad (shim) para aislar la aplicación de otros ensamblados para la prueba unitaria](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)  
  
 [Generación de código, compilación y convenciones de nomenclatura en Microsoft Fakes](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md)
