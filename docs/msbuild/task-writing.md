---
title: "Escribir tareas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, crear tareas"
  - "MSBuild, escribir tareas"
  - "tareas, crear para MSBuild"
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Escribir tareas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las tareas proporcionan el código que se ejecuta durante el proceso de compilación.  Las tareas están contenidas en destinos.  Con [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] se proporciona una biblioteca de tareas típicas, pero también puede crear las suyas propias.  Para obtener más información sobre la biblioteca de tareas proporcionada con [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], vea [Referencia de tareas](../msbuild/msbuild-task-reference.md).  
  
## Tareas  
 Algunos ejemplos de tareas son [Copy](../msbuild/copy-task.md), que copia uno o más archivos; [MakeDir](../msbuild/makedir-task.md), que crea un directorio; y [Csc](../msbuild/csc-task.md), que compila archivos de código fuente de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  Cada tarea se implementa como una clase de .NET que implementa la interfaz <xref:Microsoft.Build.Framework.ITask>, que se define en el ensamblado Microsoft.Build.Framework.dll.  
  
 Al implementar una tarea se pueden utilizar dos enfoques:  
  
-   Implementar la interfaz <xref:Microsoft.Build.Framework.ITask> directamente.  
  
-   Derivar la clase de la clase auxiliar, <xref:Microsoft.Build.Utilities.Task>, que se define en el ensamblado Microsoft.Build.Utilities.dll.  La tarea implementa ITask y proporciona implementaciones predeterminadas de algunos miembros de ITask.  Además, el registro resulta más sencillo.  
  
 En ambos casos, debe agregar a la clase un método denominado `Execute`, al que se llama cuando se ejecuta la tarea.  Este método no utiliza ningún parámetro y devuelve un valor `Boolean`: es `true` si la tarea se ha realizado correctamente o `false` si se ha producido un error.  El ejemplo siguiente muestra una tarea que no realiza ninguna acción y devuelve `true`.  
  
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
  
 El archivo de proyecto siguiente ejecuta esta tarea:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyTarget">  
        <SimpleTask />  
    </Target>  
</Project>  
```  
  
 Cuando se ejecutan tareas, también pueden recibir entradas del archivo de proyecto si se crean propiedades de .NET en la clase de tarea.  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] establece estas propiedades inmediatamente antes de llamar al método `Execute` de la tarea.  Para crear una propiedad de cadena, utilice código de tareas como:  
  
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
  
 El archivo de proyecto siguiente ejecuta esta tarea y establece `MyProperty` en el valor dado:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MyProperty="Value for MyProperty" />  
   </Target>  
</Project>  
```  
  
## Registrar las tareas  
 Si un proyecto es capaz de ejecutar una tarea, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] debe saber cómo localizar el ensamblado que contiene la clase de la tarea.  Las tareas se registran utilizando [Elemento UsingTask \(MSBuild\)](../msbuild/usingtask-element-msbuild.md).  
  
 El archivo Microsoft.Common.Tasks de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] es un archivo de proyecto que contiene una lista de elementos `UsingTask` que registran las tareas suministradas con [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  Este archivo se incluye automáticamente al compilar cada proyecto.  Si una tarea registrada en Microsoft.Common.Tasks también está registrada en el archivo de proyecto actual, éste último tiene prioridad; es decir, puede reemplazar la tarea predeterminada con la suya propia del mismo nombre.  
  
> [!TIP]
>  Puede ver una lista de las tareas que se proporcionan con [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]; para ello, vea el contenido de Microsoft.Common.Tasks.  
  
## Provocar eventos desde una tarea  
 Si la tarea se deriva de la clase auxiliar <xref:Microsoft.Build.Utilities.Task>, puede utilizar cualquiera de los siguientes métodos auxiliares en la clase <xref:Microsoft.Build.Utilities.Task> para generar eventos que se detectarán y mostrarán por cualquiera de los registradores registrados:  
  
```  
public override bool Execute()  
{  
    Log.LogError("messageResource1", "1", "2", "3");  
    Log.LogWarning("messageResource2");  
    Log.LogMessage(MessageImportance.High, "messageResource3");  
    ...  
}  
```  
  
 Si la tarea implementa <xref:Microsoft.Build.Framework.ITask> directamente, también puede provocar estos eventos, pero deberá utilizar la interfaz IBuildEngine.  El ejemplo siguiente muestra una tarea que implementa ITask y provoca un evento personalizado:  
  
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
  
## Forzar a que se establezcan algunos parámetros de las tareas  
 Puede marcar algunas propiedades de las tareas como "requeridas" para que cualquier archivo de proyecto que las ejecute deba establecer valores para ellas o, en caso contrario, la compilación no se producirá.  Para ello, aplique el atributo `[Required]` a la propiedad de .NET en la tarea, como sigue:  
  
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
  
## Ejemplo  
  
### Descripción  
 Esta clase de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] muestra una tarea que deriva de la clase auxiliar <xref:Microsoft.Build.Utilities.Task>.  Esta tarea devuelve `true`, lo que indica que se ha ejecutado correctamente.  
  
### Código  
  
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
  
## Ejemplo  
  
### Descripción  
 Esta clase de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] muestra una tarea que implementa la interfaz <xref:Microsoft.Build.Framework.ITask>.  Esta tarea devuelve `true`, lo que indica que se ha ejecutado correctamente.  
  
### Código  
  
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
  
## Ejemplo  
  
### Descripción  
 Esta clase de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] muestra una tarea que deriva de la clase auxiliar <xref:Microsoft.Build.Utilities.Task>.  Tiene una propiedad de cadena requerida y provoca un evento que aparece en todos los registradores registrados.  
  
### Código  
 [!code-cs[msbuild_SimpleTask3#1](../msbuild/codesnippet/CSharp/task-writing_1.cs)]  
  
## Ejemplo  
  
### Descripción  
 El ejemplo siguiente muestra un archivo de proyecto que invoca la tarea del ejemplo anterior, SimpleTask3.  
  
### Código  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <UsingTask TaskName="SimpleTask3.SimpleTask3"   
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>  
  
    <Target Name="MyTarget">  
        <SimpleTask3 MyProperty="Hello!"/>  
    </Target>  
</Project>  
```  
  
## Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)