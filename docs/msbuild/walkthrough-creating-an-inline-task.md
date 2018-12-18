---
title: 'Tutorial: Creación de una tarea insertada | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
- MSBuild, tasks
ms.assetid: 438194cb-668c-41a9-a7e2-c118d14c1ea7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2091bfa5408c85e4fb4dd4b8973a74d1da8b7132
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49828668"
---
# <a name="walkthrough-create-an-inline-task"></a>Tutorial: Creación de una tarea insertada
Las tareas de MSBuild se crean normalmente compilando una clase que implementa la interfaz <xref:Microsoft.Build.Framework.ITask>. A partir de .NET Framework versión 4, se pueden crear tareas insertadas en el archivo del proyecto. No es necesario crear un ensamblado independiente para hospedar la tarea. Para más información, vea [Tareas insertadas](../msbuild/msbuild-inline-tasks.md).  
  
 En este tutorial se muestra la forma de crear y ejecutar estas tareas insertadas:  
  
-   Una tarea que no tiene parámetros de entrada o de salida.  
  
-   Una tarea que tiene un parámetro de entrada y no tiene parámetros de salida.  
  
-   Una tarea que tiene dos parámetros de entrada y un parámetro de salida que devuelve una propiedad de MSBuild.  
  
-   Una tarea que tiene dos parámetros de entrada y un parámetro de salida que devuelve un elemento de MSBuild.  

Para crear y ejecutar las tareas, utilice Visual Studio y la **ventana del símbolo del sistema de Visual Studio**, del modo siguiente:  
  
1.   Cree un archivo del proyecto de MSBuild utilizando Visual Studio.  
  
2.   Modifique el archivo del proyecto en Visual Studio para crear la tarea insertada.  
  
3.   Utilice la **ventana del símbolo del sistema** para compilar el proyecto y examinar los resultados.  
  
## <a name="create-and-modify-an-msbuild-project"></a>Creación y modificación de un proyecto de MSBuild  
 El sistema de proyectos de Visual Studio se basa en MSBuild. Por consiguiente, puede crear un archivo del proyecto de compilación utilizando Visual Studio. En esta sección, creará un archivo del proyecto de Visual C#. (En su lugar, puede crear un archivo del proyecto de Visual Basic. En el contexto de este tutorial, la diferencia entre los dos archivos del proyecto es menor).  
  
#### <a name="to-create-and-modify-a-project-file"></a>Para crear y modificar un archivo de proyecto  
  
1.  En el menú **Archivo** de Visual Studio, haga clic en **Nuevo** y, a continuación, **Proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, seleccione el tipo de proyecto de **Visual C#** y, a continuación, seleccione la plantilla **Aplicación de Windows Forms**. En el cuadro **Nombre** , escriba `InlineTasks`. Escriba una **ubicación** para la solución, por ejemplo, *D:\\*. Asegúrese de que la casilla **Crear directorio para la solución** esté activada, la opción **Agregar al control de código fuente** esté desactivada y el **Nombre de la solución** sea **InlineTasks**.  
  
3.  Haga clic en **Aceptar** para crear el archivo del proyecto.  
  
3.  En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo de proyecto **InlineTasks** y, a continuación, haga clic en **Descargar el proyecto**.  
  
4.  Haga clic con el botón derecho de nuevo en el nodo del proyecto y, a continuación, haga clic en **Edit InlineTasks.csproj** (Editar InlineTasks.csproj).  
  
     El archivo del proyecto aparece en el editor de código.  
  
## <a name="add-a-basic-hello-task"></a>Adición de una tarea básica Hello  
 Ahora, agregue al archivo del proyecto una tarea básica que muestre el mensaje "Hello, world!". Además, agregue un destino TestBuild predeterminado para llamar a la tarea.  
  
#### <a name="to-add-a-basic-hello-task"></a>Para agregar una tarea básica Hello  
  
1. En el nodo raíz `Project`, cambie el atributo `DefaultTargets` a `TestBuild`. El nodo `Project` resultante debe parecerse al de este ejemplo:  
  
   ```xml
   <Project ToolsVersion="4.0" DefaultTargets="TestBuild" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   ```
  
2. Agregue la tarea insertada y el destino siguientes al archivo del proyecto, justo delante de la etiqueta `</Project>`.  
  
   ```xml  
   <UsingTask TaskName="Hello" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
     <ParameterGroup />  
     <Task>  
       <Code Type="Fragment" Language="cs">  
         Log.LogMessage("Hello, world!", MessageImportance.High);  
       </Code>  
     </Task>  
   </UsingTask>  
   <Target Name="TestBuild">  
     <Hello />  
   </Target>  
   ```  
  
