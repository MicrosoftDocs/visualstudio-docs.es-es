---
title: RegisterAssembly (Tarea) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RegisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RegisterAssembly task
- RegisterAssembly task [MSBuild]
ms.assetid: ba5f19ac-6764-4d28-9b79-a86de58f8987
caps.latest.revision: 16
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: 7a92736406aedb3706f5101af3e10ec8bb5d3fe4
ms.lasthandoff: 02/22/2017

---
# <a name="registerassembly-task"></a>RegisterAssembly (Tarea)
Lee los metadatos del ensamblado especificado y agrega las entradas necesarias al Registro, lo que permite a los clientes COM crear clases de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] de forma transparente. El comportamiento de esta tarea es similar, pero no idéntico, al de [Regasm.exe (Assembly Registration Tool)](http://msdn.microsoft.com/Library/e190e342-36ef-4651-a0b4-0e8c2c0281cb).  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `RegisterAssembly`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Assemblies`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica los ensamblados que se van a registrar con COM.|  
|`AssemblyListFile`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Contiene información sobre el estado entre las tareas `RegisterAssembly` y [UnregisterAssembly](../msbuild/unregisterassembly-task.md). Impide que la tarea `UnregisterAssembly` intente anular el registro de un ensamblado que no se pudo registrar en la tarea `RegisterAssembly`.|  
|`CreateCodeBase`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, crea una entrada de código base en el Registro, que especifica la ruta de acceso al archivo de un ensamblado que no está instalado en la memoria caché global de ensamblados. No debe especificar esta opción si posteriormente va a instalar el ensamblado que va a registrar en la caché global de ensamblados.|  
|`TypeLibFiles`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica la biblioteca de tipos que se generará a partir del ensamblado especificado. La biblioteca de tipos generada contiene las definiciones de los tipos accesibles definidas dentro del ensamblado. Solo se genera la biblioteca de tipos si se cumple una de las condiciones siguientes:<br /><br /> - Una biblioteca de tipos de dicho nombre no existe en esa ubicación.<br />- Una biblioteca de tipos existe pero es anterior al ensamblado que se está pasando.<br /><br /> Si la biblioteca de tipos es más reciente que el ensamblado que se está pasando, no se creará un nuevo ensamblado, aunque se podrá registrar.<br /><br /> Si se especifica este parámetro, debe tener el mismo número de elementos que el parámetro `Assemblies` o en la tarea se producirá un error. Si no se especifica ninguna entrada, la tarea tendrá como valor predefinido el nombre del ensamblado y cambiará la extensión del elemento a .tlb.|  
  
## <a name="remarks"></a>Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension (Clase base)](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se utiliza la tarea `RegisterAssembly` para generar el ensamblado especificado por la colección de elementos `MyAssemblies`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyAssemblies Include="MyAssembly.dll" />  
    <ItemGroup>  
  
    <Target Name="RegisterAssemblies">  
        <RegisterAssembly  
            Assemblies="@(MyAssemblies)" >  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)
