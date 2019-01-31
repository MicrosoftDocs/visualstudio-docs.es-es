---
title: 'Tutorial: Crear un archivo de proyecto de MSBuild desde cero | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: e3acff7c-cb4e-4ae1-8be2-a871bcff847b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9cbfa407a35934461fe8f2a9fdc9b4ba1fde8b68
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54997486"
---
# <a name="walkthrough-create-an-msbuild-project-file-from-scratch"></a>Tutorial: Crear un archivo de proyecto de MSBuild desde cero
Los lenguajes de programación destinados a .NET Framework usan archivos de proyecto de MSBuild para describir y controlar el proceso de compilación de aplicaciones. Cuando se usa Visual Studio para crear un archivo del proyecto de MSBuild, el XML adecuado se agrega al archivo automáticamente. Sin embargo, puede ser de utilidad comprender cómo se organiza el XML y cómo se puede cambiar para controlar una compilación.  
  
 Para obtener información sobre cómo crear un archivo del proyecto para un proyecto de C++, consulte [MSBuild (Visual C++)](/cpp/build/msbuild-visual-cpp).  
  
 Este tutorial muestra la forma de crear un archivo básico del proyecto de forma incremental, utilizando solo un editor de texto. El tutorial sigue estos pasos:  
  
1.   Crear un archivo de código fuente de aplicación mínima.  
  
2.   Crear un archivo del proyecto de MSBuild mínimo.  
  
3.   Extender la variable de entorno PATH para incluir MSBuild.  
  
4.   Compilar la aplicación utilizando el archivo del proyecto.  
  
5.   Agregar propiedades para controlar la compilación.  
  
6.   Controlar la compilación cambiando los valores de propiedad.  
  
7.   Agregar destinos a la compilación.  
  
8.   Controlar la compilación especificando destinos.  
  
9.   Compilar de forma incremental.  

Este tutorial muestra la forma de compilar el proyecto en el símbolo del sistema y examinar los resultados. Para obtener más información sobre MSBuild y cómo ejecutar MSBuild en el símbolo del sistema, vea [Tutorial: Usar MSBuild](../msbuild/walkthrough-using-msbuild.md).  

Para completar el tutorial, debe tener instalado .NET Framework (versión 2.0, 3.5, 4.0 o 4.5) porque incluye MSBuild y el compilador de Visual C#, que son necesarios para el tutorial.  
  
## <a name="create-a-minimal-application"></a>Creación de una aplicación mínima  
 En esta sección se muestra la forma de crear un archivo de código fuente de aplicación de Visual C# mínima utilizando un editor de texto.  
  
#### <a name="to-create-the-minimal-application"></a>Para crear la aplicación mínima  
  
1.  En el símbolo del sistema, vaya a la carpeta en la que quiere crear la aplicación, por ejemplo, *\My Documents\\* o *\Desktop\\*.  
  
2.  Escriba **md HelloWorld** para crear una subcarpeta denominada *\HelloWorld\\*.  
  
3.  Escriba **cd HelloWorld** para cambiar a la nueva carpeta.  
  
4.  Inicie el Bloc de notas u otro editor de texto y, a continuación, escriba el código siguiente.  
  
    ```csharp
    using System;  
  
    class HelloWorld  
    {  
        static void Main()  
        {  
    #if DebugConfig  
            Console.WriteLine("WE ARE IN THE DEBUG CONFIGURATION");  
    #endif  
  
            Console.WriteLine("Hello, world!");  
        }  
    }  
    ```  
  
5.  Guarde este archivo de código fuente y denomínelo *Helloworld.cs*.  
  
6.  Escriba **csc helloworld.cs** en el símbolo del sistema para compilar la aplicación.  
  
7.  Escriba **helloworld** en el símbolo del sistema para probar la aplicación.  
  
     El mensaje **Hello, world!** debe mostrarse.  
  
8.  Escriba **del helloworld.exe** en el símbolo del sistema para eliminar la aplicación.  
  
