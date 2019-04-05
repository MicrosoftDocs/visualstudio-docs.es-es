---
title: Acceso a los modelos a partir de plantillas de texto | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, accessing models
ms.assetid: cf65395a-0ca3-4826-89c7-b1869562685c
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a1a2ddeb3ab46bba30a505782fdd18d7df49574d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58998841"
---
# <a name="accessing-models-from-text-templates"></a>Acceso a modelos a partir de plantillas de texto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mediante el uso de plantillas de texto, puede crear archivos de informe, archivos de código fuente y otros archivos de texto que se basan en modelos de lenguaje específico de dominio. Para obtener información básica acerca de las plantillas de texto, consulte [generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md). Las plantillas de texto funcionarán en modo experimental cuando se depura su DSL y también funcionará en un equipo en el que ha implementado el DSL.  
  
> [!NOTE]
>  Cuando crea una solución de DSL, la plantilla de texto de ejemplo  **\*.tt** archivos se generan en el proyecto de depuración. Al cambiar los nombres de las clases de dominio, estas plantillas dejarán de funcionar. No obstante, se incluyen las directivas básicas que necesita y proporcionan ejemplos que se pueden actualizar para que coincida con su DSL.  
  
 Para obtener acceso a un modelo desde una plantilla de texto:  
  
- Establezca la propiedad de heredar de la directiva de plantilla para <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>. Esto proporciona acceso a la Store.  
  
- Especifique los procesadores de directivas para el DSL que se desea tener acceso a. Esto carga los ensamblados para su DSL, por lo que puede usar sus clases de dominio, propiedades y relaciones en el código de la plantilla de texto. También carga el archivo de modelo que especifique.  
  
  Un `.tt` archivo similar al ejemplo siguiente se crea en el proyecto de depuración cuando se crea un nuevo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] solución desde la plantilla de lenguaje mínimo de DSL.  
  
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
  
 Tenga en cuenta los siguientes puntos acerca de esta plantilla:  
  
-   La plantilla puede usar las clases de dominio, propiedades y relaciones que ha definido en la definición de DSL.  
  
-   La plantilla carga el archivo de modelo que especifique en el `requires` propiedad.  
  
-   Una propiedad en `this` contiene el elemento raíz. Desde allí, el código puede navegar a otros elementos del modelo. El nombre de la propiedad suele ser el mismo que la clase de dominio raíz de su DSL. En este ejemplo, es `this.ExampleModel`.  
  
-   Aunque el lenguaje en el que se escriben los fragmentos de código es C#, puede generar el texto de cualquier tipo. Como alternativa, puede escribir el código [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] mediante la adición de la propiedad `language="VB"` a la `template` directiva.  
  
-   Para depurar la plantilla, agregue `debug="true"` a la `template` directiva. La plantilla se abrirá en otra instancia de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] si se produce una excepción. Si desea interrumpir el depurador en un momento concreto en el código, inserte la instrucción `System.Diagnostics.Debugger.Break();`  
  
     Para obtener más información, consulte [depurar una plantilla de texto T4](../modeling/debugging-a-t4-text-template.md).  
  
## <a name="about-the-dsl-directive-processor"></a>Sobre el procesador de directivas de DSL  
 La plantilla puede usar las clases de dominio que ha definido en la definición de DSL. Esto es el resultado de una directiva que normalmente aparece al principio de la plantilla. En el ejemplo anterior, es la siguiente.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
```  
  
 El nombre de la directiva ( `MyLanguage`, en este ejemplo) se deriva del nombre de su DSL. Invoca un *procesador de directivas* que se genera como parte de su DSL. Puede encontrar su código fuente en **Dsl\GeneratedCode\DirectiveProcessor.cs**.  
  
 El procesador de directivas de DSL realiza dos tareas principales:  
  
-   Inserta eficazmente ensamblado e importar directivas en la plantilla que hace referencia a su DSL. Esto le permite usar las clases de dominio en el código de plantilla.  
  
-   Carga el archivo que especifique en el `requires` parámetro y establece una propiedad `this` que hace referencia al elemento raíz del modelo cargado.  
  
## <a name="validating-the-model-before-running-the-template"></a>Validar el modelo antes de ejecutar la plantilla  
 Puede hacer que el modelo que se valida antes de ejecuta la plantilla.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>  
  
```  
  
 Tenga en cuenta que:  
  
1. El `filename` y `validation` los parámetros se separan con ";" y no debe haber ningún otro separadores o espacios.  
  
2. La lista de categorías de validación determina qué métodos de validación que se va a ejecutar. Varias categorías se deben separar con "&#124;" y no debe haber ningún otro separadores o espacios.  
  
   Si se encuentra un error, se le notificará en la ventana de errores y el archivo de resultados contendrá un mensaje de error.  
  
