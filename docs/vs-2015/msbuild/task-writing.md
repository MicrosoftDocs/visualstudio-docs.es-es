---
title: Escribir tareas | Microsoft Docs
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
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4b15434c75fb4cd2a295789794f6c9f8eb882bb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49254902"
---
# <a name="task-writing"></a>Escribir tareas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Las tareas proporcionan el código que se ejecuta durante el proceso de compilación. Las tareas están contenidas en destinos. En [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] se incluye una biblioteca de tareas típicas, y también puede crear sus propias tareas. Para obtener más información sobre la biblioteca de tareas incluida en [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], consulte [Referencia de tareas](../msbuild/msbuild-task-reference.md).  
  
## <a name="tasks"></a>Tareas  
 Algunos ejemplos de tareas son [Copy](../msbuild/copy-task.md), que copia uno o más archivos, [MakeDir](../msbuild/makedir-task.md), que crea un directorio, y [Csc](../msbuild/csc-task.md), que compila archivos de código fuente [!INCLUDE[csprcs](../includes/csprcs-md.md)]. Cada tarea se implementa como una clase .NET que, a su vez, implementa la interfaz <xref:Microsoft.Build.Framework.ITask>, definida en el ensamblado Microsoft.Build.Framework.dll.  
  
 Al implementar una tarea, se pueden utilizar dos métodos:  
  
-   Implementar la interfaz <xref:Microsoft.Build.Framework.ITask> directamente.  
  
-   Derive la clase de la clase del asistente, <xref:Microsoft.Build.Utilities.Task>, que se define en el ensamblado Microsoft.Build.Utilities.dll. La tarea implementa ITask y proporciona implementaciones predeterminadas de algunos miembros ITask. Además, el registro es más sencillo.  
  
 En ambos casos, debe agregar a la clase un método denominado `Execute`, que es el método al que se llama cuando se ejecuta la tarea. Este método no utiliza ningún parámetro y devuelve un valor `Boolean`: `true` si la tarea se realizó correctamente o `false` si se produjo un error. En el ejemplo siguiente se muestra una tarea que no realiza ninguna acción y devuelve `true`.  
  
```  
using System;  
using Microsoft.Build.Framework;  
using Microsoft.Build.Utilities;  
  
namespace MyTasks  
{  
    public class SimpleTask : Task  
    {  
        public override bool Execute()  
        {  
            return true;  
        }  
    }  
}  
```  
  
 El siguiente archivo de proyecto ejecuta esta tarea:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyTarget">  
        <SimpleTask />  
    </Target>  
</Project>  
```  
  
 Mientras se ejecutan las tareas, también pueden recibir entradas del archivo del proyecto si crea las propiedades de .NET en la clase de tarea. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] establece inmediatamente estas propiedades antes de llamar al método `Execute` de la tarea. Para crear una propiedad de cadena, utilice código de tarea como:  
  
```  
using System;  
using Microsoft.Build.Framework;  
using Microsoft.Build.Utilities;  
  
namespace MyTasks  
{  
    public class SimpleTask : Task  
    {  
        public override bool Execute()  
        {  
            return true;  
         }  
  
        private string myProperty;  
        public string MyProperty  
        {  
            get { return myProperty; }  
            set { myProperty = value; }  
        }  
    }  
}  
```  
  
 El siguiente archivo del proyecto ejecuta esta tarea y establece `MyProperty` al valor dado:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MyProperty="Value for MyProperty" />  
   </Target>  
</Project>  
```  
  
