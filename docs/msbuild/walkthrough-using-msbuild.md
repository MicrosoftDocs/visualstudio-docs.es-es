---
title: 'Tutorial: Usar MSBuild | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: b8a8b866-bb07-4abf-b9ec-0b40d281c310
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 94fdbb5f143d1c087d97490961d230ace239f348
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2018
ms.locfileid: "48880154"
---
# <a name="walkthrough-use-msbuild"></a>Tutorial: Usar MSBuild
MSBuild es la plataforma de compilación para Microsoft y Visual Studio. Este tutorial presenta los bloques de compilación de MSBuild y muestra la forma de escribir, manipular y depurar los proyectos de MSBuild. Aprenderá a:

-   Crear y manipular un archivo del proyecto

-   Cómo usar las propiedades de compilación

-   Cómo usar los elementos de compilación

Puede ejecutar MSBuild desde Visual Studio o en la **ventana de comandos**. En este tutorial, creará un archivo del proyecto de MSBuild con Visual Studio. Editará el archivo del proyecto en Visual Studio y utilizará una **ventana de comandos** para compilar el proyecto y examinar los resultados.

## <a name="create-an-msbuild-project"></a>Creación de un proyecto de MSBuild
 El sistema de proyectos de Visual Studio se basa en MSBuild. Esto facilita la creación de un nuevo archivo del proyecto con Visual Studio. En esta sección, creará un archivo del proyecto de Visual C#. En su lugar, puede crear un archivo del proyecto de Visual Basic. En el contexto de este tutorial, la diferencia entre los dos archivos del proyecto es secundaria.

#### <a name="to-create-a-project-file"></a>Para crear un archivo del proyecto

1.  Abra Visual Studio.

2.  En el menú **Archivo** , elija **Nuevo**y haga clic en **Proyecto**.

3.  En el cuadro de diálogo **Nuevo proyecto**, seleccione el tipo de proyecto de **Visual C#** y, a continuación, seleccione la plantilla **Aplicación de Windows Forms**. En el cuadro **Nombre** , escriba `BuildApp`. Escriba una **ubicación** para la solución, por ejemplo, *D:\\*. Acepte los valores predeterminados de **Create directory for solution** (Crear directorio para la solución) (seleccionado), **Agregar al control de código fuente** (no seleccionado) y **Nombre de la solución** (**BuildApp**).

4.    Haga clic en **Aceptar** para crear el archivo del proyecto.

## <a name="examine-the-project-file"></a>Examen del archivo de proyecto
 En la sección anterior, utilizó Visual Studio para crear un archivo del proyecto de Visual C#. El archivo del proyecto se representa en el **Explorador de soluciones** por el nodo de proyecto denominado BuildApp. Puede utilizar el editor de código de Visual Studio para examinar el archivo del proyecto.

#### <a name="to-examine-the-project-file"></a>Para examinar el archivo del proyecto

1.  En el **Explorador de soluciones**, haga clic en el nodo de proyecto **BuildApp**.

2.  En el navegador de **Propiedades**, observe que la propiedad **Project File** es *BuildApp.csproj*. Todos los nombres de los archivos de proyecto llevan el sufijo *proj*. Si hubiera creado un proyecto de Visual Basic, el nombre del archivo del proyecto sería *BuildApp.vbproj*.

3.  Haga clic con el botón secundario en el nodo del proyecto y, después, haga clic en **Descargar el proyecto**.

4.  Haga clic con el botón secundario de nuevo en el nodo del proyecto y, a continuación, haga clic en **Editar BuildApp.csproj**.

     El archivo del proyecto aparece en el editor de código.

## <a name="targets-and-tasks"></a>Destinos y tareas
Los archivos del proyecto son archivos con formato XML y con el nodo raíz [Project](../msbuild/project-element-msbuild.md).

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0"  xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Debe especificar el espacio de nombres xmlns en el elemento Project. Si `ToolsVersion` está presente en un nuevo proyecto, debe ser "15.0".

El trabajo de compilar una aplicación se realiza con los elementos [Target](../msbuild/target-element-msbuild.md) y [Task](../msbuild/task-element-msbuild.md).

