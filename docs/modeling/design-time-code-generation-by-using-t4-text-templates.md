---
title: Generación de código en tiempo de diseño usando las plantillas de texto T4
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, guidelines for code generation
- text templates, data source model
- TextTemplatingFileGenerator custom tool
- Transform All Templates
- text templates, getting started
- Text Template project item
- text templates, generating code for your application
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 911c7dd0ff70029a3ca83ded9008472269dceaed
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49829474"
---
# <a name="design-time-code-generation-by-using-t4-text-templates"></a>Generación de código en tiempo de diseño usando las plantillas de texto T4
Plantillas de texto T4 de tiempo de diseño permiten generar código de programa y otros archivos en el proyecto de Visual Studio. Normalmente, las plantillas se escriben para que varíen el código que generan según los datos de un *modelo*. Un modelo es un archivo o una base de datos que contiene información esencial sobre los requisitos de la aplicación.

 Por ejemplo, podría tener un modelo que define un flujo de trabajo, como una tabla o un diagrama. A partir del modelo, puede generar el software que ejecuta el flujo de trabajo. Cuando cambian los requisitos del usuario, es fácil debatir el nuevo flujo de trabajo con los usuarios. Regenerar el código del flujo de trabajo es más confiable que actualizar el código a mano.

> [!NOTE]
>  Un *modelo* es un origen de datos que describe un aspecto determinado de una aplicación. Puede ser cualquier formulario, en cualquier tipo de archivo o base de datos. No tiene que estar en ningún formulario concreto, como un modelo UML o un modelo de lenguaje específico del dominio. Los modelos típicos están en el formulario de tablas o archivos XML.

 Probablemente ya está familiarizado con la generación de código. Al definir los recursos en un **.resx** se genera automáticamente el archivo en la solución de Visual Studio, un conjunto de clases y métodos. El archivo de recursos hace que resulte más fácil y confiable editar los recursos que editar las clases y los métodos. Con las plantillas de texto, puede generar código de la misma manera a partir de un origen con un diseño propio.

 Una plantilla de texto contiene una mezcla del texto que se desea generar y el código de programa que genera partes variables del texto. El código de programa y el texto permiten repetir u omitir condicionalmente partes del texto generado. El texto generado por sí mismo puede ser código de programa que formará parte de la aplicación.

## <a name="creating-a-design-time-t4-text-template"></a>Crear una plantilla de texto T4 en tiempo de diseño

#### <a name="to-create-a-design-time-t4-template-in-visual-studio"></a>Para crear una plantilla T4 en tiempo de diseño en Visual Studio

1. Crear un proyecto de Visual Studio, o abrir uno existente.

    Por ejemplo, en el **archivo** menú, elija **New** > **proyecto**.

2. Agregue un archivo de plantilla de texto al proyecto y asígnele un nombre que tenga la extensión **.tt**.

    Para ello, en **el Explorador de soluciones**, en el menú contextual del proyecto, elija **agregar** > **nuevo elemento**. En el **Agregar nuevo elemento** cuadro de diálogo seleccione **plantilla de texto** desde el panel central.

    Tenga en cuenta que el **Custom Tool** es propiedad del archivo **TextTemplatingFileGenerator**.

3. Abra el archivo. Ya contendrá las siguientes directivas:

   ```
   <#@ template hostspecific="false" language="C#" #>
   <#@ output extension=".txt" #>
   ```

    Si agregó la plantilla a un proyecto de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], el atributo de lenguaje será "`VB`".

4. Agregue el texto que desee al final del archivo. Por ejemplo:

   ```
   Hello, world!
   ```

5. Guarde el archivo.

    Es posible que vea un **advertencia de seguridad** cuadro de mensaje que le pide que confirme que desea ejecutar la plantilla. Haga clic en **Aceptar**.

6. En **el Explorador de soluciones**, expanda el nodo del archivo de plantilla y encontrará un archivo que tiene la extensión **.txt**. El archivo contiene el texto generado a partir de la plantilla.

   > [!NOTE]
   >  Si el proyecto es un proyecto de Visual Basic, debe hacer clic en **mostrar todos los archivos** con el fin de ver el archivo de salida.

### <a name="regenerating-the-code"></a>Volver a generar el código
 Se ejecutará una plantilla, que generará el archivo subsidiario, en cualquiera de los siguientes casos:

- Edite la plantilla y, a continuación, cambiar el foco a otra ventana de Visual Studio.

- Guarde la plantilla.

- Haga clic en **Transformar todas las plantillas** en el **compilar** menú. Este modo transformará todas las plantillas de la solución de Visual Studio.