## <a name="registering-tasks"></a>Registro de tareas  
 Si un proyecto va a ejecutar una tarea, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] debe saber cómo localizar el ensamblado que contiene la clase de tarea. Las tareas se registran mediante el [elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).  
  
 El archivo [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Microsoft.Common.Tasks es un archivo del proyecto que contiene una lista de elementos `UsingTask` que registran todas las tareas que se proporcionan con [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Este archivo se incluye automáticamente al compilar cada proyecto. Si una tarea registrada en Microsoft.Common.Tasks también está registrada en el archivo del proyecto actual, este tiene prioridad; es decir, puede reemplazar una tarea predeterminada por una tarea que tiene el mismo nombre.  
  
> [!TIP]
>  Para ver una lista de las tareas que se proporcionan con [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], puede visualizar el contenido de Microsoft.Common.Tasks.  
  
## <a name="raising-events-from-a-task"></a>Generación de eventos de una tarea  
 Si la tarea se deriva de la clase del asistente <xref:Microsoft.Build.Utilities.Task>, puede usar cualquiera de los siguientes métodos del asistente en la clase <xref:Microsoft.Build.Utilities.Task> para generar eventos que cualquier registrador registrado detectará y mostrará:  
  
```  
public override bool Execute()  
{  
    Log.LogError("messageResource1", "1", "2", "3");  
    Log.LogWarning("messageResource2");  
    Log.LogMessage(MessageImportance.High, "messageResource3");  
    ...  
}  
```  
  
 Si la tarea implementa directamente <xref:Microsoft.Build.Framework.ITask>, todavía puede generar dichos eventos, pero debe utilizar la interfaz IBuildEngine. En el ejemplo siguiente se muestra una tarea que implementa ITask y genera un evento personalizado:  
  
```  
public class SimpleTask : ITask  
{  
    private IBuildEngine buildEngine;  
    public IBuildEngine BuildEngine  
    {  
        get{ return buildEngine; }  
        set{ buildEngine = value; }  
    }  
  
    public override bool Execute()  
    {  
        TaskEventArgs taskEvent =  
            new TaskEventArgs(BuildEventCategory.Custom,  
            BuildEventImportance.High, "Important Message",  
           "SimpleTask");  
        BuildEngine.LogBuildEvent(taskEvent);  
        return true;  
    }  
}  
```  
  
## <a name="requiring-task-parameters-to-be-set"></a>Requerir parámetros de tareas que se deben establecer  
 Puede marcar determinadas propiedades de la tarea como "necesarias", de modo que cualquier archivo del proyecto que ejecute la tarea debe establecer los valores de estas propiedades o se produce un error en la compilación. Aplique el atributo `[Required]` a la propiedad de .NET en la tarea como se indica a continuación:  
  
```  
private string requiredProperty;  
  
[Required]  
public string RequiredProperty  
{  
    get { return requiredProperty; }  
    set { requiredProperty = value; }  
}  
```  
  
 <xref:Microsoft.Build.Framework.RequiredAttribute> define el atributo `[Required]` en el espacio de nombres <xref:Microsoft.Build.Framework>.  
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 La clase [!INCLUDE[csprcs](../includes/csprcs-md.md)] siguiente muestra una tarea que deriva de la clase del asistente <xref:Microsoft.Build.Utilities.Task>. Esta tarea devuelve `true`, lo que indica que se ha realizado correctamente.  
  
### <a name="code"></a>Código  
  
```  
using System;  
using Microsoft.Build.Utilities;  
  
namespace SimpleTask1  
{  
    public class SimpleTask1: Task  
    {  
        public override bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 La clase [!INCLUDE[csprcs](../includes/csprcs-md.md)] siguiente muestra una tarea que implementa la interfaz <xref:Microsoft.Build.Framework.ITask>. Esta tarea devuelve `true`, lo que indica que se ha realizado correctamente.  
  
### <a name="code"></a>Código  
  
```  
using System;  
using Microsoft.Build.Framework;  
  
namespace SimpleTask2  
{  
    public class SimpleTask2: ITask  
    {  
        //When implementing the ITask interface, it is necessary to  
        //implement a BuildEngine property of type  
        //Microsoft.Build.Framework.IBuildEngine. This is done for  
        //you if you derive from the Task class.  
        private IBuildEngine buildEngine;  
        public IBuildEngine BuildEngine  
        {  
            get  
            {  
                return buildEngine;  
            }  
            set  
            {  
                buildEngine = value;  
            }  
         }  
  
        // When implementing the ITask interface, it is necessary to  
        // implement a HostObject property of type Object.  
        // This is done for you if you derive from the Task class.  
        private Object hostObject;  
        public Object HostObject  
        {  
            get  
            {  
                return hostObject;  
            }  
  
            set  
            {  
                hostObject = value;  
            }  
        }  
  
        public bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 Esta clase [!INCLUDE[csprcs](../includes/csprcs-md.md)] muestra una tarea que deriva de la clase del asistente <xref:Microsoft.Build.Utilities.Task>. Tiene una propiedad de cadena necesaria y genera un evento que todos los registradores registrados muestran.  
  
### <a name="code"></a>Código  
 [!code-csharp[msbuild_SimpleTask3#1](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleTask3/CS/SimpleTask3.cs#1)]  
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 En el ejemplo siguiente se muestra un archivo del proyecto que invoca la tarea del ejemplo anterior, SimpleTask3.  
  
### <a name="code"></a>Código  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <UsingTask TaskName="SimpleTask3.SimpleTask3"   
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>  
  
    <Target Name="MyTarget">  
        <SimpleTask3 MyProperty="Hello!"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)



