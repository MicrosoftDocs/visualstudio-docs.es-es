---
title: "Soluci&#243;n de problemas de excepciones: System.InvalidOperationException | Microsoft Docs"
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
  - "InvalidOperationException (clase)"
ms.assetid: db3400e5-62d7-4d65-897d-387e7edcb7cf
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.InvalidOperationException
Si se llama a un método de un objeto cuando el estado del objeto no admite la llamada de método, se lanza una <xref:System.InvalidOperationException?displayProperty=fullName>. También se lanza la excepción cuando un método trata de manipular la interfaz de usuario desde un subproceso que no es el principal ni el subproceso de la interfaz de usuario.  
  
> [!IMPORTANT]
>  Dado que las excepciones <xref:System.InvalidOperationException> se pueden lanzar en una gran variedad de circunstancias, es importante que lea y comprenda el <xref:System.Exception.Message%2A> que se muestra en el Asistente de excepciones.  
  
##  <a name="BKMK_In_this_article"></a> En este artículo  
 [Un método que se ejecuta en un subproceso ajeno a la interfaz de usuario actualiza la interfaz de usuario](#BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI)  
  
 [Una declaración de un bloque de foreach (For Each en Visual Basic) cambia la colección que está iterando](#BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating)  
  
 [Un Nullable&lt;T&gt; que es NULL se convierte en T](#BKMK_A_Nullable_T_that_is_null_is_cast_to_T)  
  
 [Se llama a un método System.Linq.Enumerable en una colección vacía](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
 [Artículos relacionados](#BKMK_Related_articles)  
  
 En los ejemplos de código de este artículo, se muestra cómo se pueden producir algunas excepciones <xref:System.InvalidOperationException> comunes en la aplicación. La manera de controlar los problemas depende de cada situación en concreto. Si la excepción es irrecuperable para la funcionalidad de la aplicación, puede que le convenga usar una construcción [try … catch](/dotnet/csharp/language-reference/keywords/exception-handling-statements) \([Try .. Catch](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement) en Visual Basic\) para capturar la excepción y limpiar el estado de la aplicación antes de salir. Pero otras excepciones <xref:System.InvalidOperationException> se pueden prever y evitar. Los ejemplos de métodos revisados le muestran algunas de estas técnicas.  
  
##  <a name="BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI"></a> Un método que se ejecuta en un subproceso ajeno a la interfaz de usuario actualiza la interfaz de usuario  
 [Provocación de una excepción InvalidOperationException con una actualización de la interfaz de usuario desde un subproceso ajeno a la interfaz de usuario](#BKMK_Causing_an_InvalidOperationException_with_a_UI_update_from_a_non_UI_thread)  **&#124;**  [Evitar excepciones InvalidOperationException en subprocesos ajenos a la interfaz de usuario](#BKMK_Avoiding_InvalidOperationExceptions_on_non_UI_threads)  
  
 La mayoría de los marcos de aplicaciones de GUI \(interfaz gráfica de usuario\) de .NET, como Windows Forms y Windows Presentation Foundation \(WPF\), le permiten acceder a objetos de la GUI solo desde el subproceso que crea y administra la interfaz de usuario \(el subproceso **Main** o **UI**\). Si trata de acceder a un elemento de la interfaz de usuario desde un subproceso que no es el subproceso de la interfaz de usuario, se lanza una <xref:System.InvalidOperationException>.  
  
###  <a name="BKMK_Causing_an_InvalidOperationException_with_a_UI_update_from_a_non_UI_thread"></a> Provocación de una excepción InvalidOperationException con una actualización de la interfaz de usuario desde un subproceso ajeno a la interfaz de usuario  
  
> [!NOTE]
>  En los ejemplos siguientes, se usa el [Task\-based Asynchronous Pattern \(TAP\)](../Topic/Task-based%20Asynchronous%20Pattern%20\(TAP\).md) para crear subprocesos ajenos a la interfaz de usuario. Sin embargo, los ejemplos también son relevantes para todos los [Asynchronous Programming Patterns](../Topic/Asynchronous%20Programming%20Patterns.md) de .NET.  
  
 En estos ejemplos, el controlador de eventos `ThreadsExampleBtn_Click` llama al método `DoSomeWork` dos veces. La primera llamada al método \(`DoSomeWork(20);` se ejecuta de forma sincrónica correctamente. Sin embargo, la segunda llamada \(`Task.Run( () => { DoSomeWork(1000);});`\) se ejecuta en un subproceso en el [grupo de subprocesos](http://msdn.microsoft.com/en-us/library/system.threading.threadpool.aspx) de la aplicación. Como esta llamada trata de actualizar la interfaz de usuario desde un subproceso ajeno a la interfaz de usuario, la instrucción lanza una<xref:System.InvalidOperationException>.  
  
 **Aplicaciones de la Tienda y WPF**  
  
> [!NOTE]
>  En las aplicaciones del teléfono de la Tienda, se lanza una <xref:System.Exception> en lugar de la <xref:System.InvalidOperationException>, más específica.  
  
 **Mensajes de excepción:**  
  
|||  
|-|-|  
|Aplicaciones de WPF|Información adicional: el subproceso que realiza la llamada no puede acceder a este objeto porque el propietario es otro subproceso.|  
|Aplicaciones de la Tienda|Información adicional: la aplicación llamó a una interfaz que se aplanó para un subproceso diferente. \(Excepción de HRESULT: 0x8001010E \(RPC\_E\_WRONG\_THREAD\)\)|  
  
```c#  
private async void ThreadsExampleBtn_Click(object sender, RoutedEventArgs e) { TextBox1.Text = String.Empty; TextBox1.Text = "Simulating work on UI thread.\n"; DoSomeWork(20); TextBox1.Text += "Simulating work on non-UI thread.\n"; await Task.Run(() => DoSomeWork(1000)); TextBox1.Text += "ThreadsExampleBtn_Click completes. "; } private void DoSomeWork(int msOfWork) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msg = String.Format("Some work completed in {0} ms on UI thread. \n", msOfWork); TextBox1.Text += msg; }  
```  
  
 **Aplicaciones de Windows Forms**  
  
 **Mensaje de excepción:**  
  
-   Información adicional: operación no válida a través de subprocesos \(se tuvo acceso al control "TextBox1" desde un subproceso distinto a aquel en que lo creó\).  
  
```c#  
private async void ThreadsExampleBtn_Click(object sender, EventArgs e) { TextBox1.Text = String.Empty; var tbLinesList = new List<string>() {"Simulating work on UI thread."}; TextBox1.Lines = tbLinesList.ToArray(); DoSomeWork(20, tbLinesList); tbLinesList.Add("Simulating work on non-UI thread."); TextBox1.Lines = tbLinesList.ToArray(); await Task.Run(() => DoSomeWork(1000, tbLinesList)); tbLinesList.Add("ThreadsExampleBtn_Click completes."); TextBox1.Lines = tbLinesList.ToArray(); } private void DoSomeWork(int msOfWork, List<string> tbLinesList) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { }; { // spin }; // report completion var msg = String.Format("Some work completed in {0} ms on UI thread. \n", msOfWork); tbLinesList.Add(msg); TextBox1.Lines = tbLinesList.ToArray(); }  
```  
  
 ![Volver al principio](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [En este artículo](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Un método que se ejecuta en un subproceso ajeno a la interfaz de usuario actualiza la interfaz de usuario](#BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI)  
  
###  <a name="BKMK_Avoiding_InvalidOperationExceptions_on_non_UI_threads"></a> Evitar excepciones InvalidOperationException en subprocesos ajenos a la interfaz de usuario  
 Los marcos de la interfaz de usuario de Windows implementan un patrón *distribuidor* que incluye un método para comprobar si se está ejecutando una llamada a un miembro de un elemento de interfaz de usuario en el subproceso de la interfaz de usuario, y otros métodos para programar la llamada en el subproceso de la interfaz de usuario.  
  
 **Aplicaciones de WPF**  
  
 En las aplicaciones de WPF, utilice uno de los métodos <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=fullName> para ejecutar un delegado en el subproceso de la interfaz de usuario. Si es necesario, utilice el método <xref:System.Windows.Threading.Dispatcher.CheckAccess%2A?displayProperty=fullName> para determinar si un método se está ejecutando en un subproceso ajeno a la interfaz de usuario.  
  
```c#  
private void DoSomeWork(int msOfWork) { var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msgFormat = "Some work completed in {0} ms on {1}UI thread.\n"; var msg = String.Empty; if (TextBox1.Dispatcher.CheckAccess()) { msg = String.Format(msgFormat, msOfWork, String.Empty); TextBox1.Text += msg; } else { msg = String.Format(msgFormat, msOfWork, "non-"); Action act = ()=> {TextBox1.Text += msg;}; TextBox1.Dispatcher.Invoke(act); } }  
  
```  
  
 **Aplicaciones de Windows Forms**  
  
 En las aplicaciones de Windows Forms, use el método <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> para ejecutar un delegado que actualice el subproceso de la interfaz de usuario. Si es necesario, utilice la propiedad <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> para determinar si un método se está ejecutando en un subproceso ajeno a la interfaz de usuario.  
  
```c#  
private void DoSomeWork(int msOfWork, List<string> tbLinesList) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msgFormat = "Some work completed in {0} ms on {1}UI thread.\n"; var msg = String.Empty; if (TextBox1.InvokeRequired) { msg = String.Format(msgFormat, msOfWork, "non-"); tbLinesList.Add(msg); Action act = () => TextBox1.Lines = tbLinesList.ToArray(); TextBox1.Invoke( act ); } else { msg = String.Format(msgFormat, msOfWork, String.Empty); tbLinesList.Add(msg); TextBox1.Lines = tbLinesList.ToArray(); } }  
```  
  
 **Aplicaciones de la Tienda**  
  
 En las aplicaciones de la Tienda, use el método <xref:Windows.UI.Core.CoreDispatcher.RunAsync%2A?displayProperty=fullName> para ejecutar un delegado que actualice el subproceso de la interfaz de usuario. Si es necesario, utilice la propiedad <xref:Windows.UI.Core.CoreDispatcher.HasThreadAccess%2A> para determinar si un método se está ejecutando en un subproceso ajeno a la interfaz de usuario.  
  
```c#  
private void DoSomeWork(int msOfWork) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msgFormat = "Some work completed in {0} ms on {1}UI thread.\n"; var msg = String.Empty; if (TextBox1.Dispatcher.HasThreadAccess) { msg = String.Format(msgFormat, msOfWork, String.Empty); TextBox1.Text += msg; } else { msg = String.Format(msgFormat, msOfWork, "non-"); TextBox1.Dispatcher.RunAsync(Windows.UI.Core.CoreDispatcherPriority.Normal,()=> {TextBox1.Text += msg;}); } }  
```  
  
 ![Volver al principio](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [En este artículo](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Un método que se ejecuta en un subproceso ajeno a la interfaz de usuario actualiza la interfaz de usuario](#BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI)  
  
##  <a name="BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating"></a> Una declaración de un bloque de foreach \(For Each en Visual Basic\) cambia la colección que está iterando  
 [Provocación de una excepción InvalidOperationException con foreach](#BKMK_Causing_an_InvalidOperationException_with_foreach)  **&#124;**  [Evitar excepciones InvalidOperationException en bucles](#BKMK_Avoiding_InvalidOperationExceptions_in_loops)  
  
 Las instrucciones [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) \([For Each](/dotnet/visual-basic/language-reference/statements/for-each-next-statement) en Visual Basic\) repiten un grupo de instrucciones incrustadas por cada elemento de una matriz o una colección que implementa la interfaz <xref:System.Collections.IEnumerable?displayProperty=fullName> o <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>. La instrucción `foreach` se utiliza para procesar una iteración en la colección para leer y modificar los elementos, pero no se puede usar para agregar o quitar elementos de la colección. Si agrega o quita elementos de la colección de origen de una instrucción foreach, se lanza una <xref:System.InvalidOperationException>.  
  
###  <a name="BKMK_Causing_an_InvalidOperationException_with_foreach"></a> Provocación de una excepción InvalidOperationException con foreach  
 En este ejemplo, se lanza una <xref:System.InvalidOperationException> cuando la instrucción `numList.Add(5);` trata de modificar la lista del bloque foreach.  
  
 **Mensaje de excepción:**  
  
-   Información adicional: colección modificada; puede que no se ejecute la operación de enumeración.  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
 ![Volver al principio](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [En este artículo](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Una declaración de un bloque de foreach (For Each en Visual Basic) cambia la colección que está iterando](#BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating)  
  
###  <a name="BKMK_Avoiding_InvalidOperationExceptions_in_loops"></a> Evitar excepciones InvalidOperationException en bucles  
  
> [!IMPORTANT]
>  Agregar elementos a una lista o quitarlos de una lista mientras está iterando por la colección puede tener efectos secundarios no deseados y difíciles de predecir. Si es posible, debe mover la operación fuera de la iteración.  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
 Si la situación requiere que agregue elementos a una lista o que quite elementos de una lista al iterar una colección, utilice un bucle [for](/dotnet/csharp/language-reference/keywords/for) \([For](/dotnet/visual-basic/language-reference/statements/for-next-statement) en Visual Basic\):  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
 ![Volver al principio](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [En este artículo](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Una declaración de un bloque de foreach (For Each en Visual Basic) cambia la colección que está iterando](#BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating)  
  
##  <a name="BKMK_A_Nullable_T_that_is_null_is_cast_to_T"></a> Un Nullable\<T\> que es NULL se convierte en T  
 [Provocación de una excepción InvalidOperationException con una conversión no válida](#BKMK_Causing_an_InvalidOperationException_with_an_invalid_cast)  **&#124;**  [Evitar una excepción InvalidOperationException por una conversión incorrecta](#BKMK_Avoiding_InvalidOperationException_from_a_bad_cast)  
  
 Si convierte una estructura <xref:System.Nullable%601> que es `null` \(`Nothing` en Visual Basic\) en su tipo subyacente, se lanzará una excepción <xref:System.InvalidOperationException>.  
  
###  <a name="BKMK_Causing_an_InvalidOperationException_with_an_invalid_cast"></a> Provocación de una excepción InvalidOperationException con una conversión no válida  
 En este método, cuando el método Select convierte un elemento NULL de dbQueryResults en un int, se lanza una <xref:System.InvalidOperationException>.  
  
 **Mensaje de excepción:**  
  
-   Información adicional: e objeto que acepta valores Null debe tener un valor.  
  
```c#  
private void MapQueryResults() { var dbQueryResults = new int?[] { 1, 2, null, 4 }; var ormMap = dbQueryResults.Select(nullableInt => (int)nullableInt); //display map list foreach (var num in ormMap) { Console.Write("{0} ", num); } Console.WriteLine(); }  
  
```  
  
 ![Volver al principio](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [En este artículo](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Un Nullable&lt;T&gt; que es NULL se convierte en T](#BKMK_A_Nullable_T_that_is_null_is_cast_to_T)  
  
###  <a name="BKMK_Avoiding_InvalidOperationException_from_a_bad_cast"></a> Evitar una excepción InvalidOperationException por una conversión incorrecta  
 Para evitar <xref:System.InvalidOperationException>:  
  
-   Utilice la propiedad <xref:System.Nullable%601.HasValue%2A?displayProperty=fullName> para seleccionar solamente los elementos que no son NULL.  
  
-   Utilice uno de los métodos <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=fullName> sobrecargados para proporcionar un valor predeterminado a un elemento NULL.  
  
 **Ejemplo de Nullable\<T\>.HasValue**  
  
```c#  
private void MapQueryResults() { var dbQueryResults = new int?[] { 1, 2, null, 4 }; var ormMap = dbQueryResults .Where(nulllableInt => nulllableInt.HasValue) .Select(num => (int)num); //display map list foreach (var num in ormMap) { Console.Write("{0} ", num); } Console.WriteLine(); // handle nulls Console.WriteLine("{0} nulls encountered in dbQueryResults", dbQueryResults.Where(nullableInt => !nullableInt.HasValue).Count()); }  
```  
  
 **Ejemplo de Nullable\<T\>.GetValueOrDefault**  
  
 En este ejemplo, utilizamos <xref:System.Nullable%601.GetValueOrDefault%28%600%29> para especificar un valor predeterminado que está fuera de los valores esperados devueltos por `dbQueryResults`.  
  
```c#  
private void MapQueryResults() { var dbQueryResults = new int?[] { 1, 2, null, 4 }; var nullFlag = int.MinValue; var ormMap = dbQueryResults.Select(nullableInt => nullableInt.GetValueOrDefault(nullFlag)); // handle nulls Console.WriteLine("'{0}' indicates a null database value.", nullFlag); foreach (var num in ormMap) { Console.Write("{0} ", num); } Console.WriteLine(); }  
  
```  
  
 ![Volver al principio](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [En este artículo](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Un Nullable&lt;T&gt; que es NULL se convierte en T](#BKMK_A_Nullable_T_that_is_null_is_cast_to_T)  
  
##  <a name="BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection"></a> Se llama a un método System.Linq.Enumerable en una colección vacía  
 Los métodos <xref:System.Linq.Enumerable><xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.First%2A>, <xref:System.Linq.Enumerable.Single%2A> y <xref:System.Linq.Enumerable.SingleOrDefault%2A> realizan operaciones en una secuencia y devuelven un único resultado.  
  
 Algunas sobrecargas de estos métodos lanzan una excepción <xref:System.InvalidOperationException> cuando la secuencia está vacía \(otras sobrecargas devuelven `null` \(`Nothing` en Visual Basic\).<xref:System.Linq.Enumerable.SingleOrDefault%2A> también lanza <xref:System.InvalidOperationException> cuando la secuencia contiene más de un elemento.  
  
> [!TIP]
>  La mayoría de los métodos <xref:System.Linq.Enumerable> de los que se habla en esta sección están sobrecargados. Asegúrese de que comprende el comportamiento de la sobrecarga que elija.  
  
 **Mensajes de excepción:**  
  
 [Métodos Aggregate, Average, Last, Max y Min](#BKMK_Aggregate_Average_Last_Max_and_Min_methods)  **&#124;**  [Métodos First y FirstOrDefault](#BKMK_First_and_FirstOrDefault_methods)  **&#124;**  [Métodos Single y SingleOrDefault](#BKMK_Single_and_SingleOrDefault_methods)  
  
###  <a name="BKMK_Aggregate_Average_Last_Max_and_Min_methods"></a> Métodos Aggregate, Average, Last, Max y Min  
  
-   Información adicional: la secuencia no contiene elementos  
  
 **Provocación de una excepción InvalidOperationException con Average**  
  
 En este ejemplo, el siguiente método lanza una <xref:System.InvalidOperationException> cuando llama al método <xref:System.Linq.Enumerable.Average%2A> porque la expresión Linq devuelve una secuencia que no contiene elementos mayores que 4.  
  
```c#  
private void FindAverageOfNumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; var avg = dbQueryResults.Where(num => num > 4).Average(); Console.WriteLine("The average value numbers greater than 4 in the returned records is {0}", avg); }  
```  
  
 Cuando utiliza uno de estos métodos sin comprobar si hay una secuencia vacía, está asumiendo de forma implícita que la secuencia no está vacía y que una secuencia vacía es un suceso inesperado. En los casos en los que, efectivamente, presuponga que la secuencia no estará vacía, será adecuado capturar o lanzar la excepción.  
  
 **Evitar una excepción InvalidOperationException causada por una secuencia vacía**  
  
 Utilice uno de los métodos <xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName> para comprobar si la secuencia está vacía.  
  
> [!TIP]
>  Usar <xref:System.Linq.Enumerable.Any%2A> puede mejorar el rendimiento de la comprobación si es posible que la secuencia para obtener el promedio contenga un gran número de elementos, o si la operación que genera la secuencia es costosa.  
  
```c#  
private void FindAverageOfNumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; var moreThan4 = dbQueryResults.Where(num => num > 4); if(moreThan4.Any()) { var msgFormat = "The average value numbers greater than 4 in the returned records is {0}"; Console.WriteLine(msgFormat, moreThan4.Average()); } else { // handle empty collection Console.WriteLine("There are no values greater than 4 in the ecords."); } }  
  
```  
  
 ![Volver al principio](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [En este artículo](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Se llama a un método System.Linq.Enumerable en una colección vacía](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
###  <a name="BKMK_First_and_FirstOrDefault_methods"></a> Métodos First y FirstOrDefault  
 <xref:System.Linq.Enumerable.First%2A> devuelve el primer elemento de una secuencia o lanza una <xref:System.InvalidOperationException> si la secuencia está vacía.  Puede llamar al método <xref:System.Linq.Enumerable.FirstOrDefault%2A> en lugar de a <xref:System.Linq.Enumerable.First%2A> para devolver un valor especificado o predeterminado en vez de lanzar la excepción.  
  
> [!NOTE]
>  En .NET Framework, los tipos tienen un concepto de los valores predeterminados. Por ejemplo, para un tipo de referencia cualquiera, el valor predeterminado es NULL, y para un tipo entero, es cero. Vea [Tabla de valores predeterminados](/dotnet/csharp/language-reference/keywords/default-values-table)  
  
 **Provocación de una excepción InvalidOperationException con First**  
  
 <xref:System.Linq.Enumerable.First%2A> es un método de optimización que devuelve el primer elemento de una secuencia que cumple una condición especificada. Si no se encuentra ningún elemento que cumpla la condición, los métodos lanzan una excepción <xref:System.InvalidOperationException>.  
  
 En este ejemplo, el método `First` lanza la excepción porque `dbQueryResults` no contiene ningún elemento mayor que 4.  
  
 **Mensaje de excepción:**  
  
-   Información adicional: la secuencia no contiene ningún elemento coincidente  
  
```c#  
private void FindANumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; var firstNum = dbQueryResults.First(n=> n > 4); var msgFormat = "{0} is an element of dbQueryResults that is greater than 4"; Console.WriteLine(msgFormat, firstNum); }  
  
```  
  
 **Evitar una excepción con FirstOrDefault**  
  
 Puede utilizar uno de los métodos <xref:System.Linq.Enumerable.FirstOrDefault%2A> en lugar de <xref:System.Linq.Enumerable.First%2A> para comprobar que la secuencia `firstNum` contiene al menos un elemento. Si la consulta no encuentra ningún elemento que cumpla la condición, devuelve un valor especificado o predeterminado. Puede comprobar el valor devuelto para determinar si se encontró algún elemento.  
  
> [!NOTE]
>  Si el valor predeterminado del tipo es un elemento válido en la secuencia, puede ser más complicado implementar el uso de <xref:System.Linq.Enumerable.FirstOrDefault%2A>.  
  
```c#  
private void FindANumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; // default(object) == null var firstNum = dbQueryResults.FirstOrDefault(n => n > 4); if (firstNum != 0) { var msgFormat = "{0} is an element of dbQueryResults that is greater than 4"; Console.WriteLine(msgFormat, firstNum); } else { // handle default case Console.WriteLine("No element of dbQueryResults is greater than 4."); } }  
  
```  
  
 ![Volver al principio](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [En este artículo](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Se llama a un método System.Linq.Enumerable en una colección vacía](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
###  <a name="BKMK_Single_and_SingleOrDefault_methods"></a> Métodos Single y SingleOrDefault  
 Los métodos <xref:System.Linq.Enumerable.Single%2A?displayProperty=fullName> devuelven el único elemento de una secuencia, o el único elemento de una secuencia que supera una prueba especificada.  
  
 Si no hay ningún elemento en la secuencia, o si hay más de un elemento en la secuencia, el método lanza una excepción <xref:System.InvalidOperationException>.  
  
 Puede usar <xref:System.Linq.Enumerable.SingleOrDefault%2A> para devolver un valor especificado o predeterminado en lugar de lanzar la excepción cuando la secuencia no contiene ningún elemento. Aun así, <xref:System.Linq.Enumerable.SingleOrDefault%2A> lanza una <xref:System.InvalidOperationException> cuando la secuencia contiene más de un elemento que coincide con el predicado de selección.  
  
> [!NOTE]
>  En .NET Framework, los tipos tienen un concepto de los valores predeterminados. Por ejemplo, para un tipo de referencia cualquiera, el valor predeterminado es NULL, y para un tipo entero, es cero. Vea [Tabla de valores predeterminados](/dotnet/csharp/language-reference/keywords/default-values-table)  
  
 **Provocación de excepciones InvalidOperationException con Single**  
  
 En este ejemplo, `singleObject` lanza una <xref:System.InvalidOperationException> porque `dbQueryResults` no contiene ningún elemento mayor que 4.  
  
 **Mensaje de excepción:**  
  
-   Información adicional: la secuencia no contiene ningún elemento coincidente  
  
```c#  
private void FindTheOnlyNumberGreaterThan4() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var singleObject = dbQueryResults.Single(obj => (int)obj > 4); // display results var msgFormat = "{0} is the only element of dbQueryResults that is greater than 4"; Console.WriteLine(msgFormat, singleObject); }  
  
```  
  
 **Provocación de excepciones InvalidOperationException con Single o SingleOrDefault**  
  
 En este ejemplo, `singleObject` lanza una <xref:System.InvalidOperationException> porque `dbQueryResults` contiene más de un elemento mayor que 2.  
  
 **Mensaje de excepción:**  
  
-   Información adicional: la secuencia contiene más de un elemento coincidente  
  
```c#  
private void FindTheOnlyNumberGreaterThan2() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var singleObject = dbQueryResults.SingleOrDefault(obj => (int)obj > 2); if (singleObject != null) { var msgFormat = "{0} is the only element of dbQueryResults that is greater than 2"; Console.WriteLine(msgFormat, singleObject); } else { // handle empty collection Console.WriteLine("No element of dbQueryResults is greater than 2."); } }  
  
```  
  
 **Evitar excepciones InvalidOperationException con Single**  
  
 Usar <xref:System.Linq.Enumerable.Single%2A> y <xref:System.Linq.Enumerable.SingleOrDefault%2A> también sirve como documentación de sus intenciones.<xref:System.Linq.Enumerable.Single%2A> implica claramente que espera que la condición devuelva un solo resultado y no más.<xref:System.Linq.Enumerable.SingleOrDefault%2A> declara que espera uno o cero resultados, pero no más. Cuando estas condiciones no son válidas, es adecuado lanzar o capturar la <xref:System.InvalidOperationException>. Sin embargo, si es de esperar que las condiciones no válidas se produzcan con cierta frecuencia, debe plantearse usar otros métodos <xref:System.Linq.Enumerable>, como <xref:System.Linq.Enumerable.First%2A> o <xref:System.Linq.Enumerable.Where%2A>, para generar los resultados.  
  
 Durante el desarrollo, puede usar uno de los métodos <xref:System.Diagnostics.Debug.Assert%2A> para comprobar sus suposiciones. En este ejemplo, el código resaltado hace que el depurador se interrumpa y muestra un cuadro de diálogo de aserción durante el desarrollo. La aserción se quita en el código de la versión de lanzamiento y, si los resultados no son válidos, se lanzará cualquier <xref:System.Linq.Enumerable.Single%2A>.  
  
> [!NOTE]
>  Si usa <xref:System.Linq.Enumerable.Take%2A> y establece su parámetro `count` en 2, limitará la secuencia devuelta a dos elementos como máximo. Esta secuencia incluye todos los casos que tiene que comprobar \(0, 1 y más de 1 elementos\) y puede mejorar el rendimiento de la comprobación en los casos en los que es posible que la secuencia contenga un gran número de elementos, o si la operación que genera la secuencia es costosa.  
  
```c#  
private void FindTheOnlyNumberGreaterThan4() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var moreThan4 = dbQueryResults.Where(obj => (int)obj > 4).Take(2); System.Diagnostics.Debug.Assert(moreThan4.Count() == 1,String.Format("moreThan4.Count() == 1; Actual count: {0}", moreThan4.Count())); // do not handle exceptions in release code Console.WriteLine("{0} is the only element of dbQueryResults that is greater than 4", moreThan4.Single()); }  
  
```  
  
 Si quiere evitar la excepción y, al mismo tiempo, controlar los estados no válidos en el código de la versión de lanzamiento, puede modificar la técnica que describimos arriba. En este ejemplo, el método responde al número de elementos devueltos por `moreThan2` en la instrucción switch.  
  
```c#  
private void FindTheOnlyNumberGreaterThan2() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var moreThan2 = dbQueryResults.TakeWhile(obj => (int)obj > 2).Take(2); switch(moreThan2.Count()) { case 1: // success var msgFormat = "{0} is the only element of dbQueryResults that is greater than 2"; Console.WriteLine(msgFormat, moreThan2.Single()); break; case 0: // handle empty collection Console.WriteLine("No element of the dbQueryResults are greater than 4."); break; default: // count > 1 // handle more than one element Console.WriteLine("More than one element of dbQueryResults is greater than 4"); break; } }  
  
```  
  
 ![Volver al principio](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [En este artículo](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Se llama a un método System.Linq.Enumerable en una colección vacía](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
##  <a name="BKMK_Related_articles"></a> Artículos relacionados  
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
  
 ![Volver al principio](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [En este artículo](#BKMK_In_this_article)