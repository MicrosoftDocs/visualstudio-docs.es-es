---
title: "Soluci&#243;n de problemas de excepciones: System.NullReferenceException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "NullReferenceException (clase)"
ms.assetid: 4822b0b4-8105-43fb-887a-3cc51ff02899
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.NullReferenceException
Las excepciones <xref:System.NullReferenceException> se producen cuando intenta usar un método o una propiedad de un *tipo de referencia* \([C\#](/dotnet/csharp/language-reference/keywords/reference-types), [Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)\) cuyo valor es `null`. Por ejemplo, si trató de usar un objeto sin usar primero la palabra clave [new](/dotnet/csharp/language-reference/keywords/new) \([New](/dotnet/visual-basic/language-reference/operators/new-operator) en Visual Basic\), o si trató de usar un objeto cuyo valor estaba establecido en [null](/dotnet/csharp/language-reference/keywords/null) \([Nothing](/dotnet/visual-basic/language-reference/nothing) en Visual Basic\).  
  
##  <a name="BKMK_Contents"></a> Secciones de este artículo  
 [Clases que se usan en este artículo](#BKMK_Classes_used_in_the_examples)  
  
 [Causas habituales de excepciones NullReferenceException](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 [Buscar el origen de una excepción de referencia nula durante el desarrollo](#BKMK_Find_the_source_of_a_null_reference_exception_during_development)  
  
 [Evitar excepciones NullReferenceException](#BKMK_Avoid_NullReferenceExceptions)  
  
 [Controlar excepciones NullReferenceException en código de versión de lanzamiento](#BKMK_Handle_NullReferenceExceptions_in_release_code)  
  
##  <a name="BKMK_Classes_used_in_the_examples"></a> Clases que se usan en este artículo  
 En la mayoría de los ejemplos de este artículo se usa una de estas clases, o las dos:  
  
```c#  
public class Automobile { public EngineInfo Engine {get; set;} } public class EngineInfo { public EngineInfo() { } public EngineInfo(string powerSrc, double engineSize) { Power = powerSrc; Size = engineSize; } public double Size { get; set; } public string Power = null; }  
  
```  
  
```vb  
Public Class Automobile Public Property Engine As EngineInfo End Class Public Class EngineInfo Public Sub New() End Sub Public Sub New(powerSrc As String, engineSize As Double) Power = powerSrc Size = engineSize End Sub Public Property Size() As Double Public Power As String = Nothing End Class  
  
```  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Secciones de este artículo](#BKMK_Contents)  
  
##  <a name="BKMK_Common_causes_of_NullReferenceExceptions"></a> Causas habituales de excepciones NullReferenceException  
 Cualquier variable de tipo de referencia puede ser NULL. Las variables locales, las propiedades de una clase, los parámetros de método y los valores devueltos de los métodos pueden contener una referencia nula. Si se llama a métodos o propiedades de estas variables cuando son NULL se genera una excepción NullReferenceException. Casos específicos:  
  
 [Se declara, pero no se inicializa una variable local o un campo de miembro.](#BKMK_A_local_variable_or_member_field_is_declared_but_not_initialized)  
  
 [Una propiedad o un campo es NULL.](#BKMK_A_property_or_field_is_null)  
  
 [Un parámetro de método es NULL.](#BKMK_A_method_parameter_is_null)  
  
 [El valor devuelto de un método es NULL.](#BKMK_The_return_value_of_a_method_is_null)  
  
 [Un objeto de una colección o una matriz es NULL.](#BKMK_An_object_in_a_collection_or_array_is_null)  
  
 [Un objeto no se crea como consecuencia de una condición existente.](#BKMK_An_object_is_not_created_because_of_a_condition)  
  
 [Un objeto que se pasa por referencia a un método está establecido en NULL.](#BKMK_An_object_passed_by_reference_to_a_method_is_set_to_null)  
  
###  <a name="BKMK_A_local_variable_or_member_field_is_declared_but_not_initialized"></a> Se declara, pero no se inicializa una variable local o un campo de miembro.  
 Este sencillo error se da más a menudo en código de Visual Basic. Excepto en situaciones como la declaración de una variable que se va a pasar como parámetro de salida, el compilador de C\# no permite usar una variable de referencia local sin inicializarla. El compilador de Visual Basic genera una advertencia.  
  
-   En el siguiente código de C\#, la línea resaltada genera este error del compilador:  
  
 **Uso de la variable local no asignada “engine”**  
  
-   En el código de Visual Basic, la línea resaltada genera la advertencia BC42104 del compilador:  
  
 **La variable “engine” se utiliza antes de que se le asigne un valor. Podría producirse una excepción de referencia nula en tiempo de ejecución.**     La línea, además, genera una excepción NullReferenceException al ejecutarse.  
  
```c#  
public void NullReferencFromUninitializedLocalVariable() { EngineInfo engine; Console.WriteLine(engine.ToString()); }  
```  
  
```vb  
Public Sub NullReferencFromUninitializedLocalVariable() Dim engine As EngineInfo Console.WriteLine(engine.ToString()) End Sub  
```  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Causas habituales de excepciones NullReferenceException](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Secciones de este artículo](#BKMK_Contents)  
  
###  <a name="BKMK_A_property_or_field_is_null"></a> Una propiedad o un campo es NULL.  
 Los campos y las propiedades de una clase se inicializan automáticamente con su [valor predeterminado](../Topic/Data%20Member%20Default%20Values.md) cuando se crea la clase. El valor predeterminado de un tipo de referencia es `null` \(`Nothing` en Visual Basic\). Las llamadas a métodos de miembro en un campo o una propiedad de una clase principal cuando el campo o la propiedad es NULL generan una excepción NullReferenceException.  
  
 En este ejemplo, la línea resaltada genera una excepción NullReferenceException porque la propiedad `Engine` de `car` se inicializa automáticamente en NULL.  
  
```c#  
public void NullReferenceFromProperty() { var car = new Automobile(); Console.WriteLine(car.Engine.ToString()); }  
```  
  
```vb  
Public Sub NullReferenceFromProperty() Dim car = New Automobile() Console.WriteLine(car.Engine.ToString()) End Sub  
```  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Causas habituales de excepciones NullReferenceException](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Secciones de este artículo](#BKMK_Contents)  
  
###  <a name="BKMK_A_method_parameter_is_null"></a> Un parámetro de método es NULL.  
 Un parámetro de método que es un tipo de referencia puede ser `null` \(`Nothing` en Visual Basic\). Las llamadas a métodos o propiedades de miembro en un valor de parámetro NULL generan una excepción NullReferenceException.  
  
 En este ejemplo, la línea resaltada genera una excepción NullReferenceException porque `BadEngineInfoPassedToMethod` llama a `NullReferenceFromMethodParameter` con un parámetro que es NULL.  
  
```c  
public void BadEngineInfoPassedToMethod() { EngineInfo eng = null; NullReferenceFromMethodParameter(eng); } public void NullReferenceFromMethodParameter(EngineInfo engine) { Console.WriteLine(engine.ToString()); }  
  
```  
  
```vb  
Public Sub BadParameterPassedToMethod() As EngineInfo Dim eng As EngineInfo = Nothing NullReferenceFromMethodParameter(eng) End Sub Public Sub NullReferenceFromMethodParameter(engine As EngineInfo) Console.WriteLine(engine.ToString()) End Sub  
```  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Causas habituales de excepciones NullReferenceException](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Secciones de este artículo](#BKMK_Contents)  
  
###  <a name="BKMK_The_return_value_of_a_method_is_null"></a> El valor devuelto de un método es NULL.  
 Un método que devuelve un tipo de referencia puede devolver `null` \(`Nothing` en Visual Basic\). Las llamadas a métodos o propiedades del tipo de referencia devuelto generan una excepción NullReferenceException si la referencia es NULL.  
  
 En este ejemplo, la línea resaltada lanza una excepción NullReferenceException porque la llamada a `BadGetEngineInfo` devuelve una referencia nula en el método `NullReferenceFromMethodParameter`.  
  
```c#  
public EngineInfo BadGetEngineInfo() { EngineInfo engine = null; return engine; } public void NullReferenceFromMethodReturnValue() { var engine = BadGetEngineInfo(); Console.WriteLine(engine.ToString()); }  
```  
  
```vb  
Public Function BadGetEngineInfo() As EngineInfo Dim engine As EngineInfo = Nothing Return engine End Function Public Sub NullReferenceFromMethodReturnValue() Dim engine = BadGetEngineInfo() Console.WriteLine(engine.ToString()) End Sub  
  
```  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Causas habituales de excepciones NullReferenceException](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Secciones de este artículo](#BKMK_Contents)  
  
###  <a name="BKMK_An_object_in_a_collection_or_array_is_null"></a> Un objeto de una colección o una matriz es NULL.  
 Una lista o matriz de tipos de referencia puede contener un elemento que sea NULL. Las llamadas a métodos o propiedades de un elemento de lista que es NULL generan una excepción NullReferenceException.  
  
 En este ejemplo, la línea resaltada en `NullReferenceFromListItem()` genera una excepción NullReferenceException porque la llamada a `BadGetCarList` devuelve un elemento que es NULL.  
  
```c#  
public Automobile[] BadGetCarList() { var autos = new Automobile[10]; for (int i = 0; i autos.Length; i++) { if (i != 6) { autos[i] = new Automobile(); } } return autos; } public void NullReferenceFromListItem() { var cars = BadGetCarList(); foreach (Automobile car in cars) { Console.WriteLine(car.ToString()); } }  
```  
  
```vb  
Public Function BadGetCarList() As Automobile() Dim autos = New Automobile(10) {} For i As Integer = 0 To 9 If i <> 6 Then autos(i) = New Automobile() End If Next Return autos End Function Public Sub NullReferenceFromListItem() Dim cars = BadGetCarList() For Each car As Automobile In cars Console.WriteLine(car.ToString()) Next End Sub  
```  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Causas habituales de excepciones NullReferenceException](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Secciones de este artículo](#BKMK_Contents)  
  
###  <a name="BKMK_An_object_is_not_created_because_of_a_condition"></a> Un objeto no se crea como consecuencia de una condición existente.  
 Si se inicializa un tipo de referencia en un bloque condicional, el objeto no se crea si la condición es FALSE.  
  
 En este ejemplo, la línea resaltada en `NullReferenceFromConditionalCreation` lanza una excepción NullReferenceException porque inicializa la variable `engine` solo si el método `DetermineTheCondition()` devuelve `true`.  
  
```c#  
public bool DetermineTheCondition() { return false; } public void NullReferenceFromConditionalCreation() { EngineInfo engine = null; var condition = DetermineTheCondition(); if (condition) { engine = new EngineInfo(); engine.Power = "Diesel"; engine.Size = 2.4; } Console.WriteLine(engine.Size); }  
```  
  
```vb  
Public Function DetermineTheCondition() As Boolean Return False End Function Public Sub NullReferenceFromConditionalCreation() Dim engine As EngineInfo = Nothing Dim condition = DetermineTheCondition() If condition Then engine = New EngineInfo() engine.Power = "Diesel" engine.Size = 2.4 End If Console.WriteLine(engine.Size) End Sub  
```  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Causas habituales de excepciones NullReferenceException](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Secciones de este artículo](#BKMK_Contents)  
  
### La propiedad de un objeto que se pasa a un método está establecida en NULL.  
 Cuando un objeto se pasa como parámetro a un método con su valor \(sin usar la palabra clave `ref` o `out` en C\# o la palabra clave `ByRef` en Visual Basic\), el método no puede cambiar la ubicación en memoria del parámetro \(a qué apunta el parámetro\), pero puede cambiar las propiedades del objeto.  
  
 En este ejemplo, el método `NullPropertyReferenceFromPassToMethod` crea el objeto `Automobile` e inicializa la propiedad `Engine`. Luego, llama a `BadSwapCarEngine`, que pasa el nuevo objeto como parámetro.`BadSwapCarEngine` establece la propiedad Engine en NULL, lo que hace que la línea resaltada en `NullPropertyReferenceFromPassToMethod` genere una excepción NullReferenceException.  
  
```c#  
public void BadSwapCarEngine(Automobile car) { car.Engine = null; } public void (Automobile car) { car.Engine = new EngineInfo("GAS", 1.5); BadSwapCarEngine(car); Console.WriteLine(car.Engine.ToString()); }  
  
```  
  
```vb  
Public Sub BadSwapCarEngine(car As Automobile) car.Engine = Nothing End Sub Public Sub NullPropertyReferenceFromPassToMethod() Dim car As New Automobile() car.Engine = New EngineInfo("GAS", 1.5) BadSwapCarEngine(car) Console.WriteLine(car.Engine.ToString()) End Sub  
```  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Causas habituales de excepciones NullReferenceException](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Secciones de este artículo](#BKMK_Contents)  
  
###  <a name="BKMK_An_object_passed_by_reference_to_a_method_is_set_to_null"></a> Un objeto que se pasa por referencia a un método está establecido en NULL.  
 Si se pasa un tipo de referencia como parámetro a un método por referencia \(mediante la palabra clave `ref` o `out` en C\#, o la palabra clave `ByRef` en Visual Basic\), se puede cambiar la ubicación de memoria a la que señala el parámetro.  
  
 Si se pasa un tipo de referencia por referencia a un método, el método puede definir el tipo al que se hace referencia en `null` \(`Nothing` en Visual Basic\).  
  
 En este ejemplo, la línea resaltada en `NullReferenceFromPassToMethodByRef` lanza una excepción NullReferenceException porque la llamada al método `BadEngineSwapByRef` establece la variable `stockEngine` en NULL.  
  
```c#  
public void BadEngineSwapByRef(ref EngineInfo engine) { engine = null; } public void NullReferenceFromPassToMethodByRef() { var stockEngine = new EngineInfo(); stockEngine.Power = "Gas"; stockEngine.Size = 7.0; BadSwapEngineByRef(ref stockEngine); Console.WriteLine(stockEngine.ToString()); }  
```  
  
```vb  
Public Sub BadSwapEngineByRef(ByRef engine As EngineInfo) engine = Nothing End Sub Public Sub NullReferenceFromPassToMethodByRef() Dim formatStr = "The stock engine has been replaced by a {0} liter {} engine" Dim stockEngine = New EngineInfo() stockEngine.Power = "Gas" stockEngine.Size = 7.0 BadSwapEngineByRef(stockEngine) Console.WriteLine(stockEngine.ToString()) End Sub  
  
```  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Causas habituales de excepciones NullReferenceException](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Secciones de este artículo](#BKMK_Contents)  
  
##  <a name="BKMK_Find_the_source_of_a_null_reference_exception_during_development"></a> Buscar el origen de una excepción de referencia nula durante el desarrollo  
 [Usar informaciones sobre datos, la ventana Variables locales y las ventanas Inspección para ver los valores de las variables](#BKMK_Use_data_tips_the_Locals_window_and_watch_windows_to_see_variables_values)  
  
 [Recorrer la pila de llamadas para buscar el lugar en el que una variable de referencia no se inicializa o está establecida en NULL](#BKMK_Walk_the_call_stack_to_find_where_a_type_reference_is_not_initialized_or_set_to_null_)  
  
 [Establecer puntos de interrupción condicionales para detener la depuración si un objeto es NULL (Nothing en Visual Basic)](#BKMK_Set_conditional_breakpoints_to_stop_debugging_when_an_object_is_null_Nothing_in_Visual_Basic_)  
  
###  <a name="BKMK_Use_data_tips_the_Locals_window_and_watch_windows_to_see_variables_values"></a> Usar informaciones sobre datos, la ventana Variables locales y las ventanas Inspección para ver los valores de las variables  
  
-   Coloque el puntero sobre el nombre de la variable para ver su valor en la [información sobre datos](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Si la variable hace referencia a un objeto o una colección, puede expandir el tipo de datos para examinar sus propiedades o elementos.  
  
-   Abra la ventana **Variables locales** para examinar las variables activas en el contexto actual.  
  
-   Use una [ventana de inspección](../debugger/watch-and-quickwatch-windows.md) para centrarse en los cambios de una variable al ir avanzando por el código.  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Buscar el origen de una excepción de referencia nula durante el desarrollo](#BKMK_Find_the_source_of_a_null_reference_exception_during_development)  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Secciones de este artículo](#BKMK_Contents)  
  
###  <a name="BKMK_Walk_the_call_stack_to_find_where_a_type_reference_is_not_initialized_or_set_to_null_"></a> Recorrer la pila de llamadas para buscar el lugar en el que una variable de referencia no se inicializa o está establecida en NULL  
 La [ventana Pila de llamadas](../debugger/how-to-use-the-call-stack-window.md) de Visual Studio muestra una lista con los nombres de los métodos que no se han finalizado cuando el depurador se detiene en una excepción o un punto de interrupción. Puede seleccionar un nombre de la ventana **Pila de llamadas** y elegir **Cambiar a marco** para cambiar el contexto de ejecución del método y examinar sus variables.  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Buscar el origen de una excepción de referencia nula durante el desarrollo](#BKMK_Find_the_source_of_a_null_reference_exception_during_development)  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Secciones de este artículo](#BKMK_Contents)  
  
###  <a name="BKMK_Set_conditional_breakpoints_to_stop_debugging_when_an_object_is_null_Nothing_in_Visual_Basic_"></a> Establecer puntos de interrupción condicionales para detener la depuración si un objeto es NULL \(Nothing en Visual Basic\)  
 Puede establecer un [punto de interrupción condicional](http://msdn.microsoft.com/library/5557y8b4.aspx#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) para interrumpir cuando una variable es null. Los puntos de interrupción condicionales pueden ser útiles cuando la referencia nula no es muy frecuente: por ejemplo, cuando un elemento de una colección es NULL solo de vez en cuando. Otra ventaja de los puntos de interrupción condicionales es que le permiten depurar un problema antes de confirmar una rutina de control concreta.  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Buscar el origen de una excepción de referencia nula durante el desarrollo](#BKMK_Find_the_source_of_a_null_reference_exception_during_development)  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Secciones de este artículo](#BKMK_Contents)  
  
##  <a name="BKMK_Avoid_NullReferenceExceptions"></a> Evitar excepciones NullReferenceException  
 [Usar Debug.Assert para confirmar una invariable](#BKMK_Use_Debug_Assert_to_confirm_an_invariant)  
  
 [Inicializar totalmente tipos de referencia](#BKMK_Fully_initialize_reference_types)  
  
###  <a name="BKMK_Use_Debug_Assert_to_confirm_an_invariant"></a> Usar Debug.Assert para confirmar una invariable  
 Una *invariable* es una condición de la que se sabe con certeza que es true. Una instrucción [Debug.Assert \(System.Diagnostics\)](http://msdn.microsoft.com/library/system.diagnostics.debug.assert.aspx) solo se llama desde compilaciones de depuración de las aplicaciones y no desde el código de versión. Si la condición invariable no es TRUE, el depurador se interrumpe en la instrucción Assert y se muestra un cuadro de diálogo.`Debug.Assert` proporciona una comprobación para confirmar que la condición no ha cambiado mientras se desarrolla la aplicación. Las aserciones también documentan para las demás personas que leen el código que la condición siempre debe ser true.  
  
 Por ejemplo, el método `MakeEngineFaster` presupone que su parámetro `engine` no será nunca NULL porque se sabe que su único método de llamada \(`TheOnlyCallerOfMakeEngineFaster`\) inicializa `EngineInfo` por completo. La aserción de `MakeEngineFaster` documenta el supuesto y proporciona una comprobación de que el supuesto es true.  
  
 Si alguien agrega un nuevo método de llamada \(`BadNewCallerOfMakeEngineFaster`\) que no inicializa el parámetro, se desencadena la aserción.  
  
```c#  
private void TheOnlyCallerOfMakeEngineFaster() { var engine = new EngineInfo(); engine.Power = "GAS"; engine.Size = 1.5; MakeEngineFaster(engine); } private void MakeEngineFaster(EngineInfo engine) { System.Diagnostics.Debug.Assert(engine != null, "Assert: engine != null"); engine.Size *= 2; Console.WriteLine("The engine is twice as fast"); } private void BadNewCallerOfMakeEngineFaster() { EngineInfo engine = null; MakeEngineFaster(engine); }  
```  
  
```vb  
Public Sub TheOnlyCallerOfMakeEngineFaster() Dim engine As New EngineInfo engine.Power = "GAS" engine.Size = 1.5 MakeEngineFaster(engine) End Sub Private Sub MakeEngineFaster(engine As EngineInfo) System.Diagnostics.Debug.Assert(engine IsNot Nothing, "Assert: engine IsNot Nothing") engine.Size = engine.Size * 2 Console.WriteLine("The engine is twice as fast") End Sub Public Sub BadNewCallerOfMakeEngineFaster() Dim engine As EngineInfo = Nothing MakeEngineFaster(engine) End Sub  
```  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Evitar excepciones NullReferenceException](#BKMK_Avoid_NullReferenceExceptions)  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Secciones de este artículo](#BKMK_Contents)  
  
###  <a name="BKMK_Fully_initialize_reference_types"></a> Inicializar totalmente tipos de referencia  
 Para evitar muchas excepciones NullReferenceException, inicialice totalmente los tipos de referencia tan pronto como sea posible después de crearlos.  
  
 **Agregar inicialización completa a clases propias**  
  
 Si puede controlar la clase que genera una excepción NullReferenceException, considere la posibilidad de inicializar totalmente el objeto en el constructor del tipo. El ejemplo siguiente es una versión revisada de las clases de ejemplo que garantiza la inicialización completa:  
  
```c#  
public class Automobile { public EngineInfo Engine { get; set; } public Automobile(){this.Engine = new EngineInfo();} public Automobile(string powerSrc, double engineSize) { this.Engine = new EngineInfo(powerSrc, engineSize); } } public class EngineInfo { public double Size {get; set;} public string Power {get; set;} public EngineInfo(){// the base enginethis.Power = "GAS";this.Size = 1.5;} public EngineInfo(string powerSrc, double engineSize) { this.Power = powerSrc; this.Size = engineSize; } }  
  
```  
  
```vb  
Public Class Automobile Public Property Engine As EngineInfo     Public Sub New()Me.Engine = New EngineInfo()End SubPublic Sub New(powerSrc As String, engineSize As Double)Me.Engine = New EngineInfo(powerSrc, engineSize)End Sub End Class Public Class BaseEngineInfo Public Sub New()' the base engineMe.Power = "GAS"Me.Size = 1.5End Sub Public Sub New(powerSrc As String, engineSize As Double) Power = powerSrc Size = engineSize End Sub Public Property Size() As Double Public Power As String = String.Empty End Class  
```  
  
> [!NOTE]
>  **Usar inicialización diferida para propiedades de gran tamaño o que no se usan a menudo**  
>   
>  Para reducir la superficie de memoria de una clase y mejorar su rendimiento, considere la posibilidad de usar la inicialización diferida de las propiedades de tipos de referencia. Vea [Lazy Initialization](../Topic/Lazy%20Initialization.md).  
  
##  <a name="BKMK_Handle_NullReferenceExceptions_in_release_code"></a> Controlar excepciones NullReferenceException en código de versión de lanzamiento  
 [Comprobar si aparece NULL (Nothing en Visual Basic) antes de usar un tipo de referencia](#BKMK_Check_for_null_Nothing_in_Visual_Basic_before_using_a_reference_type)  
  
 [Usar try-catch-finally (Try-Catch-Finally en Visual Basic) para controlar la excepción](#BKMK_Use_try_catch_finally_Try_Catch_Finally_in_Visual_Basic_to_handle_the_exception)  
  
 Es mejor evitar las excepciones NullReferenceException que controlarlas después de que se produzcan. Controlar una excepción puede dificultar el mantenimiento y la comprensión del código y, a veces, puede introducir otros errores. Las excepciones NullReferenceException suelen ser errores sin recuperación. En esos casos, la mejor opción puede ser permitir que la excepción detenga la aplicación.  
  
 Sin embargo, hay muchas situaciones en las que puede ser útil controlar el error:  
  
-   La aplicación puede pasar por alto los objetos que son NULL. Por ejemplo, si la aplicación recupera y procesa los registros de una base de datos, puede caber la opción de pasar por alto cierto número de registros incorrectos que generan objetos NULL. Es posible que solo tenga que registrar los datos incorrectos en un archivo de registro o en la interfaz de usuario de la aplicación.  
  
-   La recuperación tras la excepción es posible. Por ejemplo, una llamada a un servicio web que devuelve un tipo de referencia podría devolver NULL si se interrumpe la conexión o se agota el tiempo de espera. Puede tratar de restablecer la conexión y volver a hacer la llamada.  
  
-   Puede restaurar el estado de la aplicación a un estado válido. Por ejemplo, puede que esté realizando una tarea con varios pasos que exija guardar información en un almacén de datos antes de llamar a un método que lance una excepción NullReferenceException. Si el objeto sin inicializar fuera a dañar el registro de datos, puede quitar los datos anteriores antes de cerrar la aplicación.  
  
-   La excepción se tiene que notificar. Por ejemplo, si la causa del error fue un error del usuario de la aplicación, puede generar un mensaje para indicarle cómo proporcionar la información correcta. También puede registrar información sobre el error para facilitar la resolución del problema. Algunos marcos, como ASP.NET, tienen un controlador de excepciones de nivel superior que captura todos los errores para que la aplicación no se bloquee nunca. En ese caso, puede que la única forma de saber que se produce sea registrar la excepción.  
  
 Aquí puede ver dos formas de controlar las excepciones NullReferenceException en el código de versión de lanzamiento.  
  
###  <a name="BKMK_Check_for_null_Nothing_in_Visual_Basic_before_using_a_reference_type"></a> Comprobar si aparece NULL \(Nothing en Visual Basic\) antes de usar un tipo de referencia  
 El uso de una prueba explícita para comprobar si aparece NULL antes de utilizar un objeto evita el problema de rendimiento de las construcciones try, catch y finally. Aun así, tiene que determinar e implementar lo que se debe hacer para responder a un objeto que no se inicializa.  
  
 En este ejemplo, `CheckForNullReferenceFromMethodReturnValue` comprueba el valor devuelto del método `BadGetEngineInfo`. Si el objeto no es NULL, se utiliza; de lo contrario, el método notifica el error.  
  
```c#  
public EngineInfo BadGetEngineInfo() { EngineInfo engine = null; return engine; } public void CheckForNullReferenceFromMethodReturnValue() { var engine = BadGetEngineInfo(); if(engine != null) { // modify the info engine.Power = "DIESEL"; engine.Size = 2.4; } else { // report the error Console.WriteLine("BadGetEngine returned null") } }  
  
```  
  
```vb  
public EngineInfo BadGetEngineInfo() { EngineInfo engine = null; return engine; } Public Sub CheckForNullReferenceFromMethodReturnValue() Dim engine = BadGetEngineInfo() If (engine IsNot Nothing) Then ' modify the info engine.Power = "DIESEL" engine.Size = 2.4 Else ' report the error Console.WriteLine("BadGetEngineInfo returned Nothing") End If End Sub  
```  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Controlar excepciones NullReferenceException en código de versión de lanzamiento](#BKMK_Handle_NullReferenceExceptions_in_release_code)  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Secciones de este artículo](#BKMK_Contents)  
  
###  <a name="BKMK_Use_try_catch_finally_Try_Catch_Finally_in_Visual_Basic_to_handle_the_exception"></a> Usar try\-catch\-finally \(Try\-Catch\-Finally en Visual Basic\) para controlar la excepción  
 Usar las construcciones integradas de control de excepciones \([try, catch y finally](/dotnet/csharp/language-reference/keywords/exception-handling-statements) en C\# y [Try, Catch y Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement) en Visual Basic\) ofrece más opciones para controlar excepciones NullReferenceException que comprobar si un objeto no es NULL.  
  
 En este ejemplo, `CatchNullReferenceFromMethodCall` utiliza dos aserciones para confirmar la suposición de que su parámetro contiene un objeto automobile completo, incluido un objeto engine. En el bloque `try`, la línea resaltada lanza una excepción NullReferenceException porque la llamada a `RarelyBadEngineSwap` puede destruir la propiedad `Engine` del automóvil. El bloque `catch` captura la excepción, escribe la información de la excepción en un archivo e informa del error al usuario. En el bloque `finally`, el método se asegura de que el estado del automóvil no sea peor que cuando se inició el método.  
  
```c#  
public void RarelyBadSwapCarEngine(Automobile car) { if ((new Random()).Next() == 42) { car.Engine = null; } else { car.Engine = new EngineInfo("DIESEL", 2.4); } } public void CatchNullReferenceFromMethodCall(Automobile car) { System.Diagnostics.Debug.Assert(car != null, "Assert: car != null"); System.Diagnostics.Debug.Assert(car.Engine != null, "Assert: car.Engine != null"); // save current engine properties in case they're needed var enginePowerBefore = car.Engine.Power; var engineSizeBefore = car.Engine.Size; try { RarelyBadSwapCarEngine(car); var msg = "Swap succeeded. New engine power source: {0} size {1}"; Console.WriteLine(msg, car.Engine.Power, car.Engine.Size); } catch(NullReferenceException nullRefEx) { // write exception info to log file LogException(nullRefEx); // notify the user Console.WriteLine("Engine swap failed. Please call your customer rep."); } finally { if(car.Engine == null) { car.Engine = new EngineInfo(enginePowerBefore, engineSizeBefore); } } }  
  
```  
  
```vb  
Public Sub RarelyBadSwapCarEngine(car As Automobile) If (New Random()).Next = 42 Then car.Engine = Nothing Else car.Engine = New EngineInfo("DIESEL", 2.4) End If End Sub Public Sub CatchNullReferenceFromMethodCall(car As Automobile) System.Diagnostics.Debug.Assert(car IsNot Nothing) System.Diagnostics.Debug.Assert(car.Engine IsNot Nothing) ' save current engine properties in case they're needed Dim powerBefore = car.Engine.Power Dim sizeBefore = car.Engine.Size Try RarelyBadSwapCarEngine(car) Dim msg = "Swap succeeded. New engine power source: {0} size {1}" Console.WriteLine(msg, car.Engine.Power, car.Engine.Size) Catch nullRefEx As NullReferenceException ' write exception info to log file LogException(nullRefEx) ' notify user Console.WriteLine("Engine swap failed. Please call your customer rep.") Finally If car.Engine Is Nothing Then car.Engine = New EngineInfo(powerBefore, sizeBefore) End Try End Sub  
  
```  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Controlar excepciones NullReferenceException en código de versión de lanzamiento](#BKMK_Handle_NullReferenceExceptions_in_release_code)  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Secciones de este artículo](#BKMK_Contents)  
  
## Artículos relacionados  
 [Instrucciones de diseño de excepciones \(Instrucciones de diseño de .NET Framework\)](http://msdn.microsoft.com/library/ms229014)  
  
 [Controlar y generar excepciones \(Elementos esenciales de aplicaciones de .NET Framework\)](http://msdn.microsoft.com/library/5b2yeyab)  
  
 [Cómo: Recibir notificaciones de excepciones de primera oportunidad \(Guía de desarrollo para .NET Framework\)](http://msdn.microsoft.com/library/Dd997368)  
  
 [Cómo: Controlar excepciones en una consulta PLINQ \(Guía de desarrollo para .NET Framework\)](http://msdn.microsoft.com/library/Dd460712)  
  
 [Excepciones en subprocesos administrados \(Guía de desarrollo de .NET Framework\)](http://msdn.microsoft.com/library/ms228965)  
  
 [Excepciones y control de excepciones \(Guía de programación de C\#\)](http://msdn.microsoft.com/library/ms173160)  
  
 [Instrucciones para el control de excepciones \(Referencia de C\#\)](http://msdn.microsoft.com/library/s7fekhdy)  
  
 [Instrucción Try...Catch...Finally \(Visual Basic\)](http://msdn.microsoft.com/library/fk6t46tz)  
  
 [Control de excepciones \(F\#\)](http://msdn.microsoft.com/library/Dd233223)  
  
 [Excepciones en C\+\+\/CLI](http://msdn.microsoft.com/library/Hh875008)  
  
 [Control de excepciones \(Task Parallel Library\)](http://msdn.microsoft.com/library/Dd997415)  
  
 [Control de excepciones \(Depurar\)](http://msdn.microsoft.com/library/x85tt0dd)  
  
 [Tutorial: Controlar una excepción de simultaneidad \(Acceder a los datos en Visual Studio\)](http://msdn.microsoft.com/library/ms171936)  
  
 [Cómo: Controlar errores y excepciones que se producen con el enlace de datos \(Windows Forms\)](http://msdn.microsoft.com/library/k26k86tb)  
  
 [Control de excepciones en aplicaciones de red \(XAML\) \(Windows\)](http://msdn.microsoft.com/library/Dn263240)  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Secciones de este artículo](#BKMK_Contents)