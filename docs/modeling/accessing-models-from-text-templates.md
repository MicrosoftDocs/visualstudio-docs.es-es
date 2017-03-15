---
title: "Acceso a modelos a partir de plantillas de texto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "plantillas de texto, acceso a modelos"
ms.assetid: cf65395a-0ca3-4826-89c7-b1869562685c
caps.latest.revision: 33
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 33
---
# Acceso a modelos a partir de plantillas de texto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilizando plantillas de texto, puede crear archivos de informe, los archivos de código fuente, y otros archivos de texto basados en modelos específicos del lenguaje.  Para obtener información básica sobre las plantillas de texto, vea [Code Generation and T4 Text Templates](../modeling/code-generation-and-t4-text-templates.md).  Las plantillas de texto funcionarán en modo experimental cuando depure DSL, y también funcionará en un equipo en el que se ha implementado ADSL.  
  
> [!NOTE]
>  Cuando se crea una solución ADSL, los archivos de **\*.tt** de plantilla de texto de muestra se representan en el proyecto de depuración.  Al cambiar los nombres de clases de dominio, estas plantillas dejarán.  Sin embargo, incluyen las directivas básicas que necesita, y se proporcionan ejemplos que puede actualizar para coincidir ADSL.  
  
 Para tener acceso a un modelo de una plantilla de texto:  
  
-   Establezca la propiedad heredan de la directiva de plantilla a <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>.  Esto proporciona acceso al almacén.  
  
-   Especifique los procesadores de directivas para ADSL al que desea obtener acceso.  Esto carga los ensamblados para ADSL para poder utilizar las clases, propiedades, y relaciones de dominio en el código de plantilla de texto.  También carga el archivo del modelo especificado.  
  
 Un archivo de `.tt` similar al ejemplo siguiente se crea en el proyecto de depuración cuando se crea una nueva solución de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de plantilla de lenguaje ADSL Minimal.  
  
```  
<#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
<#@ output extension=".txt" #>  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
  
This text will be output directly.  
  
This is the name of the model: <#= this.ModelRoot.Name #>  
  
Here is a list of elements in the model:  
<#  
  // When you change the DSL Definition, some of the code below may not work.  
  foreach (ExampleElement element in this.ExampleModel.Elements)  
  {#>  
<#= element.Name #>  
<#      
  }  
#>  
  
```  
  
 Observe los siguientes sobre esta plantilla:  
  
-   La plantilla puede utilizar clases, propiedades, y las relaciones de dominio que se define en la definición del ADSL.  
  
-   La plantilla carga el archivo modelo especificado en la propiedad de `requires` .  
  
-   Una propiedad de `this` contiene el elemento raíz.  Desde allí, el código puede navegar a otros elementos del modelo.  El nombre de la propiedad suele ser igual que la clase de dominio raíz ADSL.  en este ejemplo, es `this.ExampleModel`.  
  
-   Aunque el lenguaje en el que se escriben los fragmentos de código es C\#, puede generar el texto de la clase.  Puede escribir también el código en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] agregando la propiedad `language="VB"` a la directiva de `template` .  
  
-   para depurar la plantilla, agregue `debug="true"` a la directiva de `template` .  La plantilla se abrirá en otra instancia de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] si se produce una excepción.  Si desea interrumpir el depurador en un momento concreto en el código, inserte la instrucción `System.Diagnostics.Debugger.Break();`  
  
     Para obtener más información, vea [Debugging a T4 Text Template](../modeling/debugging-a-t4-text-template.md).  
  
## Sobre el procesador de directivas ADSL  
 La plantilla puede utilizar las clases de dominio que se define en la definición del ADSL.  Esto es causada por una directiva que aparece normalmente cerca del inicio de la plantilla.  en el ejemplo anterior, es el siguiente.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
```  
  
 El nombre de la directiva \( `MyLanguage`, en este ejemplo\) es derivado del nombre del ADSL.  Invoca *un procesador de directivas* que se genera como parte del ADSL.  Puede buscar el código fuente en **Dsl\\GeneratedCode\\DirectiveProcessor.cs**.  
  
 El procesador de directivas ADSL realiza dos tareas principales:  
  
-   Inserta eficazmente directivas de ensamblado e importación en la plantilla que hace referencia ADSL.  Esto permite utilizar las clases de dominio en el código de plantilla.  
  
-   Carga el archivo especificado en el parámetro de `requires` , y establece una propiedad en `this` que haga referencia al elemento raíz del modelo cargado.  
  
## Validar el modelo antes de ejecutar la plantilla  
 Puede hacer que el modelo que se va a validar antes de que se ejecute la plantilla.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>  
  
```  
  
 Observe que:  
  
1.  los parámetros de `filename` y de `validation` se separan con “; ” y no debe haber otros separadores o espacios.  
  
2.  La lista de categorías de validación determina que los métodos de validación se ejecutarán.  Varias categorías deben separarse con “&#124;” y no debe haber otros separadores o espacios.  
  
 Si se produce un error, se notificará en la ventana de errores, y el archivo de resultados contendrá un mensaje de error.  
  
##  <a name="Multiple"></a> Varios modelos de acceso de una plantilla de texto  
  
