---
title: Elemento UsingTask (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UsingTask
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UsingTask element [MSBuild]
- <UsingTask> element [MSBuild]
ms.assetid: 20247902-9446-4a1f-8253-5c7a17e4fe43
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 28dba0a2b386cef00daf4827609ce9762c667067
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892966"
---
# <a name="usingtask-element-msbuild"></a>Elemento UsingTask (MSBuild)
Asigna la tarea a la que se hace referencia en un elemento [Tarea](../msbuild/task-element-msbuild.md) al ensamblado que contiene la implementación de la tarea.  

 \<Project>  
 \<UsingTask>  

## <a name="syntax"></a>Sintaxis  

```xml  
<UsingTask TaskName="TaskName"  
    AssemblyName = "AssemblyName"   
    TaskFactory = "ClassName"  
    Condition="'String A'=='String B'" />  
```  

## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  

### <a name="attributes"></a>Atributos  

|Atributo|Descripción|  
|---------------|-----------------|  
|`AssemblyName`|El atributo `AssemblyName` o `AssemblyFile` son obligatorios.<br /><br /> Nombre del ensamblado que se va a cargar. El atributo `AssemblyName` acepta ensamblados con nombre seguro, aunque no es necesario usar nombres seguros. Usar este atributo es equivalente a cargar un ensamblado mediante el método <xref:System.Reflection.Assembly.Load%2A> en .NET.<br /><br /> No puede usar este atributo si se usa el atributo `AssemblyFile`.|  
|`AssemblyFile`|El atributo `AssemblyName` o `AssemblyFile` son obligatorios.<br /><br /> Ruta de acceso del archivo del ensamblado. Este atributo acepta rutas de acceso completas o rutas de acceso relativas. Las rutas de acceso relativas están relacionadas con el directorio del archivo de proyecto o del archivo de destino cuando se declara el elemento `UsingTask`. Usar este atributo es equivalente a cargar un ensamblado mediante el método <xref:System.Reflection.Assembly.LoadFrom%2A> en .NET.<br /><br /> No puede usar este atributo si se usa el atributo `AssemblyName`.|  
|`TaskFactory`|Atributo opcional.<br /><br /> Especifica la clase del ensamblado que es responsable de generar instancias del nombre `Task` especificado.  El usuario también puede especificar `TaskBody` como elemento secundario que el generador de tareas recibe y usa para generar la tarea. El contenido de `TaskBody` es específico del generador de tareas.|  
|`TaskName`|Atributo necesario.<br /><br /> Nombre de la tarea a la que se va a referencia desde un ensamblado. Si puede darse ambigüedad, este atributo siempre debe especificar espacios de nombres completos. En caso de ambigüedad, MSBuild elegirá a una coincidencia arbitraria que podría producir resultados inesperados.|  
|`Condition`|Atributo opcional.<br /><br /> Condición que se va a evaluar. Para obtener más información, consulte [Condiciones](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Elementos secundarios  

|Elemento|Descripción|  
|-------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Conjunto de parámetros que aparecen en la tarea que se genera mediante el objeto `TaskFactory` especificado.|  
|[Task](../msbuild/task-element-msbuild.md)|Datos que se pasan a `TaskFactory` para generar una instancia de la tarea.|  

### <a name="parent-elements"></a>Elementos primarios  

| Elemento | Descripción |
| - | - |
| [Proyecto](../msbuild/project-element-msbuild.md) | Elemento raíz necesario de un archivo de proyecto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] . |

## <a name="remarks"></a>Comentarios  
 Se puede hacer referencia a variables de entorno, propiedades de línea de comandos, propiedades de nivel de proyecto y elementos de nivel de proyecto en los elementos `UsingTask` incluidos en el archivo de proyecto, ya sea directamente o a través de un archivo de proyecto importado. Para obtener más información, consulte [Tareas](../msbuild/msbuild-tasks.md).  

> [!NOTE]
>  Las propiedades y los elementos de nivel de proyecto no tienen ningún sentido si el elemento `UsingTask` proviene de uno de los archivos *.tasks* registrados globalmente con el motor MSBuild. Los valores de nivel de proyecto no son globales en MSBuild.  

 En MSBuild 4.0, el uso de tareas puede cargarse a partir de archivos *.overridetask*.  

## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar el elemento `UsingTask` con un atributo `AssemblyName`.  

```xml  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
              ...  
</ParameterGroup>  
       <TaskBody>  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  

## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar el elemento `UsingTask` con un atributo `AssemblyFile`.  

```xml  
<UsingTask TaskName="Email"  
              AssemblyFile="c:\myTasks\myTask.dll" />  
```  

## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Referencia de esquema de archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)
