---
title: WriteLinesToFile (Tarea) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WriteLinesToFile task [MSBuild]
- MSBuild, WriteLinesToFile task
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e8fa6ff5dbfcbbeb158f22256e18f6fb90bab348
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341815"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile (tarea)
Escribe las rutas de acceso de los elementos especificados en el archivo de texto especificado.  
  
## <a name="task-parameters"></a>Parámetros de tareas  
 En la siguiente tabla se describen los parámetros de la tarea `WriteLinestoFile` .  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`File`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> requerido.<br /><br /> Especifica el archivo en el que se escriben los elementos.|  
|`Lines`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los elementos que se van a escribir en el archivo.|  
|`Overwrite`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, la tarea sobrescribe cualquier contenido existente en el archivo.|  
|`Encoding`|Parámetro `String` opcional.<br /><br /> Selecciona la codificación de caracteres, por ejemplo, "Unicode".  Vea también <xref:System.Text.Encoding>.|  
  
## <a name="remarks"></a>Comentarios  
 Si `Overwrite` es `true`, crea un archivo, escribe el contenido en el archivo y después lo cierra. Si el archivo de destino ya existe, se sobrescribe. Si `Overwrite` es `false`, anexa el contenido al archivo y crea el archivo de destino si aún no existe.  
  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se usa la tarea `WriteLinesToFile` para escribir las rutas de acceso de los elementos de la colección de elementos `MyItems` en el archivo especificado por la colección de elementos `MyTextFile`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyTextFile Include="Items.txt"/>  
        <MyItems Include="*.cs"/>  
    </ItemGroup>  
  
    <Target Name="WriteToFile">  
        <WriteLinesToFile  
            File="@(MyTextFile)"  
            Lines="@(MyItems)"  
            Overwrite="true"  
            Encoding="Unicode"/>  
    </Target>  
  
</Project>  
```

En este ejemplo se usa una propiedad con nuevas líneas insertadas para escribir un archivo de texto con varias líneas. Si una entrada en `Lines` ha insertado caracteres de nueva línea, las nuevas líneas se incluirán en el archivo de salida. De este modo, puede hacer referencia a las propiedades de varias líneas.

```xml  
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <Target Name="WriteLaunchers" AfterTargets="CopyFilesToOutputDirectory">
      <PropertyGroup>
        <LauncherCmd>
@ECHO OFF
dotnet %~dp0$(AssemblyName).dll %*
        </LauncherCmd>
      </PropertyGroup>

      <WriteLinesToFile
        File="$(OutputPath)$(AssemblyName).cmd"
        Overwrite="true"
        Lines="$(LauncherCmd)" />
  </Target>
</Project>
```  
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)