## <a name="create-a-minimal-msbuild-project-file"></a>Creación de un archivo de proyecto de MSBuild mínimo  
 Ahora que tiene un archivo de código fuente de aplicación mínima, puede crear un archivo del proyecto mínimo para compilar la aplicación. Este archivo del proyecto contiene los elementos siguientes:  
  
-   El nodo raíz `Project` necesario.  
  
-   Un nodo `ItemGroup` para contener los elementos.  
  
-   Un elemento que hace referencia al archivo de código fuente de aplicación.  
  
-   Un nodo `Target` para contener las tareas necesarias para compilar la aplicación.  
  
-   Un elemento `Task` para iniciar el compilador de Visual C# con el fin de compilar la aplicación.  
  
#### <a name="to-create-a-minimal-msbuild-project-file"></a>Para crear un archivo del proyecto de MSBuild mínimo  
  
1.  En el editor de texto, reemplace el texto existente utilizando estas dos líneas:  
  
    ```xml  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    </Project>  
    ```  
  
2.  Inserte este nodo `ItemGroup` como elemento secundario del nodo `Project`:  
  
    ```xml  
    <ItemGroup>  
      <Compile Include="helloworld.cs" />  
    </ItemGroup>  
    ```  
  
     Observe que este `ItemGroup` ya contiene un elemento.  
  
3.  Agregue un nodo `Target` como elemento secundario del nodo `Project`. Asigne un nombre al nodo `Build`.  
  
    ```xml  
    <Target Name="Build">  
    </Target>  
    ```  
  
4.  Inserte este elemento de tarea como elemento secundario del nodo `Target`:  
  
    ```xml  
    <Csc Sources="@(Compile)"/>  
    ```  
  
5.  Guarde este archivo del proyecto y denomínelo *Helloworld.csproj*.  

Su archivo del proyecto mínimo debe ser similar al código siguiente:  

```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <ItemGroup>  
    <Compile Include="helloworld.cs" />  
  </ItemGroup>  
  <Target Name="Build">  
    <Csc Sources="@(Compile)"/>    
  </Target>  
</Project>  
```  

Las tareas en el destino Build se ejecutan secuencialmente. En este caso, la tarea `Csc` del compilador de Visual C# es la única tarea. Espera la compilación de una lista de archivos de código fuente y esto se produce mediante el valor del elemento `Compile`. El elemento `Compile` hace referencia a solo un archivo de código fuente, *Helloworld.cs*.  
  
> [!NOTE]
>  En el elemento, puede utilizar el carácter comodín asterisco (\*) para hacer referencia a todos los archivos cuya extensión de nombre de archivo sea *.cs*, del modo siguiente:  
>   
>  `<Compile Include="*.cs" />`  
>   
>  Sin embargo, no se recomienda el uso de caracteres comodín porque dificulta la depuración y la asignación selectiva de destino si se agregan o eliminan archivos de código fuente.  
  
## <a name="extend-the-path-to-include-msbuild"></a>Extensión de la ruta de acceso para incluir MSBuild  
 Antes de poder tener acceso a MSBuild, debe extender la variable de entorno PATH para incluir la carpeta .NET Framework.  
  
#### <a name="to-add-msbuild-to-your-path"></a>Para agregar MSBuild a su ruta de acceso  
  
-   A partir de Visual Studio 2013, puede encontrar *MSBuild.exe* en la carpeta de MSBuild (*%ProgramFiles%\MSBuild* en un sistema operativo de 32 bits o *% ProgramFiles (x86) %\MSBuild* en un sistema operativo de 64 bits).  
  
     En el símbolo del sistema, escriba **set PATH=%PATH%;%ProgramFiles%\MSBuild** o **set PATH=%PATH%;%ProgramFiles(x86)%\MSBuild**.  
  
     Alternativamente, si tiene instalado Visual Studio, puede utilizar el **símbolo del sistema de Visual Studio**, que tiene una ruta de acceso que incluye la carpeta *MSBuild*.  
  
## <a name="use-the-project-file-to-build-the-application"></a>Uso del archivo de proyecto para compilar la aplicación  
 Ahora, para compilar la aplicación, utilice el archivo del proyecto que acaba de crear.  
  
#### <a name="to-build-the-application"></a>Para compilar la aplicación  
  
