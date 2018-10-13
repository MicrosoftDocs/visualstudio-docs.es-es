---
title: Tareas insertadas de MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: e72e6506-4a11-4edf-ae8d-cfb5a3b9d8a0
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b706aa4de24152a7cf656b2cec9aee64f36d7773
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223462"
---
# <a name="msbuild-inline-tasks"></a>Tareas insertadas de MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Las tareas de MSBuild se crean normalmente compilando una clase que implementa la interfaz <xref:Microsoft.Build.Framework.ITask>. Para obtener más información, consulte [Tareas](../msbuild/msbuild-tasks.md).  
  
 A partir de .NET Framework versión 4, se pueden crear tareas insertadas en el archivo del proyecto. No es necesario crear un ensamblado independiente para hospedar la tarea. Esto facilita el seguimiento del código fuente y la implementación de la tarea. El código fuente se integra en el script.  
  
## <a name="the-structure-of-an-inline-task"></a>Estructura de una tarea insertada  
 Una tarea insertada está contenida en un elemento [UsingTask](../msbuild/usingtask-element-msbuild.md). La tarea insertada y el elemento `UsingTask` que la contiene se incluyen normalmente en un archivo .targets y se importan en otros archivos del proyecto según se requiera. A continuación se muestra una tarea insertada básica. Observe que no se realiza ninguna acción.  
  
```  
<Project ToolsVersion="12.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- This simple inline task does nothing. -->  
  <UsingTask  
    TaskName="DoNothing"  
    TaskFactory="CodeTaskFactory"  
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v12.0.dll" >  
    <ParameterGroup />  
    <Task>  
      <Reference Include="" />  
      <Using Namespace="" />  
      <Code Type="Fragment" Language="cs">  
      </Code>  
    </Task>  
  </UsingTask>  
</Project>  
```  
  
 El elemento `UsingTask` del ejemplo tiene tres atributos que describen la tarea y el generador de tareas insertadas que lo compila.  
  
-   El atributo `TaskName` asigna un nombre a la tarea, en este caso, `DoNothing`.  
  
-   El atributo `TaskFactory` asigna un nombre a la clase que implementa el generador de tareas insertadas.  
  
-   El atributo `AssemblyFile` proporciona la ubicación del generador de tareas insertadas. Alternativamente, puede utilizar el atributo `AssemblyName` para especificar el nombre completo de la clase de generador de tareas insertadas, que está ubicada normalmente en la caché global de ensamblados (GAC).  
  
 Los elementos restantes de la tarea `DoNothing` están vacíos y se proporcionan para mostrar el orden y la estructura de una tarea insertada. Un ejemplo más completo se presenta posteriormente en este tema.  
  
-   El elemento `ParameterGroup` es opcional. Cuando se especifica, declara los parámetros para la tarea. Para obtener más información sobre los parámetros de entrada y salida, vea "Parámetros de entrada y salida" más adelante en este tema.  
  
-   El elemento `Task` describe y contiene el código fuente de la tarea.  
  
-   El elemento `Reference` especifica las referencias a los ensamblados de .NET que se utilizan en el código. Esto es equivalente a agregar una referencia a un proyecto en Visual Studio. El atributo `Include` especifica la ruta de acceso del ensamblado al que se hace referencia.  
  
-   El elemento `Using` enumera los espacios de nombres a los que se desea obtener acceso. Esto es similar a la instrucción `Using` de Visual C#. El atributo `Namespace` especifica el espacio de nombres que se va a incluir.  
  
 Los elementos `Reference` y `Using` son independientes del lenguaje. Las tareas insertadas se pueden escribir en cualquiera de los lenguajes CodeDom para .NET admitidos, por ejemplo, Visual Basic o Visual C#.  
  
> [!NOTE]
>  Los elementos contenidos en el elemento `Task` son específicos del generador de tareas, en este caso, el generador de tareas de código.  
  
### <a name="code-element"></a>Elemento de código  
 El último elemento secundario que aparece dentro del elemento `Task` es el elemento `Code`. El elemento `Code` contiene o localiza el código que se desea compilar en una tarea. Lo que se incluye en el elemento `Code` depende de cómo se desea escribir la tarea.  
  
 El atributo `Language` especifica el lenguaje en el que se escribe el código. Los valores aceptables son `cs` para C#, `vb` para Visual Basic.  
  
 El atributo `Type` especifica el tipo de código que se encuentra en el elemento `Code`.  
  
-   Si el valor de `Type` es `Class`, el elemento `Code` contiene el código para una clase que deriva de la interfaz <xref:Microsoft.Build.Framework.ITask>.  
  
-   Si el valor de `Type` es `Method`, el código define un reemplazo del método `Execute` de la interfaz <xref:Microsoft.Build.Framework.ITask>.  
  
