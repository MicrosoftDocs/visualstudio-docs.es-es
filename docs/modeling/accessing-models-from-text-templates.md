---
title: Acceso a modelos a partir de plantillas de texto
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, accessing models
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 54bd5c4989f23b1de64a17bdf8d88ccebeb65a38
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31952331"
---
# <a name="accessing-models-from-text-templates"></a>Acceso a modelos a partir de plantillas de texto
Mediante el uso de plantillas de texto, puede crear archivos de informes, archivos de código fuente y otros archivos de texto que se basan en modelos de lenguaje específico de dominio. Para obtener información básica acerca de las plantillas de texto, consulte [generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md). Las plantillas de texto funcionarán en modo experimental cuando se depura el ADSL y también funcionará en un equipo en el que haya implementado el ADSL.

> [!NOTE]
>  Cuando se crea una solución DSL, la plantilla de texto de ejemplo  **\*.tt** archivos se generan en el proyecto de depuración. Al cambiar los nombres de las clases de dominio, estas plantillas ya no funcionará. No obstante, se incluyen las directivas básicas que necesita y se proporcionan ejemplos que se pueden actualizar para que coincida con el ADSL.

 Para obtener acceso a un modelo de una plantilla de texto:

-   Establecer la propiedad de herencia de la directiva de plantilla para <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>. Esto proporciona acceso al almacén.

-   Especifique procesadores de directivas para DSL que desea obtener acceso. Esto carga los ensamblados para ADSL, por lo que puede usar sus clases de dominio, propiedades y relaciones en el código de la plantilla de texto. También se carga el archivo de modelo que especifique.

 A `.tt` archivo similar al ejemplo siguiente se crea en el proyecto de depuración cuando se crea un nuevo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solución desde la plantilla de idioma mínimo ADSL.

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

-   La plantilla puede utilizar las clases de dominio, propiedades y relaciones que ha definido en la definición de DSL.

-   La plantilla carga el archivo de modelo que se especifica en el `requires` propiedad.

-   Una propiedad en `this` contiene el elemento raíz. A partir de ahí, el código puede navegar a otros elementos del modelo. El nombre de la propiedad suele ser la misma que la clase de dominio raíz del ADSL. En este ejemplo, es `this.ExampleModel`.

-   Aunque el idioma en el que se escriben los fragmentos de código es C#, puede generar el texto de cualquier tipo. O bien puede escribir el código [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] mediante la adición de la propiedad `language="VB"` a la `template` directiva.

-   Para depurar la plantilla, agregue `debug="true"` a la `template` directiva. La plantilla se abrirá en otra instancia de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] si se produce una excepción. Si desea interrumpir el depurador en un momento concreto en el código, la instrucción de inserción `System.Diagnostics.Debugger.Break();`

     Para obtener más información, consulte [depurar una plantilla de texto T4](../modeling/debugging-a-t4-text-template.md).

## <a name="about-the-dsl-directive-processor"></a>Acerca de cómo el procesador de directivas de DSL
 La plantilla puede utilizar las clases de dominio que ha definido en la definición DSL. Esto es el resultado de mediante una directiva que normalmente aparece al principio de la plantilla. En el ejemplo anterior, es la siguiente.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>
```

 El nombre de la directiva ( `MyLanguage`, en este ejemplo) se deriva del nombre del ADSL. Invoca un *procesador de directivas* que se genera como parte del ADSL. Puede encontrar su código fuente en **Dsl\GeneratedCode\DirectiveProcessor.cs**.

 El procesador de directivas de DSL realiza dos tareas principales:

-   Inserta eficazmente ensamblado e importar directivas en la plantilla que hace referencia el ADSL. Esto le permite usar las clases de dominio en el código de plantilla.

-   Carga el archivo que especifique en el `requires` parámetro y establece una propiedad `this` que hace referencia al elemento raíz del modelo cargado.

## <a name="validating-the-model-before-running-the-template"></a>Validar el modelo antes de ejecutar la plantilla
 También puede hacer que el modelo que se debe validar antes de ejecuta la plantilla.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>

```

 Tenga en cuenta que:

1.  El `filename` y `validation` parámetros se separan con ";" y no debe haber ningún otro separadores o espacios.

2.  La lista de categorías de validación determina qué métodos de validación se ejecutará. Varias categorías deben estar separados mediante "&#124;" y no debe haber ningún otro separadores o espacios.

 Si se encuentra un error, se incluirán en la ventana de errores y el archivo de resultados contendrá un mensaje de error.

##  <a name="Multiple"></a> Obtiene acceso a varios modelos desde una plantilla de texto

> [!NOTE]
>  Este método permite leer varios modelos en la misma plantilla pero no admite las referencias de ModelBus. Para los modelos que se entrelazan por ModelBus referencias, consulte [utilizando ModelBus de Microsoft Visual Studio en una plantilla de texto](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 Si desea tener acceso a más de un modelo de la misma plantilla de texto, debe llamar el procesador de directivas generado una vez para cada modelo. Debe especificar el nombre de archivo de cada modelo en el `requires` parámetro. Debe especificar los nombres que desea usar para la clase de dominio raíz en el `provides` parámetro. Debe especificar valores diferentes para el `provides` parámetros de cada una de las llamadas a la directiva. Por ejemplo, suponga que tiene tres archivos de modelo se denomina Library.xyz, School.xyz y Work.xyz. Para tener acceso a ellos desde la misma plantilla de texto, debe escribir tres llamadas de directiva similares a las siguientes.

```
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>
```

> [!NOTE]
>  Este código de ejemplo es para un idioma que se basa en la plantilla de solución de lenguaje mínima.

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

## <a name="loading-models-dynamically"></a>Cargar modelos de forma dinámica
 Si desea determinar en tiempo de ejecución qué modelos de carga, puede cargar dinámicamente un archivo de modelo en el código de programa, en lugar de usar la directiva de DSL específica.

 Sin embargo, una de las funciones de la directiva específica de DSL consiste en importar el espacio de nombres del ADSL, por lo que el código de plantilla puede utilizar las clases de dominio definidas en ese DSL. Dado que no se utiliza la directiva, debe agregar  **\<ensamblado >** y  **\<Importar >** directivas para todos los modelos que pueden cargar. Esto es fácil si los distintos modelos que podría cargar son todas las instancias de la misma DSL.

 Para cargar el archivo, el método más eficaz es mediante [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus. En un escenario típico, la plantilla de texto a usar una directiva específica de DSL para cargar el primer modelo de la manera habitual. Ese modelo contendría las referencias de ModelBus a otro modelo. Puede utilizar ModelBus para abrir el modelo que se hace referencia y tener acceso a un elemento determinado. Para obtener más información, consulte [utilizando ModelBus de Microsoft Visual Studio en una plantilla de texto](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 En un escenario menos habitual, puede abrir un archivo de modelo para los que tiene solo un nombre de archivo, y que podrían no ser actual [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyecto. En este caso, puede abrir el archivo mediante el uso de la técnica descrita en [Cómo: abrir un modelo de archivo en el código de programa](../modeling/how-to-open-a-model-from-file-in-program-code.md).

## <a name="generating-multiple-files-from-a-template"></a>Generar varios archivos de una plantilla
 Si desea generar varios archivos: por ejemplo, para generar un archivo independiente para cada elemento en un modelo, hay varios enfoques posibles. De forma predeterminada, se genera un único archivo de cada archivo de plantilla.

### <a name="splitting-a-long-file"></a>Dividir un archivo largo
 En este método, se utiliza una plantilla para generar un único archivo, separado por un delimitador. A continuación, había divida el archivo en sus partes. Hay dos plantillas, uno para generar el archivo único y el otro para dividirla.

 **LoopTemplate.t4** genera el archivo único largo. Observe que la extensión de archivo es ".t4", porque no se debe procesar directamente al hacer clic en **Transformar todas las plantillas**. Esta plantilla toma un parámetro, que especifica la cadena de delimitador que separa los segmentos:

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