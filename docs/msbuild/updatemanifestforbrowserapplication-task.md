---
title: UpdateManifestForBrowserApplication (Tarea) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f7e86f07d0806f6ce5873cd91b68b4b32d58f4e6
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220702"
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication (Tarea)
La tarea <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> se ejecuta para agregar el elemento **\<hostInBrowser />** al manifiesto de aplicación (*\<nombreproyecto.exe.manifest*) cuando se compila un proyecto [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)].  
  
## <a name="task-parameters"></a>Parámetros de tareas  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`ApplicationManifest`|Parámetro obligatorio de tipo **ITaskItem[]**.<br /><br /> Especifica la ruta de acceso y el nombre del archivo de manifiesto de aplicación al que se quiere agregar el elemento `<hostInBrowser />`.|  
|`HostInBrowser`|Parámetro obligatorio de tipo **Boolean**.<br /><br /> Especifica si se debe modificar el manifiesto de aplicación para incluir el elemento **\<hostInBrowser />**. Si es **true**, se incluye un nuevo elemento **\<hostInBrowser />** en el elemento **\<entryPoint />**. La inclusión de elementos es acumulativa: si ya existe un elemento **\<hostInBrowser />**, no se quita ni se sobrescribe. En vez de eso, se crea otro elemento **\<hostInBrowser />**. Si es **false**, el manifiesto de aplicación no se modifica.|  
  
## <a name="remarks"></a>Comentarios  
 Se ejecutan [!INCLUDE[TLA2#tla_xbap#plural](../msbuild/includes/tla2sharptla_xbapsharpplural_md.md)] mediante la implementación de [!INCLUDE[TLA#tla_clickonce](../msbuild/includes/tlasharptla_clickonce_md.md)] y, por tanto, se deben publicar con manifiestos de aplicación e implementación compatibles. [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] usa la tarea [GenerateApplicationManifest](generateapplicationmanifest-task.md) para generar un manifiesto de aplicación.  
  
 A continuación, para configurar una aplicación que se va a hospedar en un explorador, debe agregarse al manifiesto de aplicación un elemento adicional, **\<hostInBrowser />**, tal como refleja el ejemplo siguiente:  
  
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
  
 La tarea <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> se ejecuta cuando se compila un proyecto [!INCLUDE[TLA2#tla_xbap](../msbuild/includes/tla2sharptla_xbap_md.md)] con el fin de agregar el elemento `<hostInBrowser />`.  
  
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
 [Referencia de MSBuild para WPF](../msbuild/wpf-msbuild-reference.md)   
 [Referencia de tareas](../msbuild/wpf-msbuild-task-reference.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Compilar una aplicación de WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)   
 [Información general sobre las aplicaciones de explorador XAML de WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)