- En **el Explorador de soluciones**, en el menú contextual de cualquier archivo, elija **ejecutar herramienta personalizada**. Utilice este método para transformar un subconjunto seleccionado de plantillas.

  También puede configurar un proyecto de Visual Studio para que las plantillas se ejecuten cuando han cambiado los archivos de datos que leen. Para obtener más información, consulte [automáticamente volver a generar el código](#Regenerating).

## <a name="generating-variable-text"></a>Generar texto variable
 Las plantillas de texto permiten utilizar código de programa para modificar el contenido del archivo generado.

#### <a name="to-generate-text-by-using-program-code"></a>Para generar texto utilizando código de programa

1. Cambie el contenido del archivo `.tt`:

   ```csharp
   <#@ template hostspecific="false" language="C#" #>
   <#@ output extension=".txt" #>
   <#int top = 10;

   for (int i = 0; i<=top; i++)
   { #>
      The square of <#= i #> is <#= i*i #>
   <# } #>
   ```

   ```vb
   <#@ template hostspecific="false" language="VB" #>
   <#@ output extension=".txt" #>
   <#Dim top As Integer = 10

   For i As Integer = 0 To top
   #>
       The square of <#= i #> is <#= i*i #>
   <#
   Next
   #>
   ```

2. Guarde el archivo .tt e inspeccione de nuevo el archivo .txt generado. Muestra los valores elevados al cuadrado de los números del 0 al 10.

   Observe que las instrucciones se colocan entre `<#...#>` y las expresiones simples entre `<#=...#>`. Para obtener más información, consulte [escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md).

   Si escribe el código de generación en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], la directiva `template` debería contener `language="VB"`. `"C#"` es el valor predeterminado.

## <a name="debugging-a-design-time-t4-text-template"></a>Depurar una plantilla de texto T4 en tiempo de diseño
 Para depurar una plantilla de texto:

- Inserte `debug="true"` en la directiva `template`. Por ejemplo:

   `<#@ template debug="true" hostspecific="false" language="C#" #>`

- Establezca puntos de interrupción en la plantilla, como si fuera código normal.

- Elija **depurar plantilla T4** en el menú contextual del archivo de plantilla de texto en el Explorador de soluciones.

  Se ejecutará la plantilla y se detendrá en los puntos de interrupción. Puede examinar las variables y recorrer el código de la forma habitual.

> [!TIP]
>  `debug="true"` hace que el código generado se asigne con más precisión a la plantilla de texto insertando más directivas de numeración de líneas en el código generado. Si las omite, los puntos de interrupción pueden detener la ejecución en un estado incorrecto.
>
>  Puede dejar la cláusula en la directiva de plantilla incluso aunque no esté realizando la depuración. Esto solo produce una pequeña caída del rendimiento.

## <a name="generating-code-or-resources-for-your-solution"></a>Generar código o recursos para la solución
 Puede generar archivos de programa que varían dependiendo de un modelo. Un modelo es una entrada como una base de datos, un archivo de configuración, un modelo UML, un modelo DSL u otro origen. Normalmente genera varios archivos de programa que proceden del mismo modelo. Para ello, crea un archivo de plantilla para cada archivo de programa generado y establece que todas las plantillas lean el mismo modelo.

#### <a name="to-generate-program-code-or-resources"></a>Para generar código de programa o recursos

1.  Cambie la directiva de salida para generar un archivo del tipo adecuado, como .cs, .vb, .resx o .xml.

2.  Inserte el código que generará el código de solución que requiere. Por ejemplo, si desea generar tres declaraciones de campo de número entero en una clase:

    ```csharp

              <#@ template debug="false" hostspecific="false" language="C#" #>
    <#@ output extension=".cs" #>
    <# var properties = new string [] {"P1", "P2", "P3"}; #>
    // This is generated code:
    class MyGeneratedClass {
    <# // This code runs in the text template:
      foreach (string propertyName in properties)  { #>
      // Generated code:
      private int <#= propertyName #> = 0;
    <# } #>
    }
    ```

    ```vb
    <#@ template debug="false" hostspecific="false" language="VB" #>
    <#@ output extension=".cs" #>
    <# Dim properties = {"P1", "P2", "P3"} #>
    class MyGeneratedClass {
    <#
       For Each propertyName As String In properties
    #>
      private int <#= propertyName #> = 0;
    <#
       Next
    #>
    }

    ```

3.  Guarde el archivo e inspeccione el archivo generado, que ahora contiene el siguiente código:

    ```csharp
    class MyGeneratedClass {
      private int P1 = 0;
      private int P2 = 0;
      private int P3 = 0;
    }
    ```

