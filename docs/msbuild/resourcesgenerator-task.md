---
title: ResourcesGenerator (Tarea) | Microsoft Docs
description: Obtenga información sobre cómo MSBuild usa la tarea ResourcesGenerator para insertar uno o varios recursos en un archivo .resources.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- embedding resources into a .resources file [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild], parameters
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a26c8bfc29ca985a725deea6c75b14d68abb9eb4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937893"
---
# <a name="resourcesgenerator-task"></a>ResourcesGenerator (Tarea)

La tarea <xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> inserta uno o varios recursos ( *.jpg*, *.ico*, *.bmp*, XAML en formato binario y en otros tipos de extensiones) en un archivo *.resources*.

## <a name="task-parameters"></a>Parámetros de tareas

|Parámetro|Descripción|
|---------------|-----------------|
|`OutputPath`|Parámetro obligatorio de tipo **String**.<br /><br /> Especifica la ruta de acceso del directorio de salida. Si la ruta de acceso no es una ruta de acceso absoluta, se trata como si fuese una ruta de acceso relativa al directorio raíz del proyecto.|
|`OutputResourcesFile`|Parámetro de salida obligatorio de tipo **ITaskItem[]**.<br /><br /> Especifica la ruta de acceso y el nombre del archivo *.resources* generado. Si la ruta de acceso no es una ruta absoluta, el archivo *.resources* se genera respecto al directorio raíz del proyecto.|
|`ResourcesFiles`|Parámetro obligatorio de tipo **ITaskItem[]** .<br /><br /> Especifica uno o más recursos que se van a insertar en el archivo *.resources* generado.|

## <a name="example"></a>Ejemplo

 En el ejemplo siguiente, se genera un archivo *.resources* con un solo recurso *.bmp*. El recurso *.bmp* se genera en un directorio que es relativo al directorio raíz del proyecto.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.ResourcesGenerator"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="ResourcesGeneratorTask">
    <ResourcesGenerator
      ResourceFiles="Resource1.bmp"
      OutputPath="myresources"
      OutputResourcesFile="myresources\my.resources" />
  </Target>
</Project>
```

## <a name="see-also"></a>Vea también

- [Referencia de MSBuild para WPF](../msbuild/wpf-msbuild-reference.md)
- [Referencia de tareas](../msbuild/wpf-msbuild-task-reference.md)
- [Referencia de MSBuild](../msbuild/msbuild-reference.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
- [Compilar una aplicación de WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)