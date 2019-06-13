---
title: RegisterAssembly (Tarea) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 488ae44a89c203b70e6c8e635d99eb699349156e
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747321"
---
# <a name="registerassembly-task"></a>RegisterAssembly (tarea)
Lee los metadatos dentro del ensamblado especificado y agrega las entradas necesarias al registro, lo que permite a los clientes COM crear clases de .NET Framework de forma transparente. El comportamiento de esta tarea es similar, pero no idéntico, al de [Regasm.exe (Assembly Registration Tool)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool).

## <a name="parameters"></a>Parámetros
 En la siguiente tabla se describen los parámetros de la tarea `RegisterAssembly` .

|Parámetro|Descripción|
|---------------|-----------------|
|`Assemblies`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica los ensamblados que se van a registrar con COM.|
|`AssemblyListFile`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Contiene información sobre el estado entre las tareas `RegisterAssembly` y [UnregisterAssembly](../msbuild/unregisterassembly-task.md). Esta información impide que la tarea `UnregisterAssembly` intente eliminar del Registro un ensamblado que no se pudo registrar en la tarea `RegisterAssembly`.|
|`CreateCodeBase`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, crea una entrada de código base en el Registro, que especifica la ruta de acceso al archivo de un ensamblado que no está instalado en la memoria caché global de ensamblados. No debe especificar esta opción si posteriormente va a instalar el ensamblado que va a registrar en la caché global de ensamblados.|
|`TypeLibFiles`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica la biblioteca de tipos que se generará a partir del ensamblado especificado. La biblioteca de tipos generada contiene las definiciones de los tipos accesibles definidas dentro del ensamblado. La biblioteca de tipos solo se genera si se cumple una de las condiciones siguientes:<br /><br /> - Una biblioteca de tipos de dicho nombre no existe en esa ubicación.<br />- Una biblioteca de tipos existe pero es anterior al ensamblado que se está pasando.<br /><br /> Si la biblioteca de tipos es más reciente que el ensamblado que se está pasando, no se crea un nuevo ensamblado, aunque se podrá registrar.<br /><br /> Si se especifica este parámetro, debe tener el mismo número de elementos que el parámetro `Assemblies` o en la tarea se producirá un error. Si no se especifica ninguna entrada, la tarea tendrá como valor predefinido el nombre del ensamblado y cambiará la extensión del elemento a *.tlb*.|

## <a name="remarks"></a>Comentarios
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

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
- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)