-   Una tarea es la unidad de trabajo más pequeña, en otras palabras, el "átomo" de una compilación. Las tareas son componentes ejecutables independientes que pueden tener entradas y salidas. No hay actualmente ninguna tarea a la que se haga referencia o que esté definida en el archivo del proyecto. Agregará tareas al archivo del proyecto en las secciones siguientes. Para obtener más información, consulte el tema [Tareas](../msbuild/msbuild-tasks.md).

-   Un destino es una secuencia con nombre de tareas. Para obtener más información, consulte el tema [Destinos](../msbuild/msbuild-targets.md).

El destino predeterminado no se define en el archivo del proyecto, sino que se especifica en los proyectos importados. El elemento [Import](../msbuild/import-element-msbuild.md) indica los proyectos importados. Por ejemplo, en un proyecto de C#, el destino predeterminado se importa del archivo *Microsoft.CSharp.targets*.

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

Los archivos importados se insertan realmente en el archivo del proyecto, dondequiera que se les haga referencia.

> [!NOTE]
> En algunos tipos de proyecto, como .NET Core, se usa un esquema simplificado con un atributo `Sdk` en lugar de `ToolsVersion`. Estos proyectos tienen importaciones implícitas y valores de atributo predeterminados diferentes.

MSBuild realiza el seguimiento de los destinos de una compilación y garantiza que cada destino se compile solamente una vez.

## <a name="add-a-target-and-a-task"></a>Agregar un destino y una tarea
 Agregue un destino al archivo del proyecto. Agregue una tarea al destino que imprima un mensaje.

#### <a name="to-add-a-target-and-a-task"></a>Para agregar un destino y una tarea

1.  Agregue estas líneas al archivo del proyecto, justo después de la instrucción Import:

    ```xml
    <Target Name="HelloWorld">
    </Target>
    ```

     Esto crea un destino denominado HelloWorld. Observe que tiene compatibilidad con IntelliSense mientras edita el archivo del proyecto.

2.  Agregue líneas al destino HelloWorld para que la sección resultante sea similar a esta:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Hello"></Message>  <Message Text="World"></Message>
    </Target>
    ```

3.  Guarde el archivo de proyecto.

La tarea Message es una de las muchas tareas que se distribuyen con MSBuild. Para obtener una lista completa de tareas disponibles e información de uso, consulte [Referencia de tareas](../msbuild/msbuild-task-reference.md).

La tarea Message toma el valor de cadena del atributo Text como entrada y lo muestra en el dispositivo de salida. El destino HelloWorld ejecuta la tarea Message dos veces: primero para mostrar "Hello" y luego para mostrar "World".

## <a name="build-the-target"></a>Compilación del destino
 Ejecute MSBuild desde el **símbolo del sistema de Visual Studio** para compilar el destino HelloWorld definido anteriormente. Utilice el modificador de línea de comandos -target o -t para seleccionar el destino.

> [!NOTE]
>  Haremos referencia al **símbolo del sistema de Visual Studio** como la **ventana Comandos** en las secciones siguientes.

#### <a name="to-build-the-target"></a>Para compilar el destino

1.  Haga clic en **Inicio** y, a continuación, en **Todos los programas**. Busque y haga clic en el **símbolo del sistema de Visual Studio** en la carpeta **Visual Studio Tools**.

2.  En la ventana de comandos, navegue hasta la carpeta que contiene el archivo de proyecto, en este caso, *D:\BuildApp\BuildApp*.

3.  Ejecute msbuild con el modificador de comando -t:HelloWorld. Esto selecciona y compila el destino HelloWorld:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4.  Examine la salida en la **ventana Comandos**. Debe ver las dos líneas "Hello" y "World":

    ```
    Hello
    World
    ```

> [!NOTE]
>  Si en su lugar ve `The target "HelloWorld" does not exist in the project`, es probable que se haya olvidado de guardar el archivo del proyecto en el editor de código. Guarde el archivo y vuelva a intentarlo.

 Alternando entre el editor de código y la ventana Comandos, puede cambiar el archivo del proyecto y ver rápidamente los resultados.

## <a name="build-properties"></a>Propiedades de compilación
 Las propiedades de compilación son pares de nombre y valor que guían la compilación. Ya se han definido varias propiedades de compilación al principio del archivo del proyecto:

```xml
<PropertyGroup>
...
  <ProductVersion>10.0.11107</ProductVersion>
  <SchemaVersion>2.0</SchemaVersion>
  <ProjectGuid>{30E3C9D5-FD86-4691-A331-80EA5BA7E571}</ProjectGuid>
  <OutputType>WinExe</OutputType>