> [!NOTE]
>  Este método permite leer varios modelos en la misma plantilla pero no admite las referencias de ModelBus.  Para leer los modelos que están ligados por las referencias de ModelBus, vea [Usar ModelBus de Visual Studio en plantillas de texto](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 Si desea tener acceso a más de un modelo de la misma plantilla de texto, debe llamar al procesador de directivas generado una vez para cada modelo.  Debe especificar el nombre de archivo de cada modelo en el parámetro de `requires` .  Debe especificar los nombres que desea utilizar para la clase de dominio raíz en el parámetro de `provides` .  Debe especificar valores diferentes para los parámetros de `provides` en cada una de las llamadas directivas.  Por ejemplo, suponga que tiene tres archivos de modelo denominados Library.xyz, School.xyz, y Work.xyz.  Para tener acceso a la misma plantilla de texto, debe escribir tres llamadas directivas que se similares los siguientes.  
  
```  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>  
```  
  
> [!NOTE]
>  Este código de ejemplo para un lenguaje basado en la plantilla de solución de lenguaje mínimos.  
  
 Para tener acceso a los modelos en la plantilla de texto, ahora puede escribir código similar al código del ejemplo siguiente.  
  
```c#  
<#  
foreach (ExampleElement element in this.LibraryModel.Elements)  
...  
foreach (ExampleElement element in this.SchoolModel.Elements)  
...  
foreach (ExampleElement element in this.WorkModel.Elements)  
...  
#>  
```  
  
```vb#  
<#  
For Each element As ExampleElement In Me.LibraryModel.Elements  
...  
For Each element As ExampleElement In Me.SchoolModel.Elements  
...  
For Each element As ExampleElement In Me.WorkModel.Elements  
...  
#>  
```  
  
## La carga modela dinámicamente  
 Si desea determinar en tiempo de ejecución que modela para cargar, puede cargar un archivo modelo dinámicamente en el código de programa, en lugar de utilizar la directiva DSL\-específica.  
  
 Sin embargo, una de las funciones de la directiva DSL\-específica es importar el espacio de nombres ADSL, de modo que el código de plantilla puede utilizar las clases de dominio definido en ese ADSL.  Porque no se utiliza la directiva, debe agregar **\<assembly\>** y las directivas de **\<import\>** para todos los modelos que puede cargar.  Esto es fácil si los distintos modelos que puede cargar son todas las instancias del mismo ADSL.  
  
 Para cargar el archivo, el método más eficaz es utilizar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus.  En un escenario típico, la plantilla de texto utilizará una directiva DSL\-específica para cargar el primer modelo de la forma habitual.  Que el modelo contendrá referencias de ModelBus a otro modelo.  Puede utilizar ModelBus para abrir el modelo hace referencia y tener acceso a un elemento determinado.  Para obtener más información, vea [Usar ModelBus de Visual Studio en plantillas de texto](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 En un escenario menos habitual, puede que desee abrir un archivo modelo para el que sólo tiene un nombre de archivo, y que no esté en el proyecto actual de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  En este caso, puede abrir el archivo mediante la técnica descrita en [Cómo: Abrir un modelo desde un archivo en el código del programa](../modeling/how-to-open-a-model-from-file-in-program-code.md).  
  
## Generar varios archivos de una plantilla  
 Si desea generar varios archivos \(por ejemplo, generar un archivo independiente para cada elemento de un modelo, hay varios posibles enfoques.  De forma predeterminada, solo un archivo se muestra de cada archivo de plantilla.  
  
### dividir un archivo largo  
 En este método, se usa una plantilla para generar un único archivo, separados por un delimitador.  A continuación dividió el archivo en sus componentes.  Hay dos plantillas, una para generar el archivo único, y otra para dividirlo.  
  
 **LoopTemplate.t4** genera el único archivo largo.  Observe que su extensión es “.t4”, porque no se debería procesar directamente al hacer clic en **Transformar todas las plantillas**.  esta plantilla toma un parámetro, que especifica la cadena de delimitador que separa los segmentos:  
  
```  
<#@ template ninherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
<#@ parameter name="delimiter" type="System.String" #>  
<#@ output extension=".txt" #>  
<#@ MyDSL processor="MyDSLDirectiveProcessor" requires="fileName='SampleModel.mydsl1';validation='open|load|save|menu'" #>  
<#  
  // Create a file segment for each element:  
  foreach (ExampleElement element in this.ExampleModel.Elements)   
  {   
    // First item is the delimiter:  
#>  
<#= string.Format(delimiter, element.Id) #>  
  
   Element: <#= element.Name #>  
<#  
   // Here you generate more content derived from the element.  
  }  
#>  
  
```  
  
 `LoopSplitter.tt` invoca `LoopTemplate.t4`, y después divide el archivo resultante en sus segmentos.  Observe que esta plantilla no tiene que ser una plantilla de modelado, porque no lee el modelo.  
  
```  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>  
<#@ import namespace="System.Runtime.Remoting.Messaging" #>  
<#@ import namespace="System.IO" #>  
  
<#  
  // Get the local path:  
  string itemTemplatePath = this.Host.ResolvePath("LoopTemplate.t4");  
  string dir = Path.GetDirectoryName(itemTemplatePath);  
  
  // Get the template for generating each file:  
  string loopTemplate = File.ReadAllText(itemTemplatePath);  
  
  Engine engine = new Engine();  
  
  // Pass parameter to new template:  
  string delimiterGuid = Guid.NewGuid().ToString();  
  string delimiter = "::::" + delimiterGuid + ":::";  
  CallContext.LogicalSetData("delimiter", delimiter + "{0}:::");   
  string joinedFiles = engine.ProcessTemplate(loopTemplate, this.Host);  
  
  string [] separateFiles = joinedFiles.Split(new string [] {delimiter}, StringSplitOptions.None);  
  
  foreach (string nameAndFile in separateFiles)   
  {   
     if (string.IsNullOrWhiteSpace(nameAndFile)) continue;  
     string[] parts = nameAndFile.Split(new string[]{":::"}, 2, StringSplitOptions.None);  
     if (parts.Length < 2) continue;  
#>  
 Generate: [<#= dir #>] [<#= parts[0] #>]  
<#  
     // Generate a file from this item:  
     File.WriteAllText(Path.Combine(dir, parts[0] + ".txt"), parts[1]);    
  }  
#>  
  
```