##  <a name="Multiple"></a> Acceso a varios modelos desde una plantilla de texto  
  
> [!NOTE]
>  Este método le permite leer varios modelos en la misma plantilla, pero no admite referencias de ModelBus. Para los modelos que intervinculadas por referencias de ModelBus, consulte [utilizando Visual Studio ModelBus en una plantilla de texto](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 Si desea tener acceso a más de un modelo desde la misma plantilla de texto, debe llamar una vez el procesador de directivas personalizadas para cada modelo. Debe especificar el nombre de archivo de cada modelo en el `requires` parámetro. Debe especificar los nombres que desea usar para la clase de dominio raíz en el `provides` parámetro. Debe especificar valores diferentes para el `provides` parámetros de cada una de las llamadas de la directiva. Por ejemplo, suponga que tiene tres archivos de modelo se denomina Library.xyz, School.xyz y Work.xyz. Para acceder a ellas desde la misma plantilla de texto, debe escribir tres llamadas de directiva similares a las siguientes.  
  
```  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>  
```  
  
> [!NOTE]
>  Este código de ejemplo es para un idioma que se basa en la plantilla de solución de lenguaje mínimo.  
  
 Para obtener acceso a los modelos en la plantilla de texto, ahora puede escribir código similar al código en el ejemplo siguiente.  
  
```csharp  
<#  
foreach (ExampleElement element in this.LibraryModel.Elements)  
...  
foreach (ExampleElement element in this.SchoolModel.Elements)  
...  
foreach (ExampleElement element in this.WorkModel.Elements)  
...  
#>  
```  
  
```vb  
<#  
For Each element As ExampleElement In Me.LibraryModel.Elements  
...  
For Each element As ExampleElement In Me.SchoolModel.Elements  
...  
For Each element As ExampleElement In Me.WorkModel.Elements  
...  
#>  
```  
  
## <a name="loading-models-dynamically"></a>Cargar dinámicamente los modelos  
 Si desea determinar en tiempo de ejecución qué modelos de carga, puede cargar dinámicamente un archivo de modelo en el código del programa, en lugar de usar la directiva específica de DSL.  
  
 Sin embargo, una de las funciones de la directiva de DSL específica consiste en importar el espacio de nombres DSL, para que el código de plantilla puede utilizar las clases de dominio definidas en ese DSL. Dado que no usa la directiva, debe agregar  **\<ensamblado >** y  **\<Importar >** directivas para todos los modelos que se pueden cargar. Esto es fácil si son de los distintos modelos que podrían cargar todas las instancias del mismo DSL.  
  
 Para cargar el archivo, el método más eficaz es mediante [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus. En un escenario típico, la plantilla de texto usará una directiva específica de DSL para cargar el primer modelo de la forma habitual. Ese modelo contendría las referencias de ModelBus a otro modelo. Puede usar ModelBus para abrir el modelo que se hace referencia y tener acceso a un elemento determinado. Para obtener más información, consulte [utilizando Visual Studio ModelBus en una plantilla de texto](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 En un escenario menos habitual, es posible que desee abrir un archivo de modelo para el que tiene solo un nombre de archivo, y que podría no ser actual [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proyecto. En este caso, puede abrir el archivo mediante el uso de la técnica descrita en [Cómo: Abrir un modelo desde un archivo de código de programa](../modeling/how-to-open-a-model-from-file-in-program-code.md).  
  
## <a name="generating-multiple-files-from-a-template"></a>Generar varios archivos desde una plantilla  
 Si desea generar varios archivos: por ejemplo, para generar un archivo independiente para cada elemento en un modelo, hay varios enfoques posibles. De forma predeterminada, se genera un único archivo de cada archivo de plantilla.  
  
### <a name="splitting-a-long-file"></a>Dividir un archivo largo  
 En este método, usa una plantilla para generar un único archivo, separado por un delimitador. A continuación, había divida el archivo en sus partes. Hay dos plantillas, uno para generar el archivo único y el otro para dividirla.  
  
 **LoopTemplate.t4** genera el único archivo largo. Tenga en cuenta que su extensión de archivo es ".t4", porque no se debe procesar directamente al hacer clic en **Transformar todas las plantillas**. Esta plantilla toma un parámetro, que especifica la cadena de delimitador que separa los segmentos:  
  
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
  
 `LoopSplitter.tt` invoca `LoopTemplate.t4`y, a continuación, divide el archivo resultante en sus segmentos. Tenga en cuenta que esta plantilla no tiene que ser una plantilla de modelado, porque no leer el modelo.  
  
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