1.  En el símbolo del sistema, escriba **msbuild helloworld.csproj -t:Build**.  
  
     Esto genera el destino Build del archivo del proyecto Helloworld al llamar al compilador de Visual C# para crear la aplicación Helloworld.  
  
2.  Escriba **helloworld** para probar la aplicación.  
  
     El mensaje **Hello, world!** debe mostrarse.  
  
> [!NOTE]
>  Puede ver más detalles sobre la compilación aumentando el nivel de detalle. Para establecer el nivel de detalle en "detailed", escriba este comando en el símbolo del sistema:  
>   
>  **msbuild helloworld.csproj -t:Build -verbosity:detailed**  
  
## <a name="add-build-properties"></a>Agregar propiedades de compilación  
 Puede agregar propiedades de compilación al archivo del proyecto para controlar mejor la compilación. Agregue ahora estas propiedades:  
  
-   Una propiedad `AssemblyName` para especificar el nombre de la aplicación.  
  
-   Una propiedad `OutputPath` para especificar una carpeta que contenga la aplicación.  
  
#### <a name="to-add-build-properties"></a>Para agregar propiedades de compilación  
  
1.  Escriba **del helloworld.exe** en el símbolo del sistema para eliminar la aplicación existente.  
  
2.  En el archivo del proyecto, inserte este elemento `PropertyGroup` justo después del elemento `Project` de apertura:  
  
    ```xml  
    <PropertyGroup>  
      <AssemblyName>MSBuildSample</AssemblyName>  
      <OutputPath>Bin\</OutputPath>  
    </PropertyGroup>  
    ```  
  
3.  Agregue esta tarea al destino Build, justo antes de la tarea `Csc`:  
  
    ```xml  
    <MakeDir Directories="$(OutputPath)"      Condition="!Exists('$(OutputPath)')" />  
    ```  
  
     La tarea `MakeDir` crea una carpeta denominada por la propiedad `OutputPath`, con tal de que no exista actualmente ninguna carpeta con ese nombre.  
  
4.  Agregue este atributo `OutputAssembly` a la tarea `Csc`.  
  
    ```xml  
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
    ```  
  
     Esto indica al compilador de Visual C# que cree un ensamblado denominado por la propiedad `AssemblyName` y lo coloque en la carpeta denominada por la propiedad `OutputPath`.  
  
5.  Guarde los cambios.  

Su archivo del proyecto debe ser ahora similar al código siguiente:  

```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <AssemblyName>MSBuildSample</AssemblyName>  
    <OutputPath>Bin\</OutputPath>  
  </PropertyGroup>  
  <ItemGroup>  
    <Compile Include="helloworld.cs" />  
  </ItemGroup>  
  <Target Name="Build">  
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />  
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
  </Target>  
</Project>  
```  

> [!NOTE]
>  Se recomienda agregar el delimitador de ruta de acceso de barra diagonal inversa (\\) al final del nombre de la carpeta al especificarlo en el elemento `OutputPath`, en lugar de agregarlo en el atributo `OutputAssembly` de la tarea `Csc`. Por lo tanto,  
>   
>  `<OutputPath>Bin\</OutputPath>`  
>   
>  `OutputAssembly=="$(OutputPath)$(AssemblyName).exe" />`  
>   
>  es mejor que  
>   
>  `<OutputPath>Bin</OutputPath>`  
>   
>  `OutputAssembly=="$(OutputPath)\$(AssemblyName).exe" />`  
  
## <a name="test-the-build-properties"></a>Prueba de las propiedades de compilación  
 Ahora puede compilar la aplicación utilizando el archivo del proyecto en el que utilizó propiedades de compilación para especificar la carpeta de salida y el nombre de aplicación.  
  
#### <a name="to-test-the-build-properties"></a>Para probar las propiedades de compilación  
  
1.  En el símbolo del sistema, escriba **msbuild helloworld.csproj -t:Build**.  
  
     De este modo se crea la carpeta *\Bin\\* y, a continuación, se llama al compilador de Visual C# para crear la aplicación *MSBuildSample* y colocarla en dicha carpeta.  
  