...
</PropertyGroup>
```

 Todas las propiedades son elementos secundarios de elementos PropertyGroup. El nombre de la propiedad es el nombre del elemento secundario y el valor de la propiedad es el elemento de texto del elemento secundario. Por ejemplo,

```xml
<TargetFrameworkVersion>v15.0</TargetFrameworkVersion>
```

 define la propiedad denominada TargetFrameworkVersion, dándole el valor de cadena "v15.0".

 Las propiedades de compilación se pueden volver a definir en cualquier momento. Si

```xml
<TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
```

 aparece más adelante en el archivo del proyecto, o en un archivo importado posteriormente en el archivo del proyecto, TargetFrameworkVersion toma el nuevo valor "v3.5".

## <a name="examine-a-property-value"></a>Examen del valor de una propiedad
 Para obtener el valor de una propiedad, utilice la sintaxis siguiente, donde PropertyName es el nombre de la propiedad:

```xml
$(PropertyName)
```

 Utilice esta sintaxis para examinar algunas de las propiedades en el archivo del proyecto.

#### <a name="to-examine-a-property-value"></a>Para examinar el valor de una propiedad

1.  En el editor de código, reemplace el destino HelloWorld por este código:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Configuration is $(Configuration)" />
      <Message Text="MSBuildToolsPath is $(MSBuildToolsPath)" />
    </Target>
    ```

2.  Guarde el archivo de proyecto.

3.  Desde la **ventana Comandos**, escriba y ejecute la siguiente línea:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4.  Examine los resultados. Debe ver estas dos líneas (es posible que su versión de .NET Framework difiera):

    ```
    Configuration is Debug
    MSBuildToolsPath is C:\Program Files (x86)\Microsoft Visual Studio\2017\<Visual Studio SKU>\MSBuild\15.0\Bin
    ```

> [!NOTE]
>  Si no ve estas líneas, es probable que se haya olvidado de guardar el archivo del proyecto en el editor de código. Guarde el archivo y vuelva a intentarlo.

### <a name="conditional-properties"></a>Propiedades condicionales
 Muchas propiedades, como Configuration, se definen condicionalmente, es decir, el atributo Condition aparece en el elemento de propiedad. Las propiedades condicionales se definen o vuelven a definir solo si la condición se evalúa como "true". Observe que a las propiedades no definidas se les proporciona el valor predeterminado de una cadena vacía. Por ejemplo,

```xml
<Configuration   Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

 significa "Si la propiedad Configuration no se ha definido todavía, defínala y dele el valor 'Debug'".

 Casi todos elementos de MSBuild pueden tener un atributo Condition. Para obtener más información sobre cómo utilizar el atributo Condition, consulte [Condiciones](../msbuild/msbuild-conditions.md).

### <a name="reserved-properties"></a>Propiedades reservadas
 MSBuild reserva algunos nombres de propiedades para almacenar información sobre el archivo del proyecto y los archivos binarios de MSBuild. MSBuildToolsPath es un ejemplo de una propiedad reservada. Como a cualquier otra propiedad, a las propiedades reservadas se hace referencia con la notación $. Para más información, consulte [Cómo: Hacer referencia al nombre o la ubicación del archivo del proyecto](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) y [Propiedades reservadas y conocidas de MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).

### <a name="environment-variables"></a>Variables de entorno
 En los archivos del proyecto, se puede hacer referencia a las variables de entorno como si fueran propiedades de compilación. Por ejemplo, para utilizar la variable de entorno PATH en el archivo de proyecto, utilice $(Path). Si el proyecto incluye la definición de una propiedad que tiene el mismo nombre que una variable de entorno, la propiedad del proyecto reemplaza el valor de la variable de entorno. Para más información, consulte [Cómo: Utilizar variables de entorno en una compilación](../msbuild/how-to-use-environment-variables-in-a-build.md).

## <a name="set-properties-from-the-command-line"></a>Establecimiento de propiedades desde la línea de comandos
 Las propiedades se pueden definir en la línea de comandos utilizando el modificador de línea de comandos -property o -p. Los valores de propiedad recibidos desde la línea de comandos invalidan los valores de propiedad establecidos en el archivo del proyecto y las variables de entorno.

#### <a name="to-set-a-property-value-from-the-command-line"></a>Para establecer el valor de una propiedad desde la línea de comandos

1.  Desde la **ventana Comandos**, escriba y ejecute la siguiente línea:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld -p:Configuration=Release
    ```

