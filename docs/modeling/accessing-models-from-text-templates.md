---
title: Acceso a modelos a partir de plantillas de texto
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- text templates, accessing models
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a66f160d25ccacbdaaaf2238dfc738ade4a4200f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85531474"
---
# <a name="access-models-from-text-templates"></a>Acceder a los modelos desde plantillas de texto

Mediante el uso de plantillas de texto, puede crear archivos de informe, archivos de código fuente y otros archivos de texto basados en modelos de lenguajes específicos de dominio. Para obtener información básica sobre las plantillas de texto, vea [generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md). Las plantillas de texto funcionarán en el modo experimental cuando se depura el DSL y también funcionarán en un equipo en el que se haya implementado el DSL.

> [!NOTE]
> Cuando se crea una solución DSL, se generan archivos de plantilla de texto de ejemplo ** \* . TT** en el proyecto de depuración. Al cambiar los nombres de las clases de dominio, estas plantillas dejarán de funcionar. No obstante, incluyen las directivas básicas que necesita y proporcionan ejemplos que puede actualizar para que coincidan con el DSL.

 Para tener acceso a un modelo desde una plantilla de texto:

- Establezca la propiedad inherit de la Directiva de plantilla en [Microsoft. VisualStudio. TextTemplating. VSHost. ModelingTextTransformation](/previous-versions/bb893209(v=vs.140)). Esto proporciona acceso al almacén.

- Especifique los procesadores de directivas para el DSL al que desea obtener acceso. De este modo, se cargan los ensamblados del DSL para que pueda usar sus clases de dominio, propiedades y relaciones en el código de la plantilla de texto. También carga el archivo de modelo que especifique.

  Un `.tt` archivo similar al ejemplo siguiente se crea en el proyecto de depuración cuando se crea una nueva solución de Visual Studio a partir de la plantilla de lenguaje mínimo DSL.

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

 Tenga en cuenta los puntos siguientes sobre esta plantilla:

- La plantilla puede usar las clases de dominio, las propiedades y las relaciones definidas en la definición de DSL.

- La plantilla carga el archivo de modelo que se especifica en la `requires` propiedad.

- Una propiedad de `this` contiene el elemento raíz. Desde allí, el código puede navegar a otros elementos del modelo. El nombre de la propiedad suele ser el mismo que el de la clase de dominio raíz de DSL. En este ejemplo, es `this.ExampleModel`.

- Aunque el lenguaje en el que se escriben los fragmentos de código es C#, puede generar texto de cualquier tipo. Como alternativa, puede escribir el código en agregando [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] la propiedad `language="VB"` a la `template` Directiva.

- Para depurar la plantilla, agregue `debug="true"` a la `template` Directiva. La plantilla se abrirá en otra instancia de Visual Studio si se produce una excepción. Si desea interrumpir el depurador en un punto concreto del código, inserte la instrucción.`System.Diagnostics.Debugger.Break();`

   Para obtener más información, vea [depurar una plantilla de texto T4](../modeling/debugging-a-t4-text-template.md).

## <a name="about-the-dsl-directive-processor"></a>Acerca del procesador de directivas DSL
 La plantilla puede usar las clases de dominio que definió en la definición de DSL. Se trata de una directiva que suele aparecer cerca del inicio de la plantilla. En el ejemplo anterior, es lo siguiente.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>
```

 El nombre de la Directiva ( `MyLanguage` , en este ejemplo) se deriva del nombre del DSL. Invoca un procesador de *directivas* que se genera como parte del DSL. Puede encontrar su código fuente en **Dsl\GeneratedCode\DirectiveProcessor.CS**.

 El procesador de directivas de DSL realiza dos tareas principales:

- Inserta de forma eficaz las directivas de ensamblado e importación en la plantilla que hace referencia a su DSL. Esto le permite usar las clases de dominio en el código de plantilla.

- Carga el archivo especificado en el `requires` parámetro y establece una propiedad en `this` que hace referencia al elemento raíz del modelo cargado.

## <a name="validating-the-model-before-running-the-template"></a>Validar el modelo antes de ejecutar la plantilla
 Puede hacer que el modelo se valide antes de que se ejecute la plantilla.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>
```

 Tenga en lo siguiente:

1. Los `filename` `validation` parámetros y se separan con ";" y no debe haber otros separadores ni espacios.

