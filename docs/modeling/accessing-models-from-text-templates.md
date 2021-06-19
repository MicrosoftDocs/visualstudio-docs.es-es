---
title: Acceso a modelos a partir de plantillas de texto
description: Obtenga información sobre cómo puede usar plantillas de texto para crear archivos de informe, archivos de código fuente y otros archivos de texto basados en modelos de lenguaje específicos del dominio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- text templates, accessing models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 05e21dacfe56f41f1d2c0da51659ab55203db1a0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389168"
---
# <a name="access-models-from-text-templates"></a>Acceso a modelos desde plantillas de texto

Mediante el uso de plantillas de texto, puede crear archivos de informe, archivos de código fuente y otros archivos de texto basados en modelos de lenguaje específicos del dominio. Para obtener información básica sobre las plantillas de texto, vea [Generación de código y Plantillas de texto T4.](../modeling/code-generation-and-t4-text-templates.md) Las plantillas de texto funcionarán en modo experimental al depurar el DSL y también funcionarán en un equipo en el que haya implementado el DSL.

> [!NOTE]
> Al crear una solución DSL, se generan archivos **\* .tt** de plantilla de texto de ejemplo en el proyecto de depuración. Al cambiar los nombres de las clases de dominio, estas plantillas ya no funcionarán. No obstante, incluyen las directivas básicas que necesita y proporcionan ejemplos que puede actualizar para que coincidan con el DSL.

 Para acceder a un modelo desde una plantilla de texto:

- Establezca la propiedad inherit de la directiva de plantilla en [Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation](/previous-versions/bb893209(v=vs.140)). Esto proporciona acceso a Store.

- Especifique los procesadores de directivas para el DSL al que desea acceder. Esto carga los ensamblados del DSL para que pueda usar sus clases de dominio, propiedades y relaciones en el código de la plantilla de texto. También carga el archivo de modelo que especifique.

  Se crea un archivo similar al ejemplo siguiente en el proyecto Depuración cuando se crea una nueva solución Visual Studio a partir de la `.tt` plantilla lenguaje mínimo DSL.

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

 Observe los siguientes puntos sobre esta plantilla:

- La plantilla puede usar las clases de dominio, las propiedades y las relaciones que definió en la definición de DSL.

- La plantilla carga el archivo de modelo que especifique en la `requires` propiedad .

- Una propiedad de `this` contiene el elemento raíz. Desde allí, el código puede navegar a otros elementos del modelo. El nombre de la propiedad suele ser el mismo que la clase de dominio raíz del DSL. En este ejemplo, es `this.ExampleModel`.

- Aunque el lenguaje en el que se escriben los fragmentos de código es C#, puede generar texto de cualquier tipo. También puede escribir el código en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] agregando la propiedad `language="VB"` a la `template` directiva .

- Para depurar la plantilla, agregue `debug="true"` a la `template` directiva . La plantilla se abrirá en otra instancia de Visual Studio si se produce una excepción. Si desea interrumpir el depurador en un punto específico del código, inserte la instrucción . `System.Diagnostics.Debugger.Break();`

   Para obtener más información, vea [Depuración de una plantilla de texto T4.](../modeling/debugging-a-t4-text-template.md)

## <a name="about-the-dsl-directive-processor"></a>Acerca del procesador de directivas DSL
 La plantilla puede usar las clases de dominio que definió en la definición de DSL. Esto se debe a una directiva que normalmente aparece cerca del inicio de la plantilla. En el ejemplo anterior, es el siguiente.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>
```

 El nombre de la directiva ( `MyLanguage` , en este ejemplo) se deriva del nombre del DSL. Invoca un procesador *de directivas* que se genera como parte del DSL. Puede encontrar su código fuente en **Dsl\GeneratedCode\DirectiveProcessor.cs**.

 El procesador de directivas DSL realiza dos tareas principales:

- Inserta eficazmente directivas de ensamblado e importación en la plantilla que hace referencia al DSL. Esto le permite usar las clases de dominio en el código de plantilla.

- Carga el archivo especificado en el parámetro y establece una propiedad en que hace referencia al elemento `requires` `this` raíz del modelo cargado.

## <a name="validating-the-model-before-running-the-template"></a>Validación del modelo antes de ejecutar la plantilla
 Puede hacer que el modelo se valide antes de que se ejecute la plantilla.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>
```

 Tenga en lo siguiente:

1. Los `filename` parámetros y se `validation` separan con ";" y no debe haber ningún otro separador ni espacio.

2. La lista de categorías de validación determina qué métodos de validación se ejecutarán. Se deben separar varias categorías con "&#124;" y no debe haber ningún otro separador ni espacio.

   Si se encuentra un error, se notifica en la ventana de errores y el archivo de resultados contendrá un mensaje de error.

## <a name="accessing-multiple-models-from-a-text-template"></a><a name="Multiple"></a> Acceso a varios modelos desde una plantilla de texto

> [!NOTE]
> Este método permite leer varios modelos en la misma plantilla, pero no admite referencias de ModelBus. Para leer los modelos que están intervinculados por referencias de ModelBus, vea [Using Visual Studio ModelBus in a Text Template](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 Si desea tener acceso a más de un modelo desde la misma plantilla de texto, debe llamar al procesador de directivas generado una vez para cada modelo. Debe especificar el nombre de archivo de cada modelo en el `requires` parámetro . Debe especificar los nombres que desea usar para la clase de dominio raíz en el `provides` parámetro . Debe especificar valores diferentes para los `provides` parámetros de cada una de las llamadas de directiva. Por ejemplo, suponga que tiene tres archivos de modelo denominados Library.xyz, School.xyz y Work.xyz. Para acceder a ellos desde la misma plantilla de texto, debe escribir tres llamadas de directiva similares a las siguientes.

```
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>
```

> [!NOTE]
> Este código de ejemplo es para un lenguaje que se basa en la plantilla de solución Lenguaje mínimo.

 Para acceder a los modelos de la plantilla de texto, ahora puede escribir código similar al código del ejemplo siguiente.

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

## <a name="loading-models-dynamically"></a>Carga dinámica de modelos
 Si desea determinar en tiempo de ejecución qué modelos cargar, puede cargar un archivo de modelo dinámicamente en el código del programa, en lugar de usar la directiva específica de DSL.

 Sin embargo, una de las funciones de la directiva específica de DSL es importar el espacio de nombres DSL, para que el código de plantilla pueda usar las clases de dominio definidas en ese DSL. Dado que no usa la directiva , debe agregar directivas **\<assembly>** y para todos los modelos que pueda **\<import>** cargar. Esto es fácil si los diferentes modelos que puede cargar son todas instancias del mismo DSL.

 Para cargar el archivo, el método más eficaz es mediante Visual Studio ModelBus. En un escenario típico, la plantilla de texto usará una directiva específica de DSL para cargar el primer modelo de la manera habitual. Ese modelo contendrá referencias de ModelBus a otro modelo. Puede usar ModelBus para abrir el modelo al que se hace referencia y acceder a un elemento determinado. Para obtener más información, vea [Using Visual Studio ModelBus in a Text Template](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 En un escenario menos habitual, es posible que quiera abrir un archivo de modelo para el que solo tenga un nombre de archivo y que podría no estar en el proyecto de Visual Studio actual. En este caso, puede abrir el archivo mediante la técnica descrita en [Cómo: Abrir un](../modeling/how-to-open-a-model-from-file-in-program-code.md)modelo desde un archivo en código de programa .

## <a name="generating-multiple-files-from-a-template"></a>Generación de varios archivos a partir de una plantilla
 Si desea generar varios archivos, por ejemplo, para generar un archivo independiente para cada elemento de un modelo, hay varios enfoques posibles. De forma predeterminada, solo se genera un archivo a partir de cada archivo de plantilla.

### <a name="splitting-a-long-file"></a>División de un archivo largo
 En este método, se usa una plantilla para generar un único archivo, separado por un delimitador. A continuación, divida el archivo en sus partes. Hay dos plantillas, una para generar el archivo único y la otra para dividirlo.

 **LoopTemplate.t4** genera el archivo único largo. Observe que su extensión de archivo es ".t4", ya que no se debe procesar directamente al hacer clic **en Transformar todas las plantillas.** Esta plantilla toma un parámetro , que especifica la cadena delimitadora que separa los segmentos:

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

 `LoopSplitter.tt` invoca `LoopTemplate.t4` y, a continuación, divide el archivo resultante en sus segmentos. Tenga en cuenta que esta plantilla no tiene que ser una plantilla de modelado, porque no lee el modelo.

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