2.  Para comprobar que se ha creado la carpeta *\Bin\\* y que contiene la aplicación *MSBuildSample*, escriba **dir Bin**.  
  
3.  Escriba **Bin\MSBuildSample** para probar la aplicación.  
  
     El mensaje **Hello, world!** debe mostrarse.  
  
## <a name="add-build-targets"></a>Agregar destinos de compilación  
 A continuación, agregue dos destinos más al archivo del proyecto, del siguiente modo:  
  
-   Un destino Clean que elimine los archivos antiguos.  
  
-   Un destino Rebuild que utilice el atributo `DependsOnTargets` para obligar a que la tarea Clean se ejecute antes que la tarea Build.  

Ahora que tiene varios destinos, puede establecer el destino Build como destino predeterminado.  
  
#### <a name="to-add-build-targets"></a>Para agregar destinos de compilación  
  
1.  En el archivo del proyecto, agregue estos dos destinos justo después del destino Build:  
  
    ```xml  
    <Target Name="Clean" >  
      <Delete Files="$(OutputPath)$(AssemblyName).exe" />  
    </Target>  
    <Target Name="Rebuild" DependsOnTargets="Clean;Build" />  
    ```  
  
     El destino Clean llama a la tarea Delete para eliminar la aplicación. El destino Rebuild no se ejecutará hasta que se hayan ejecutado el destino Clean y el destino Build. Aunque el destino Rebuild no tiene tareas, hace que el destino Clean se ejecute antes que el destino Build.  
  
2.  Agregue este atributo `DefaultTargets` al elemento `Project`.  
  
    ```xml  
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ```  
  
     Esto establece el destino Build como destino predeterminado.  

Su archivo del proyecto debe ser ahora similar al código siguiente:  

```xml  
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <AssemblyName>MSBuildSample</AssemblyName>  
    <OutputPath>Bin\</OutputPath>  
  </PropertyGroup>  
  <ItemGroup>  
    <Compile Include="helloworld.cs" />  
  </ItemGroup>  
  <Target Name="Build">  
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />  
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
  </Target>  
  <Target Name="Clean" >  
    <Delete Files="$(OutputPath)$(AssemblyName).exe" />  
  </Target>  
  <Target Name="Rebuild" DependsOnTargets="Clean;Build" />  
</Project>  
```  

## <a name="test-the-build-targets"></a>Prueba de los destinos de compilación  
 Puede utilizar los nuevos destinos de compilación para probar estas características del archivo del proyecto:  
  
-   Compilar la compilación predeterminada.  
  
-   Establecer el nombre de aplicación en el símbolo del sistema.  
  
-   Eliminar la aplicación antes de que se compile otra aplicación.  
  
-   Eliminar la aplicación sin que se compile otra aplicación.  
  
#### <a name="to-test-the-build-targets"></a>Para probar los destinos de compilación  
  
1.  En el símbolo del sistema, escriba **msbuild helloworld.csproj -p:AssemblyName=Greetings**.  
  
     Como no utilizó el modificador **-t** para establecer el destino explícitamente, MSBuild ejecutará el destino Build predeterminado. El modificador **-p** invalida la propiedad `AssemblyName` y le da el nuevo valor, `Greetings`. Esto hace que se cree una aplicación, *Greetings.exe*, en la carpeta *\Bin\\*.  
  
2.  Para comprobar que la carpeta *\Bin\\* contiene la aplicación *MSBuildSample* y la nueva aplicación *Greetings*, escriba **dir Bin**.  
  
3.  Escriba **Bin\Greetings** para probar la aplicación Greetings.  
  
     El mensaje **Hello, world!** debe mostrarse.  
  
4.  Escriba **msbuild helloworld.csproj -t:clean** para eliminar la aplicación MSBuildSample.  
  
     Esto ejecuta la tarea Clean para quitar la aplicación que tiene el valor de propiedad `AssemblyName` predeterminado, `MSBuildSample`.  
  
