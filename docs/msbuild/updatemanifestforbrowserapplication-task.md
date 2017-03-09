---
title: "UpdateManifestForBrowserApplication (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "agregar el elemento <hostInBrowser /> al manifiesto de aplicación [WPF MSBuild]"
  - "compilar proyectos XBAP [WPF MSBuild]"
  - "UpdateManifestForBrowserApplication (tarea) [WPF MSBuild]"
  - "UpdateManifestForBrowserApplication (tarea) [WPF MSBuild], parámetros"
ms.assetid: 653339f7-654b-4d64-a26a-5c9f27036895
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# UpdateManifestForBrowserApplication (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La tarea <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> se ejecuta para agregar el elemento **\<hostInBrowser \/\>** al manifiesto de aplicación \(*nombreproyecto*.exe.manifest\) cuando se compila un proyecto [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)].  
  
## Parámetros de tareas  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`ApplicationManifest`|Se requiere el parámetro **ITaskItem\[\]**.<br /><br /> Especifica la ruta de acceso y el nombre del archivo de manifiesto de aplicación al que se quiere agregar el elemento `<hostInBrowser />`.|  
|`HostInBrowser`|Se requiere el parámetro **Boolean**.<br /><br /> Especifica si se debe modificar el manifiesto de aplicación para incluir el elemento **\<hostInBrowser \/\>**.  Si es **true**, se incluye un nuevo elemento `<`**hostInBrowser \/\>** en el elemento **\<entryPoint \/\>**.  Tenga en cuenta que la inclusión de elementos es acumulativa: si ya existe un elemento **\<hostInBrowser \/\>**, no se quita ni se sobrescribe.  En vez de eso, se crea otro elemento **\<hostInBrowser \/\>**.  Si es **false**, el manifiesto de aplicación no se modifica.|  
  
## Comentarios  
 Los [!INCLUDE[TLA2#tla_xbap#plural](../msbuild/includes/tla2sharptla_xbapsharpplural_md.md)] se ejecutan mediante la implementación de [!INCLUDE[TLA#tla_clickonce](../msbuild/includes/tlasharptla_clickonce_md.md)] y, por tanto, deben publicarse con manifiestos de aplicación e implementación compatibles.  [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] usa la tarea [GenerateApplicationManifest](http://msdn2.microsoft.com/library/6wc2ccdc.aspx) para generar un manifiesto de aplicación.  
  
 A continuación, para configurar una aplicación que se va a hospedar en un explorador, debe agregarse al manifiesto de aplicación un elemento adicional,  **\<hostInBrowser \/\>**, tal como refleja el ejemplo siguiente:  
  
```  
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
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo asegurarse de que el elemento `<hostInBrowser />` se incluye en un archivo de manifiesto de aplicación.  
  
```  
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
  
## Vea también  
 [Referencia de MSBuild para WPF](../msbuild/wpf-msbuild-reference.md)   
 [Referencia de tareas](../msbuild/wpf-msbuild-task-reference.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Compilar una aplicación de WPF \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)   
 [Información general sobre las aplicaciones de explorador XAML de WPF](../Topic/WPF%20XAML%20Browser%20Applications%20Overview.md)