-   Si el valor de `Type` es `Fragment`, el código define el contenido del método `Execute`, pero no la firma o la instrucción `return`.  
  
 El propio código aparece normalmente entre un marcador `<![CDATA[` y un marcador `]]>`. Dado que el código está en una sección CDATA, no tiene que preocuparse de anteponer caracteres de escape a los caracteres reservados, como "\<" o ">".  
  
 Alternativamente, puede utilizar el atributo `Source` del elemento `Code` para especificar la ubicación de un archivo que contiene el código para la tarea. El código del archivo de código fuente debe ser del tipo especificado por el atributo `Type`. Si el atributo `Source` está presente, el valor predeterminado de `Type` es `Class`. Si `Source` no está presente, el valor predeterminado es `Fragment`.  
  
> [!NOTE]
>  Al definir la clase de tarea en el archivo de origen, el nombre de clase debe corresponder al atributo `TaskName` del elemento [UsingTask](../msbuild/usingtask-element-msbuild.md) correspondiente.  
  
## <a name="hello-world"></a>Hello World  
 A continuación se muestra una tarea insertada más completa. La tarea HelloWorld muestra "Hello, world!" en el dispositivo de registro de errores predeterminado, que suele ser la consola del sistema o la ventana de **salida** de Visual Studio. El elemento `Reference` del ejemplo se incluye solamente a efectos de ilustración.  
  
```  
<Project ToolsVersion="12.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- This simple inline task displays "Hello, world!" -->  
  <UsingTask  
    TaskName="HelloWorld"  
    TaskFactory="CodeTaskFactory"  
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
    <ParameterGroup />  
    <Task>  
      <Reference Include="System.Xml"/>  
      <Using Namespace="System"/>  
      <Using Namespace="System.IO"/>  
      <Code Type="Fragment" Language="cs">  
<![CDATA[  
// Display "Hello, world!"  
Log.LogError("Hello, world!");  
]]>  
      </Code>  
    </Task>  
  </UsingTask>  
</Project>  
```  
  
 Puede guardar la tarea HelloWorld en un archivo denominado HelloWorld.targets y, a continuación, invocarlo desde un proyecto del modo siguiente.  
  
```  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <Import Project="HelloWorld.targets" />  
  <Target Name="Hello">  
    <HelloWorld />  
  </Target>  
</Project>  
```  
  
## <a name="input-and-output-parameters"></a>Parámetros de entrada y salida  
 Los parámetros de las tareas insertadas son elementos secundarios de un elemento `ParameterGroup`. Cada parámetro toma el nombre del elemento que lo define. En el código siguiente se define el parámetro `Text`.  
  
```  
<ParameterGroup>  
    <Text />  
</ParameterGroup>  
```  
  
 Los parámetros pueden tener uno o más de estos atributos:  
  
-   `Required` es un atributo opcional que es `false` de forma predeterminada. Si es `true`, el parámetro es necesario y se le debe proporcionar un valor antes de llamar a la tarea.  
  
-   `ParameterType` es un atributo opcional que es `System.String` de forma predeterminada. Se puede establecer en cualquier tipo completo que sea un elemento o un valor que se pueda convertir a y de una cadena utilizando System.Convert.ChangeType. (En otras palabras, cualquier tipo que se pueda pasar a y desde una tarea externa).  
  
-   `Output` es un atributo opcional que es `false` de forma predeterminada. Si es `true`, se debe proporcionar al parámetro un valor antes de volver del método Execute.  
  
 Por ejemplo,  
  
```  
<ParameterGroup>  
    <Expression Required="true" />  
      <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />  
    <Tally ParameterType="System.Int32" Output="true" />  
</ParameterGroup>  
```  
  
 define estos tres parámetros:  
  
-   `Expression` es un parámetro de entrada necesario de tipo System.String.  
  
-   `Files` es un parámetro de entrada de lista de elementos necesario.  
  
-   `Tally` es un parámetro de salida de tipo System.Int32.  
  
 Si el elemento `Code` tiene el atributo `Type` de `Fragment` o `Method`, las propiedades se crean automáticamente para cada parámetro. De lo contrario, las propiedades se deben declarar explícitamente en el código fuente de la tarea y deben coincidir exactamente con sus definiciones de parámetro.  
  
## <a name="example"></a>Ejemplo  
 La tarea insertada siguiente reemplaza cada aparición de un token en el archivo determinado por el valor determinado.  
  
```  
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="12.0">  
  
  <UsingTask TaskName="TokenReplace" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v12.0.dll">  
    <ParameterGroup>  
      <Path ParameterType="System.String" Required="true" />  
      <Token ParameterType="System.String" Required="true" />  
      <Replacement ParameterType="System.String" Required="true" />  
    </ParameterGroup>  
    <Task>  
      <Code Type="Fragment" Language="cs"><![CDATA[  
string content = File.ReadAllText(Path);  
content = content.Replace(Token, Replacement);  
File.WriteAllText(Path, content);  
  
]]></Code>  
    </Task>  
  </UsingTask>  
  
  <Target Name='Demo' >  
    <TokenReplace Path="C:\Project\Target.config" Token="$MyToken$" Replacement="MyValue"/>  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Tutorial: Crear una tarea insertada](../msbuild/walkthrough-creating-an-inline-task.md)