### <a name="generating-code-and-generated-text"></a>Generar código y texto generado
 Al generar el código de programa, es muy importante no confundir el código de generación que se ejecuta en la plantilla con el código generado resultante que pasa a formar parte de la solución. No es necesario que los dos lenguajes sean iguales.

 El ejemplo anterior tiene dos versiones. En una versión, el código de generación es en C#. En la otra versión, el código de generación es en Visual Basic. Sin embargo, el texto generado por ambos es el mismo, y es una clase de C#.

 Del mismo modo, podría utilizar una plantilla de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] para generar código en cualquier lenguaje. El texto generado no tiene que estar en un lenguaje determinado, y no tiene que ser código de programa.

### <a name="structuring-text-templates"></a>Estructura de plantillas de texto
 Como práctica recomendable, se tiende a separar el código de plantilla en dos partes:

- Una configuración o parte de la recolección de datos, que establece valores en variables, pero no contiene bloques de texto. En el ejemplo anterior, esta parte es la inicialización de `properties`.

   Esto, a veces se denomina la sección "modelo", porque genera un modelo en almacén y lee normalmente un archivo del modelo.

- La parte de la generación de texto (`foreach(...){...}` en el ejemplo), que utiliza valores de las variables.

  Esta separación no es necesaria, pero es un estilo que facilita la lectura de la plantilla reduciendo la complejidad de la parte que incluye el texto.

## <a name="reading-files-or-other-sources"></a>Leer archivos u otros orígenes
 Para obtener acceso a un archivo modelo o base de datos, el código de plantilla puede utilizar ensamblados como System.XML. Para obtener acceso a estos ensamblados, debe insertar directivas como las siguientes:

```
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.IO" #>
```

 El `assembly` directiva hace que el ensamblado especificado esté disponible para el código de plantilla, en la misma manera que la sección de referencias de un proyecto de Visual Studio. No necesita incluir una referencia a System.dll, al que se hace referencia automáticamente. La directiva `import` permite utilizar tipos sin usar sus nombres completos, de la misma manera que la directiva `using` en un archivo de programa normal.

 Por ejemplo, después de importar **System.IO**, podría escribir:

```csharp

      <# var properties = File.ReadLines("C:\\propertyList.txt");#>
...
<# foreach (string propertyName in properties) { #>
...
```

```vb
<# For Each propertyName As String In
             File.ReadLines("C:\\propertyList.txt")
#>
```

### <a name="opening-a-file-with-a-relative-pathname"></a>Abrir un archivo con un nombre de ruta de acceso relativa
 Para cargar un archivo de una ubicación relativa a la plantilla de texto, puede utilizar `this.Host.ResolvePath()`. Para utilizar this.Host, debe establecer `hostspecific="true"` en la `template`:

```
<#@ template debug="false" hostspecific="true" language="C#" #>
```

 A continuación, puede escribir, por ejemplo:

```csharp
<# string fileName = this.Host.ResolvePath("filename.txt");
  string [] properties = File.ReadLines(filename);
#>
...
<#  foreach (string propertyName in properties { #>
...
```

```vb
<# Dim fileName = Me.Host.ResolvePath("propertyList.txt")
   Dim properties = File.ReadLines(filename)
#>
...
<#   For Each propertyName As String In properties
...
#>
```

 También puede utilizar `this.Host.TemplateFile`, que identifica el nombre del archivo de plantilla actual.

 El tipo de `this.Host` (en VB, `Me.Host`) es `Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost`.

### <a name="getting-data-from-visual-studio"></a>Obtención de datos de Visual Studio
 Para utilizar servicios proporcionados en Visual Studio, establezca el `hostSpecific` atributo y carga el `EnvDTE` ensamblado. Puede utilizar entonces IServiceProvider.GetCOMService() para tener acceso al DTE y otros servicios. Por ejemplo:

```scr
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetCOMService(typeof(EnvDTE.DTE));
#>

Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>
```

> [!TIP]
>  Una plantilla de texto se ejecuta en su propio dominio de aplicación y el acceso a los servicios se realiza mediante el cálculo de referencias. En este caso, GetCOMService() es más confiable que GetService().

## <a name="Regenerating"></a> Volver a generar el código automáticamente
 Normalmente, se generan varios archivos en una solución de Visual Studio con un modelo de entrada. Cada archivo se genera a partir de su propia plantilla, pero todas las plantillas hacen referencia al mismo modelo.

 Si el modelo de origen cambia, debe volver a ejecutar todas las plantillas de la solución. Para hacerlo manualmente, elija **Transformar todas las plantillas** en el **compilar** menú.

 Si ha instalado el SDK de modelado de Visual Studio, puede tener todas las plantillas se transformen automáticamente cada vez que realice una compilación. Para ello, edite el archivo de proyecto (.csproj o .vbproj) en un editor de texto y agregue las siguientes líneas cerca del final del archivo, después de cualquier otra instrucción `<import>`:

> [!NOTE]
> En Visual Studio 2017, el SDK de transformación de plantilla de texto y el SDK de modelado de Visual Studio se instalan automáticamente al instalar características específicas de Visual Studio. Para obtener más información, consulte [esta entrada de blog](https://blogs.msdn.microsoft.com/visualstudioalm/2016/12/12/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets" />
<PropertyGroup>
   <TransformOnBuild>true</TransformOnBuild>
   <!-- Other properties can be inserted here -->
</PropertyGroup>
```

 Para obtener más información, consulte [generación de código en un proceso de compilación](../modeling/code-generation-in-a-build-process.md).

## <a name="error-reporting"></a>Notificación de errores
 Para colocar mensajes de error y advertencia en la ventana de errores de Visual Studio, puede utilizar estos métodos:

```
Error("An error message");
Warning("A warning message");
```

## <a name="Converting"></a> Convertir un archivo existente en una plantilla
 Una característica útil de las plantillas es que se parecen mucho a los archivos que generan y cuentan con algún código de programa insertado. Esto sugiere un método útil para crear una plantilla. En primer lugar cree un archivo normal como prototipo, como un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] de archivo y, a continuación, agregue gradualmente código de generación que modifique el archivo resultante.

#### <a name="to-convert-an-existing-file-to-a-design-time-template"></a>Para convertir un archivo existente en una plantilla en tiempo de diseño

1. A su proyecto de Visual Studio, agregue un archivo del tipo que desea generar, como un `.cs`, `.vb`, o `.resx` archivo.

2. Pruebe el nuevo archivo para asegurarse de que funciona.

3. En el Explorador de soluciones, cambie la extensión de nombre de archivo a **.tt**.

4. Compruebe las siguientes propiedades de la **.tt** archivo:


   | | |
   |-|-|
   | **Herramienta personalizada =** | **TextTemplatingFileGenerator** |
   | **Acción de compilación =** | **Ninguno** |


5. Inserte las siguientes líneas al principio del archivo:

   ```
   <#@ template debug="false" hostspecific="false" language="C#" #>
   <#@ output extension=".cs" #>
   ```

    Si desea escribir el código de generación de la plantilla en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], establezca el atributo `language` en `"VB"` en lugar de `"C#"`.

    Establezca el atributo `extension` en la extensión de nombre de archivo para el tipo de archivo que desea generar, por ejemplo `.cs`, `.resx` o `.xml`.

6. Guarde el archivo.

    Se crea un archivo subsidiario, con la extensión especificada. Sus propiedades son correctas para el tipo de archivo. Por ejemplo, el **acción de compilación** propiedad de un archivo .cs sería **compilar**.

    Compruebe que el archivo generado incluye el mismo contenido que el archivo original.

7. Identifique una parte del archivo que desea modificar. Por ejemplo, una parte que aparece solamente bajo ciertas condiciones o una parte que se repite o donde los valores concretos varían. Inserte el código de generación. Guarde el archivo y compruebe que el archivo subsidiario se genera correctamente. Repita este paso.

## <a name="guidelines-for-code-generation"></a>Directrices para la generación de código
 Consulte [directrices para escribir plantillas de texto T4](../modeling/guidelines-for-writing-t4-text-templates.md).

## <a name="next-steps"></a>Pasos siguientes

|Paso siguiente|Tema|
|-|-|
|Escriba y depure una plantilla de texto más avanzada, con código que utilice funciones auxiliares, archivos incluidos y datos externos.|[Escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md)|
|Genere documentos a partir de plantillas en tiempo de ejecución.|[Generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md)|
|Ejecute la generación de texto fuera de Visual Studio.|[Generar archivos con la utilidad TextTransform](../modeling/generating-files-with-the-texttransform-utility.md)|
|Transforme los datos al formato de un lenguaje específico de dominio.|[Generar código a partir de lenguajes específicos de dominio](../modeling/generating-code-from-a-domain-specific-language.md)|
|Escriba procesadores de directivas para transformar sus propios orígenes de datos.|[Personalizar la transformación de texto T4](../modeling/customizing-t4-text-transformation.md)|

## <a name="see-also"></a>Vea también

- [Instrucciones para escribir plantillas de texto T4](../modeling/guidelines-for-writing-t4-text-templates.md)