3. Guarde el archivo de proyecto.  
  
   Este código crea una tarea insertada que se denomina Hello y no tiene parámetros, referencias o instrucciones `Using`. La tarea Hello contiene simplemente una línea de código, que muestra un mensaje de saludo en el dispositivo de registro predeterminado, normalmente la ventana de la consola.  
  
### <a name="run-the-hello-task"></a>Ejecución de la tarea Hello  
 Ejecute MSBuild utilizando la **ventana del símbolo del sistema** para crear la tarea Hello y procesar el destino TestBuild que la invoca.  
  
##### <a name="to-run-the-hello-task"></a>Para ejecutar la tarea Hello  
  
1. Haga clic en **Inicio** y en **Todos los programas** y, a continuación, busque la carpeta **Visual Studio Tools** y haga clic en **Símbolo del sistema de Visual Studio**.  
  
2. En la **ventana del símbolo del sistema**, busque la carpeta que contiene el archivo del proyecto; en este caso, *D:\InlineTasks\InlineTasks\\*.  
  
3. Escriba **msbuild** sin modificadores de comando y, a continuación, presione **ENTRAR**. De forma predeterminada, esto compila el archivo *InlineTasks.csproj* y procesa el destino TestBuild predeterminado, que llama a la tarea Hello.  
  
4. Examine la salida en la **ventana del símbolo del sistema**. Debe ver esta línea:  
  
    `Hello, world!`  
  
   > [!NOTE]
   >  Si no ve el mensaje de saludo, intente guardar de nuevo el archivo del proyecto y, a continuación, ejecute la tarea Hello.  
  
   Puede cambiar el archivo del proyecto y ver rápidamente los resultados alternando entre el editor de código y la **ventana del símbolo del sistema**.  
  
## <a name="define-the-echo-task"></a>Definición de la tarea Echo  
 Cree una tarea insertada que acepte un parámetro de cadena y muestre la cadena en el dispositivo de registro predeterminado.  
  
#### <a name="to-define-the-echo-task"></a>Para definir la tarea Echo  
  
1. En el editor de código, reemplace la tarea Hello y el destino TestBuild utilizando el código siguiente.  
  
   ```xml  
   <UsingTask TaskName="Echo" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
     <ParameterGroup>  
       <Text Required="true" />  
     </ParameterGroup>  
     <Task>  
       <Code Type="Fragment" Language="cs">  
         Log.LogMessage(Text, MessageImportance.High);  
       </Code>  
     </Task>  
   </UsingTask>  
   <Target Name="TestBuild">  
     <Echo Text="Greetings!" />  
   </Target>  
   ```  
  
2. En la **ventana del símbolo del sistema**, escriba **msbuild** sin modificadores de comando y, a continuación, presione **ENTRAR**. De forma predeterminada, esto procesa el destino TestBuild predeterminado, que llama a la tarea Echo.  
  
3. Examine la salida en la **ventana del símbolo del sistema**. Debe ver esta línea:  
  
    `Greetings!`  
  
   Este código define una tarea insertada que se denomina Echo y tiene simplemente un parámetro de entrada necesario Text. De forma predeterminada, los parámetros son de tipo System.String. El valor del parámetro Text se establece cuando el destino TestBuild llama a la tarea Echo.  
  
## <a name="define-the-adder-task"></a>Definición de una tarea Adder  
 Cree una tarea insertada que agregue dos parámetros enteros y emita su suma como una propiedad de MSBuild.  
  
#### <a name="to-define-the-adder-task"></a>Para definir la tarea Adder  
  
1. En el editor de código, reemplace la tarea Echo y el destino TestBuild utilizando el código siguiente.  
  
   ```xml  
   <UsingTask TaskName="Adder" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
     <ParameterGroup>  
       <A ParameterType="System.Int32" Required="true" />  
       <B ParameterType="System.Int32" Required="true" />  
       <C ParameterType="System.Int32" Output="true" />  
     </ParameterGroup>  
     <Task>  
       <Code Type="Fragment" Language="cs">  
         C = A + B;  
       </Code>  
     </Task>  
   </UsingTask>    
   <Target Name="TestBuild">  
     <Adder A="4" B="5">  
       <Output PropertyName="Sum" TaskParameter="C" />  
     </Adder>  
     <Message Text="The sum is $(Sum)" Importance="High" />  
   </Target>  
   ```  
  
2. En la **ventana del símbolo del sistema**, escriba **msbuild** sin modificadores de comando y, a continuación, presione **ENTRAR**. De forma predeterminada, esto procesa el destino TestBuild predeterminado, que llama a la tarea Echo.  
  