2. La lista de categorías de validación determina qué métodos de validación se ejecutarán. Varias categorías se deben separar con "&#124;" y no debe haber otros separadores ni espacios.

   Si se encuentra un error, se le indicará en la ventana errores y el archivo de resultados contendrá un mensaje de error.

## <a name="accessing-multiple-models-from-a-text-template"></a><a name="Multiple"></a>Obtener acceso a varios modelos desde una plantilla de texto

> [!NOTE]
> Este método permite leer varios modelos en la misma plantilla, pero no admite referencias de ModelBus. Para leer modelos intervinculados por referencias de ModelBus, vea [usar Visual Studio ModelBus en una plantilla de texto](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 Si desea tener acceso a más de un modelo de la misma plantilla de texto, debe llamar al procesador de directivas generado una vez para cada modelo. Debe especificar el nombre de archivo de cada modelo en el `requires` parámetro. Debe especificar los nombres que desea usar para la clase de dominio raíz en el `provides` parámetro. Debe especificar valores diferentes para los `provides` parámetros en cada una de las llamadas de directiva. Por ejemplo, suponga que tiene tres archivos de modelo denominados Library. XYZ, School. XYZ y work. XYZ. Para tener acceso a ellas desde la misma plantilla de texto, debe escribir tres llamadas de directiva similares a las siguientes.

```
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>
```

> [!NOTE]
> Este código de ejemplo es para un idioma que se basa en la plantilla de la solución de idioma mínimo.

 Para tener acceso a los modelos de la plantilla de texto, ahora puede escribir código similar al código del siguiente ejemplo.

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

## <a name="loading-models-dynamically"></a>Cargar modelos dinámicamente
 Si desea determinar en tiempo de ejecución qué modelos se van a cargar, puede cargar dinámicamente un archivo de modelo en el código del programa, en lugar de usar la Directiva específica de DSL.

 Sin embargo, una de las funciones de la Directiva específica de DSL es importar el espacio de nombres DSL para que el código de plantilla pueda usar las clases de dominio definidas en ese DSL. Dado que no se usa la Directiva, debe agregar **\<assembly>** directivas y **\<import>** para todos los modelos que puede cargar. Esto es fácil si los diferentes modelos que puede cargar son todas las instancias del mismo DSL.

 Para cargar el archivo, el método más eficaz es mediante el uso de Visual Studio ModelBus. En un escenario típico, la plantilla de texto usará una directiva específica de DSL para cargar el primer modelo de la manera habitual. Ese modelo contiene referencias de ModelBus a otro modelo. Puede usar ModelBus para abrir el modelo al que se hace referencia y obtener acceso a un elemento determinado. Para obtener más información, vea [usar Visual Studio ModelBus en una plantilla de texto](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 En un escenario menos habitual, es posible que desee abrir un archivo de modelo para el que solo tenga un nombre de archivo y que no esté en el proyecto actual de Visual Studio. En este caso, puede abrir el archivo mediante la técnica descrita en [Cómo: abrir un modelo desde un archivo en el código del programa](../modeling/how-to-open-a-model-from-file-in-program-code.md).

## <a name="generating-multiple-files-from-a-template"></a>Generar varios archivos a partir de una plantilla
 Si desea generar varios archivos (por ejemplo, para generar un archivo independiente para cada elemento de un modelo), existen varios enfoques posibles. De forma predeterminada, solo se genera un archivo a partir de cada archivo de plantilla.

### <a name="splitting-a-long-file"></a>Dividir un archivo largo
 En este método, se usa una plantilla para generar un único archivo, separado por un delimitador. A continuación, divida el archivo en sus elementos. Hay dos plantillas, una para generar el único archivo y otra para dividirla.

 **LoopTemplate. T4** genera el archivo Long único. Tenga en cuenta que la extensión de archivo es ". T4", ya que no debe procesarse directamente al hacer clic en **transformar todas las plantillas**. Esta plantilla toma un parámetro, que especifica la cadena de delimitador que separa los segmentos:

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

 `LoopSplitter.tt`invoca `LoopTemplate.t4` y, a continuación, divide el archivo resultante en sus segmentos. Tenga en cuenta que esta plantilla no tiene que ser una plantilla de modelado, ya que no lee el modelo.

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