2.  Examine los resultados. Debe ver esta línea:

    ```
    Configuration is Release.
    ```

MSBuild crea la propiedad Configuration y le asigna el valor "Release".

## <a name="special-characters"></a>Caracteres especiales
 Ciertos caracteres tienen un significado especial en archivos del proyecto de MSBuild. Ejemplos de estos caracteres son los signos de punto y coma (;) y los asteriscos (*). Para utilizar estos caracteres especiales con su significado literal en un archivo de proyecto, es preciso especificarlos con la sintaxis %\<xx>, donde \<xx> representa el valor hexadecimal ASCII del carácter.

 Cambie la tarea Message para mostrar el valor de la propiedad Configuration con caracteres especiales para que se pueda leer mejor.

#### <a name="to-use-special-characters-in-the-message-task"></a>Para utilizar caracteres especiales en la tarea Message

1.  En el editor de código, reemplace ambas tareas Message por esta línea:

    ```xml
    <Message Text="%24(Configuration) is %22$(Configuration)%22" />
    ```

2.  Guarde el archivo de proyecto.

3.  Desde la **ventana Comandos**, escriba y ejecute la siguiente línea:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4.  Examine los resultados. Debe ver esta línea:

    ```
    $(Configuration) is "Debug"
    ```

Para más información, consulte [Caracteres especiales de MSBuild](../msbuild/msbuild-special-characters.md).

## <a name="build-items"></a>Elementos de compilación
 Un elemento es un fragmento de información, normalmente un nombre de archivo, que se utiliza como entrada al sistema de compilación. Por ejemplo, una colección de elementos que representan archivos de código fuente pueden pasarse a una tarea denominada Compile para compilarlos en un ensamblado.

 Todos los elementos son elementos secundarios de elementos ItemGroup. El nombre de elemento es el nombre del elemento secundario y el valor de elemento es el valor del atributo Include del elemento secundario. Los valores de elementos con el mismo nombre se agrupan en tipos de elemento de ese nombre.  Por ejemplo,

```xml
<ItemGroup>
    <Compile Include="Program.cs" />
    <Compile Include="Properties\AssemblyInfo.cs" />
</ItemGroup>
```

 define un grupo de elementos que contiene dos elementos. El tipo de elemento Compile tiene dos valores: *Program.cs* y *Properties\AssemblyInfo.cs*.

 El código siguiente crea el mismo tipo de elemento declarando ambos archivos en un atributo Include, separados por punto y coma.

```xml
<ItemGroup>
    <Compile Include="Program.cs;Properties\AssemblyInfo.cs" />
</ItemGroup>
```

Para obtener más información, consulte [Elementos](../msbuild/msbuild-items.md).

> [!NOTE]
>  Las rutas de acceso de archivo son relativas a la carpeta que contiene el archivo del proyecto de MSBuild.

## <a name="examine-item-type-values"></a>Examen de los valores de tipo de elemento
 Para obtener los valores de un tipo de elemento, utilice la sintaxis siguiente, donde ItemType es el nombre del tipo de elemento:

```xml
@(ItemType)
```

 Utilice esta sintaxis para examinar el tipo de elemento Compile en el archivo del proyecto.

#### <a name="to-examine-item-type-values"></a>Para examinar los valores de tipo de elemento