3. Examine la salida en la **ventana del símbolo del sistema**. Debe ver esta línea:  
  
    `The sum is 9`  
  
   Este código define una tarea insertada que se denomina Adder y tiene dos parámetros de entrada enteros necesarios, A y B, y un parámetro de salida entero, C. La tarea Adder agrega los dos parámetros de entrada y devuelve la suma en el parámetro de salida. La suma se emite como la propiedad `Sum` de MSBuild. Los valores de los parámetros de entrada se establecen cuando el destino TestBuild llama a la tarea Adder.  
  
## <a name="define-the-regx-task"></a>Definición de la tarea RegX  
 Cree una tarea insertada que acepte un grupo de elementos y una expresión regular y devuelva una lista de todos los elementos cuyo contenido de archivo coincida con la expresión.  
  
#### <a name="to-define-the-regx-task"></a>Para definir la tarea RegX  
  
1. En el editor de código, reemplace la tarea Adder y el destino TestBuild utilizando el código siguiente.  
  
   ```xml  
   <UsingTask TaskName="RegX" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
     <ParameterGroup>  
       <Expression Required="true" />  
       <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />  
       <Result ParameterType="Microsoft.Build.Framework.ITaskItem[]" Output="true" />  
     </ParameterGroup>  
     <Task>  
       <Using Namespace="System.Text.RegularExpressions"/>  
       <Code Type="Fragment" Language="cs">  
   <![CDATA[  
         if (Files.Length > 0)  
         {  
           Result = new TaskItem[Files.Length];  
           for (int i = 0; i < Files.Length; i++)  
           {  
             ITaskItem item = Files[i];  
             string path = item.GetMetadata("FullPath");  
             using(StreamReader rdr = File.OpenText(path))  
             {  
               if (Regex.Match(rdr.ReadToEnd(), Expression).Success)  
               {  
                 Result[i] = new TaskItem(item.ItemSpec);  
               }  
             }  
           }  
         }  
   ]]>  
       </Code>  
     </Task>  
   </UsingTask>    
   <Target Name="TestBuild">  
     <RegX Expression="public|protected" Files="@(Compile)">  
       <Output ItemName="MatchedFiles" TaskParameter="Result" />  
     </RegX>  
     <Message Text="Input files: @(Compile)" Importance="High" />  
     <Message Text="Matched files: @(MatchedFiles)" Importance="High" />  
   </Target>  
   ```  
  
2. En la **ventana del símbolo del sistema**, escriba **msbuild** sin modificadores de comando y, a continuación, presione **ENTRAR**. De forma predeterminada, esto procesa el destino TestBuild predeterminado, que llama a la tarea RegX.  
  
3. Examine la salida en la **ventana del símbolo del sistema**. Debe ver las siguientes líneas:  
  
   ```
   Input files: Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
   ```  
  
   ```
   Matched files: Form1.cs;Form1.Designer.cs;Properties\Settings.Designer.cs
   ```  
  
   Este código define una tarea insertada que se denomina RegX y tiene estos tres parámetros:  
  
- `Expression` es un parámetro de entrada de cadena necesario que tiene un valor que es la expresión regular con que se va a hacer coincidir. En este ejemplo, la expresión coincide con las palabras "public" o "protected".  
  
- `Files` es un parámetro de entrada de lista de elementos necesario que tiene un valor que es una lista de archivos cuya coincidencia se va a buscar. En este ejemplo, `Files` se establece en el elemento `Compile`, que enumera los archivos de origen del proyecto.  
  
- `Result` es un parámetro de salida que tiene un valor que es la lista de archivos cuyo contenido coincide con la expresión regular.  
  
  El valor de los parámetros de entrada se establece cuando el destino TestBuild llama a la tarea RegX. La tarea RegX lee todos los archivos y devuelve la lista de archivos que coincide con la expresión regular. Esta lista se devuelve como el parámetro de salida `Result`, que se emite como el elemento `MatchedFiles` de MSBuild.  
  
### <a name="handle-reserved-characters"></a>Control de caracteres reservados  
 El analizador de MSBuild procesa las tareas insertadas como XML. Los caracteres que tienen significado reservado en XML, por ejemplo "\<" y ">", se detectan y controlan como si fueran XML, y no código fuente de .NET. Para incluir los caracteres reservados en expresiones de código como `Files.Length > 0`, escriba el elemento `Code` para que su contenido se incluya en una expresión CDATA, del modo siguiente:  
  
 ```xml
<Code Type="Fragment" Language="cs">  
  <![CDATA[  
  
  // Your code goes here.  
  
  ]]>  
</Code>  
```  

## <a name="see-also"></a>Vea también  
 [Tareas insertadas](../msbuild/msbuild-inline-tasks.md)   
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Destinos](../msbuild/msbuild-targets.md)