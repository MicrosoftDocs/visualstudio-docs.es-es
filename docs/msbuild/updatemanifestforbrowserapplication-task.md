---
title: UpdateManifestForBrowserApplication (Tarea) | Microsoft Docs
description: Obtenga información sobre cómo MSBuild ejecuta la tarea UpdateManifestForBrowserApplication para agregar el elemento hostInBrowser al manifiesto de aplicación.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UpdateManifestForBrowserApplication task [WPF MSBuild]
- adding the <hostInBrowser /> element to the application manifest [WPF MSBuild]
- building XBAP projects [WPF MSBuild]
- UpdateManifestForBrowserApplication task [WPF MSBuild], parameters
ms.assetid: 653339f7-654b-4d64-a26a-5c9f27036895
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43e8fc7b9b09af51ea3be73409e2dcde9a718cee
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046815"
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication (Tarea)

La tarea <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> se ejecuta para agregar el elemento **\<hostInBrowser />** al manifiesto de aplicación ( *\<projectname>.exe.manifest* ) cuando se compila un proyecto de aplicación de explorador XAML (XBAP).

## <a name="task-parameters"></a>Parámetros de tareas

|Parámetro|Descripción|
|---------------|-----------------|
|`ApplicationManifest`|Parámetro obligatorio de tipo **ITaskItem[]** .<br /><br /> Especifica la ruta de acceso y el nombre del archivo de manifiesto de aplicación al que se quiere agregar el elemento `<hostInBrowser />`.|
|`HostInBrowser`|Parámetro obligatorio de tipo **Boolean**.<br /><br /> Especifica si se debe modificar el manifiesto de aplicación para incluir el elemento **\<hostInBrowser />** . Si es **true** , se incluye un nuevo elemento **\<hostInBrowser />** en el elemento **\<entryPoint />** . La inclusión de elementos es acumulativa: si ya existe un elemento **\<hostInBrowser />** , no se quita ni se sobrescribe. En su lugar, se crea otro elemento **\<hostInBrowser />** . Si es **false** , el manifiesto de aplicación no se modifica.|

## <a name="remarks"></a>Comentarios

 Se ejecutan XBAP mediante la implementación de ClickOnce y, por tanto, se deben publicar con manifiestos de aplicación e implementación compatibles. MSBuild usa la tarea [GenerateApplicationManifest](generateapplicationmanifest-task.md) para generar un manifiesto de aplicación.

 Después, a fin de configurar una aplicación para que se hospede en un explorador, se debe agregar un elemento **\<hostInBrowser />** adicional al manifiesto de aplicación, como se muestra en el ejemplo siguiente:

```xml
<!--MyXBAPApplication.exe.manifest-->
<?xml version="1.0" encoding="utf-8"?>
<asmv1:assembly ... >
    <asmv1:assemblyIdentity ... />
    <application />
    <entryPoint>
      ...
      <hostInBrowser xmlns="urn:schemas-microsoft-com:asm.v3" />
    </entryPoint>
  ...
/>
```

 La tarea <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> se ejecuta cuando se compila un proyecto XBAP con el fin de agregar el elemento `<hostInBrowser />`.

## <a name="example"></a>Ejemplo

 En el ejemplo siguiente se muestra cómo asegurarse de que el elemento `<hostInBrowser />` se incluye en un archivo de manifiesto de aplicación.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="UpdateManifestForBrowserApplicationTask">
    <UpdateManifestForBrowserApplication
      ApplicationManifest="MyXBAPApplication.exe.manifest"
      HostInBrowser="true" />
  </Target>
</Project>
```

## <a name="see-also"></a>Vea también

- [Referencia de MSBuild para WPF](../msbuild/wpf-msbuild-reference.md)
- [Referencia de tareas](../msbuild/wpf-msbuild-task-reference.md)
- [Referencia de MSBuild](../msbuild/msbuild-reference.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
- [Compilar una aplicación de WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Información general sobre las aplicaciones de explorador XAML de WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)