1.  En el editor de código, reemplace la tarea de destino HelloWorld por este código:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Compile item type contains @(Compile)" />
    </Target>
    ```

2.  Guarde el archivo de proyecto.

3.  Desde la **ventana Comandos**, escriba y ejecute la siguiente línea:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4.  Examine los resultados. Debe ver esta línea larga:

    ```
    Compile item type contains Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
    ```

Los valores de un tipo de elemento se separan de forma predeterminada con puntos y coma.

Para cambiar el separador de un tipo de elemento, utilice la sintaxis siguiente, donde ItemType es el tipo de elemento y Separator es una cadena de uno o más caracteres de separación:

```xml
@(ItemType, Separator)
```

Cambie la tarea Message para utilizar retornos de carro y saltos de línea (% 0A%0D) con el fin de mostrar los elementos Compile uno por línea.

#### <a name="to-display-item-type-values-one-per-line"></a>Para mostrar los valores de tipo de elemento uno por línea

1.  En el editor de código, reemplace la tarea Message por esta línea:

    ```xml
    <Message Text="Compile item type contains @(Compile, '%0A%0D')" />
    ```

2.  Guarde el archivo de proyecto.

3.  Desde la **ventana Comandos**, escriba y ejecute la siguiente línea:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4.  Examine los resultados. Debe ver las siguientes líneas:

    ```
    Compile item type contains Form1.cs
    Form1.Designer.cs
    Program.cs
    Properties\AssemblyInfo.cs
    Properties\Resources.Designer.cs
    Properties\Settings.Designer.cs
    ```

### <a name="include-exclude-and-wildcards"></a>Include, Exclude y caracteres comodín
 Puede utilizar los caracteres comodín "*", "\*\*" y "?" con el atributo Include para agregar elementos a un tipo de elemento. Por ejemplo,

```xml
<Photos Include="images\*.jpeg" />
```

 agrega todos los archivos con la extensión *.jpeg* de la carpeta *images* al tipo de elemento Photos, mientras que

```xml
<Photos Include="images\**.jpeg" />
```

 agrega todos los archivos con la extensión *.jpeg* de la carpeta *images*, y todas sus subcarpetas, al tipo de elemento Photos. Para obtener más ejemplos, consulte [Cómo: Seleccionar los archivos que se van a compilar](../msbuild/how-to-select-the-files-to-build.md).

 Observe que según se declaran elementos se agregan al tipo de elemento. Por ejemplo,

```xml
<Photos Include="images\*.jpeg" />
<Photos Include="images\*.gif" />
```

 crea un tipo de elemento denominado Photo que contiene todos los archivos de la carpeta *images* con una extensión *.jpeg* o *.gif*. Esto es equivalente a la línea siguiente:

```xml
<Photos Include="images\*.jpeg;images\*.gif" />
```

 Puede excluir un elemento de un tipo de elemento con el atributo Exclude. Por ejemplo,

```xml
<Compile Include="*.cs" Exclude="*Designer*">
```

 agrega todos los archivos con la extensión *.cs* al tipo de elemento Compile, salvo los archivos cuyos nombres contienen la cadena *Designer*. Para obtener más ejemplos, consulte [Cómo: Excluir archivos de la compilación](../msbuild/how-to-exclude-files-from-the-build.md).

El atributo Exclude solamente afecta a los elementos agregados por el atributo Include en el elemento que contiene ambos. Por ejemplo,

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

no excluiría el archivo *Form1.cs*, que se agregó en el elemento anterior.

##### <a name="to-include-and-exclude-items"></a>Para incluir y excluir elementos

1.  En el editor de código, reemplace la tarea Message por esta línea:

    ```xml
    <Message Text="XFiles item type contains @(XFiles)" />
    ```

2.  Agregue este grupo de elementos justo después del elemento Import:

    ```xml
    <ItemGroup>
       <XFiles Include="*.cs;properties/*.resx" Exclude="*Designer*" />
    </ItemGroup>
    ```

3.  Guarde el archivo de proyecto.

4.  Desde la **ventana Comandos**, escriba y ejecute la siguiente línea:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

5.  Examine los resultados. Debe ver esta línea:

    ```
    XFiles item type contains Form1.cs;Program.cs;Properties/Resources.resx
    ```

## <a name="item-metadata"></a>Metadatos de elementos
 Los elementos pueden contener metadatos además de la información recopilada de los atributos Include y Exclude. Estos metadatos los pueden utilizar las tareas que requieren más información sobre elementos que solo el valor de elemento.

 Los metadatos de elementos se declaran en el archivo de proyecto creando un elemento con el nombre de los metadatos como elemento secundario del elemento. Un elemento puede tener cero o varios valores de metadatos. Por ejemplo, el elemento CSFile siguiente tiene los metadatos Culture con un valor de "Fr":

```xml
<ItemGroup>
    <CSFile Include="main.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 Para obtener el valor de metadatos de un tipo de elemento, utilice la sintaxis siguiente, donde ItemType es el nombre del tipo de elemento y MetaDataName es el nombre de los metadatos:

```xml
%(ItemType.MetaDataName)
```

#### <a name="to-examine-item-metadata"></a>Para examinar los metadatos de elementos

1.  En el editor de código, reemplace la tarea Message por esta línea:

    ```xml
    <Message Text="Compile.DependentUpon: %(Compile.DependentUpon)" />
    ```

2.  Guarde el archivo de proyecto.

3.  Desde la **ventana Comandos**, escriba y ejecute la siguiente línea:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4.  Examine los resultados. Debe ver las siguientes líneas:

    ```
    Compile.DependentUpon:
    Compile.DependentUpon: Form1.cs
    Compile.DependentUpon: Resources.resx
    Compile.DependentUpon: Settings.settings
    ```

Observe cómo la frase "Compile.DependentUpon" aparece varias veces. El uso de metadatos con esta sintaxis dentro de un destino produce el "procesamiento por lotes". El procesamiento por lotes significa que las tareas dentro del destino se ejecutan una vez para cada valor de metadatos único. Este es el script de MSBuild equivalente de la construcción de programación "bucle for" común. Para obtener más información, consulte [Procesamiento por lotes](../msbuild/msbuild-batching.md).

### <a name="well-known-metadata"></a>Metadatos conocidos
 Cada vez que se agrega un elemento a una lista de elementos, se le asignan metadatos conocidos. Por ejemplo, %(Filename) devuelve el nombre de archivo de cualquier elemento. Para obtener una lista completa de metadatos conocidos, consulte [Metadatos de elementos conocidos](../msbuild/msbuild-well-known-item-metadata.md).

##### <a name="to-examine-well-known-metadata"></a>Para examinar los metadatos conocidos

1.  En el editor de código, reemplace la tarea Message por esta línea:

    ```xml
    <Message Text="Compile Filename: %(Compile.Filename)" />
    ```

2.  Guarde el archivo de proyecto.

3.  Desde la **ventana Comandos**, escriba y ejecute la siguiente línea:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4.  Examine los resultados. Debe ver las siguientes líneas:

    ```
    Compile Filename: Form1
    Compile Filename: Form1.Designer
    Compile Filename: Program
    Compile Filename: AssemblyInfo
    Compile Filename: Resources.Designer
    Compile Filename: Settings.Designer
    ```

Comparando los dos ejemplos anteriores, puede ver que mientras que no todos los elementos del tipo de elemento Compile tiene metadatos DependentUpon, todos los elementos tienen metadatos Filename conocidos.

### <a name="metadata-transformations"></a>Transformaciones de metadatos
 Las listas de elementos se pueden transformar en nuevas listas de elementos. Para transformar una lista de elementos, utilice la sintaxis siguiente, donde \<ItemType> es el nombre del tipo de elemento y \<MetadataName> es el nombre de los metadatos:

```xml
@(ItemType -> '%(MetadataName)')
```

Por ejemplo, una lista de elementos de archivos de origen se puede transformar en una colección de archivos de objeto mediante una expresión como `@(SourceFiles -> '%(Filename).obj')`. Para obtener más información, consulte [Transformaciones](../msbuild/msbuild-transforms.md).

##### <a name="to-transform-items-using-metadata"></a>Para transformar elementos mediante metadatos

1.  En el editor de código, reemplace la tarea Message por esta línea:

    ```xml
    <Message Text="Backup files: @(Compile->'%(filename).bak')" />
    ```

2.  Guarde el archivo de proyecto.

3.  Desde la **ventana Comandos**, escriba y ejecute la siguiente línea:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4.  Examine los resultados. Debe ver esta línea:

    ```
    Backup files: Form1.bak;Form1.Designer.bak;Program.bak;AssemblyInfo.bak;Resources.Designer.bak;Settings.Designer.bak
    ```

Observe que los metadatos expresados en esta sintaxis no producen el procesamiento por lotes.

## <a name="whats-next"></a>Pasos adicionales
 Para información sobre cómo crear un archivo del proyecto paso a paso, consulte [Tutorial: Crear un archivo del proyecto de MSBuild desde el principio](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).

## <a name="see-also"></a>Vea también

- [Información general sobre MSBuild](../msbuild/msbuild.md)
- [Referencia de MSBuild](../msbuild/msbuild-reference.md)