5.  Escriba **msbuild helloworld.csproj -t:clean -p:AssemblyName=Greetings** para eliminar la aplicación Greetings.  
  
     Esto ejecuta la tarea Clean para quitar la aplicación que tiene el valor de propiedad **AssemblyName** dado, `Greetings`.  
  
6.  Para comprobar que la carpeta *\Bin\\* está ahora vacía, escriba **dir Bin**.  
  
7.  Escriba **msbuild**.  
  
     Aunque no se especifica un archivo de proyecto, MSBuild compila el archivo *helloworld.csproj* porque solo hay un archivo de proyecto en la carpeta actual. Esto hace que se cree la aplicación *MSBuildSample* en la carpeta *\Bin\\*.  
  
     Para comprobar que la carpeta *\Bin\\* contiene la aplicación *MSBuildSample*, escriba **dir Bin**.  
  
## <a name="build-incrementally"></a>Compilación de forma incremental  
 Puede indicar a MSBuild que cree un destino sólo si los archivos de código fuente o los archivos de destino de los que depende el destino han cambiado. MSBuild utiliza la marca de tiempo de un archivo para determinar si ha cambiado.  
  
#### <a name="to-build-incrementally"></a>Para compilar de forma incremental  
  
1.  En el archivo del proyecto, agregue estos atributos al destino Build de apertura:  
  
    ```xml  
    Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe"  
    ```  
  
     Esto especifica que el destino Build depende de los archivos de entrada que se especifican en el grupo de elementos `Compile` y que el destino de salida es el archivo de aplicación.  
  
     El destino Build resultante debe ser similar al código siguiente:  
  
    ```xml  
    <Target Name="Build" Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe">  
      <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />  
      <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
    </Target>  
    ```  
  
2.  Escriba **msbuild -v:d** en el símbolo del sistema para probar el destino Build.  
  
     Recuerde que *helloworld.csproj* es el archivo de proyecto predeterminado y que Build es el destino predeterminado.  
  
     El modificador **-v:d** especifica una descripción detallada del proceso de compilación.  
  
     Se deben mostrar estas líneas:  
  
     **Se omitirá el destino "Build" porque todos los archivos de salida están actualizados respecto a los archivos de entrada.**  
  
     **Archivos de entrada: HelloWorld.cs**  
  
     **Archivos de salida: BinMSBuildSample.exe**  
  
     MSBuild omite el destino Build porque ninguno de los archivos de código fuente ha cambiado desde que la aplicación se compiló por última vez.  
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 En el ejemplo siguiente se muestra un archivo del proyecto que compila una aplicación de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] y registra un mensaje que contiene el nombre del archivo de salida.  
  
### <a name="code"></a>Código  
  
```xml
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>HelloWorldCS</appname>  
    </PropertyGroup>  
  
    <!-- Specify the inputs by type and file name -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using input files of type CSFile -->  
        <CSC  
            Sources = "@(CSFile)"  
            OutputAssembly = "$(appname).exe">  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the executable file that is created -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 En el ejemplo siguiente se muestra un archivo del proyecto que compila una aplicación de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] y registra un mensaje que contiene el nombre del archivo de salida.  
  
### <a name="code"></a>Código  
  
```xml  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>HelloWorldVB</appname>  
    </PropertyGroup>  
  
    <!-- Specify the inputs by type and file name -->  
    <ItemGroup>  
        <VBFile Include = "consolehwvb1.vb"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">      
        <!-- Run the Visual Basic compilation using input files of type VBFile -->  
        <VBC  
            Sources = "@(VBFile)"  
            OutputAssembly= "$(appname).exe">  
            <!-- Set the OutputAssembly attribute of the VBC task  
            to the name of the executable file that is created -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </VBC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
## <a name="whats-next"></a>Pasos adicionales  
 Visual Studio puede realizar automáticamente gran parte del trabajo que se muestra en este tutorial. Para aprender a usar Visual Studio a fin de crear, editar, compilar y probar archivos de proyecto de MSBuild, vea [Tutorial: Usar MSBuild](../msbuild/walkthrough-using-msbuild.md).  
  
## <a name="see-also"></a>Vea también  
[Información general sobre MSBuild](../msbuild/msbuild.md)  
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)