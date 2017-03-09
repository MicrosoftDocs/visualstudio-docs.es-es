---
title: "MarkupCompilePass1 (Tarea) | Microsoft Docs"
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
  - "convertir proyectos XAML a formato binario compilado [WPF MSBuild]"
  - "convertir proyectos XAML a formato binario [WPF MSBuild]"
  - "MarkupCompilePass1 (tarea) [WPF MSBuild], convertir XAML a formato binario"
  - "MarkupCompilePass1 (tarea) [WPF MSBuild], parámetros"
ms.assetid: 693d6945-fd6f-4698-8f64-9dfcb71052d3
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MarkupCompilePass1 (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La tarea <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> convierte archivos de proyecto [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] no adaptables al formato binario compilado.  
  
## Parámetros de la tarea  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`AllGeneratedFiles`|Parámetro de salida opcional de tipo **ITaskItem\[\]**.<br /><br /> Contiene la lista completa de archivos generados por la tarea <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>.|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|Parámetro opcional de tipo **Boolean**.<br /><br /> Especifica si la tarea debe ejecutarse en un <xref:System.AppDomain> independiente.  Si este parámetro devuelve el valor **false**, la tarea se ejecuta en el mismo <xref:System.AppDomain> que [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] y su ejecución es más rápida.  Si el parámetro devuelve el valor **true**, la tarea se ejecuta en otro <xref:System.AppDomain> que está aislado de [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] y su ejecución es más lenta.|  
|`ApplicationMarkup`|Parámetro opcional de tipo **ITaskItem\[\]**.<br /><br /> Especifica el nombre del archivo [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] de la definición de aplicación.|  
|`AssembliesGeneratedDuringBuild`|Parámetro opcional de tipo **String\[\]**.<br /><br /> Especifica referencias a los ensamblados que cambian durante el proceso de compilación.  Por ejemplo, una solución de [!INCLUDE[TLA#tla_visualstu2005](../msbuild/includes/tlasharptla_visualstu2005_md.md)] puede contener un proyecto que haga referencia al resultado compilado de otro proyecto.  En este caso, el resultado compilado del segundo proyecto se puede agregar al parámetro **AssembliesGeneratedDuringBuild**.<br /><br /> Nota: el parámetro **AssembliesGeneratedDuringBuild** debe contener referencias al conjunto completo de ensamblados que genera una solución de compilación.|  
|`AssemblyName`|Parámetro obligatorio de tipo **String**.<br /><br /> Especifica el nombre corto del ensamblado que se genera para un proyecto.  Por ejemplo, si un proyecto genera un archivo ejecutable de [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] con el nombre **WinExeAssembly.exe**, el parámetro **AssemblyName** tiene el valor **WinExeAssembly**.|  
|`AssemblyPublicKeyToken`|Parámetro opcional de tipo **String**.<br /><br /> Especifica el token de la clave pública del ensamblado.|  
|`AssemblyVersion`|Parámetro opcional de tipo **String**.<br /><br /> Especifica el número de versión del ensamblado.|  
|`ContentFiles`|Parámetro opcional de tipo **ITaskItem\[\]**.<br /><br /> Especifica la lista de archivos de contenido separados.|  
|`DefineConstants`|Parámetro opcional de tipo **String**.<br /><br /> Especifica que se mantiene el valor actual de **DefineConstants**,  lo que afecta a la generación del ensamblado de destino. Si se cambia este parámetro, puede que cambie la API pública del ensamblado de destino y se vea afectada la compilación de los archivos [!INCLUDE[TLA2#tla_titlexaml](../msbuild/includes/tla2sharptla_titlexaml_md.md)] que hacen referencia a tipos locales.|  
|`ExtraBuildControlFiles`|Parámetro opcional de tipo **ITaskItem\[\]**.<br /><br /> Especifica una lista de los archivos que controlan si se va a desencadenar una recompilación cuando se vuelva a ejecutar la tarea <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>; se desencadena una recompilación si cambia alguno de estos archivos.|  
|`GeneratedBamlFiles`|Parámetro de salida opcional de tipo **ITaskItem\[\]**.<br /><br /> Contiene la lista de archivos generados en formato binario [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].|  
|`GeneratedCodeFiles`|Parámetro de salida opcional de tipo **ITaskItem\[\]**.<br /><br /> Contiene la lista de los archivos de código administrado generados.|  
|`GeneratedLocalizationFiles`|Parámetro de salida opcional de tipo **ITaskItem\[\]**.<br /><br /> Contiene la lista de los archivos de localización que se generaron por cada archivo [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] adaptable.|  
|`HostInBrowser`|Parámetro opcional de tipo **String**.<br /><br /> Especifica si el ensamblado generado es una [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)].  Las opciones válidas son **true** y **false**.  Si es **true**, se genera código para admitir el hospedaje en el explorador.|  
|`KnownReferencePaths`|Parámetro opcional de tipo **String\[\]**.<br /><br /> Especifica referencias a los ensamblados que no cambian durante el proceso de compilación.  Incluye los ensamblados que se encuentran en la [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)], en un directorio de instalación de [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)], etc.|  
|`Language`|Parámetro obligatorio de tipo **String**.<br /><br /> Especifica el lenguaje administrado que el compilador admite.  las opciones válidas son **C\#**, **VB**, **JScript**, y **C\+\+**.|  
|`LanguageSourceExtension`|Parámetro opcional de tipo **String**.<br /><br /> Especifica la extensión que se anexa a la extensión del archivo de código administrado generado:<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> Si el valor del parámetro **LanguageSourceExtension** no se establece en un valor concreto, se utiliza la extensión de nombre de archivo de código fuente predeterminada de un lenguaje: **.vb** para [!INCLUDE[TLA#tla_visualb](../msbuild/includes/tlasharptla_visualb_md.md)], **.csharp** para [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)].|  
|`LocalizationDirectivesToLocFile`|Parámetro opcional de tipo **String**.<br /><br /> Especifica cómo generar la información de localización para cada archivo de código fuente [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].  Las opciones válidas son **None**, **CommentsOnly** y **All**.|  
|`OutputPath`|Parámetro obligatorio de tipo **String**.<br /><br /> Especifica el directorio en el que se generan los archivos de código administrado y los archivos de formato binario [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].|  
|`OutputType`|Parámetro obligatorio de tipo **String**.<br /><br /> Especifica el tipo de ensamblado que un proyecto genera.  Las opciones válidas son **winexe**, **exe**, **library** y **netmodule**.|  
|`PageMarkup`|Parámetro opcional de tipo **ITaskItem\[\]**.<br /><br /> Especifica una lista de los archivos [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] que se van a procesar.|  
|`References`|Parámetro opcional de tipo **ITaskItem\[\]**.<br /><br /> Especifica la lista de referencias de los archivos a los ensamblados que contienen los tipos que se usan en los archivos [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].|  
|`RequirePass2ForMainAssembly`|Parámetro de salida opcional de tipo **Boolean**.<br /><br /> Indica si el proyecto contiene archivos [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] no adaptables que hagan referencia a tipos locales incrustados en el ensamblado principal.|  
|`RequirePass2ForSatelliteAssembly`|Parámetro de salida opcional de tipo **Boolean**.<br /><br /> Indica si el proyecto contiene archivos [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] adaptables que hagan referencia a tipos locales incrustados en el ensamblado principal.|  
|`RootNamespace`|Parámetro opcional de tipo **String**.<br /><br /> Especifica el espacio de nombres de la raíz de las clases que están dentro del proyecto.  **RootNamespace** también se usa como espacio de nombres predeterminado de un archivo de código administrado generado cuando el archivo [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] correspondiente no incluye el atributo `x:Class`.|  
|`SourceCodeFiles`|Parámetro opcional de tipo **ITaskItem\[\]**.<br /><br /> Especifica la lista de archivos de código del proyecto actual.  La lista no incluye los archivos de código administrado específicos del lenguaje que se hayan generado.|  
|`UICulture`|Parámetro opcional de tipo **String**.<br /><br /> Especifica el ensamblado satélite de la referencia cultural de la interfaz de usuario en la que se incrustan los archivos de formato binario [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] generados.  Si no se establece el valor de **UICulture**, los archivos de formato binario [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] generados se incrustan en el ensamblado principal.|  
|`XAMLDebuggingInformation`|Parámetro opcional de tipo **Boolean**.<br /><br /> Si el valor es **true**, se genera información de diagnóstico y se incluye en el archivo [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] compilado como ayuda para la depuración.|  
  
## Comentarios  
 La tarea <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> normalmente compila [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] en formato binario y genera los archivos de código fuente.  Si un archivo [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] contiene referencias a tipos definidos en el mismo proyecto, **MarkupCompilePass1** aplaza su compilación en formato binario a un segundo paso de compilación de marcado \(**MarkupCompilePass2**\).  Estos archivos se deben compilar de forma aplazada porque deben esperar hasta que se compilen los tipos definidos localmente a los que se hace referencia.  Sin embargo, si un archivo [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] tiene un atributo `x:Class`, <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> genera el archivo de código específico del lenguaje.  
  
 Un archivo [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] es adaptable si contiene elementos que usan el atributo `x:Uid`:  
  
```  
<Page x:Class="WPFMSBuildSample.Page1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    x:Uid="Page1Uid"  
    >  
  ...  
</Page>  
```  
  
 Un archivo [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] hace referencia a un tipo definido localmente cuando declara un espacio de nombres [!INCLUDE[TLA#tla_xml](../msbuild/includes/tlasharptla_xml_md.md)] que use el valor `clr-namespace` para hacer referencia a un espacio de nombres del proyecto actual:  
  
```  
<Page x:Class="WPFMSBuildSample.Page1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:localNamespace="clr-namespace:WPFMSBuildSample"  
    >  
    <Grid>  
      <Grid.Resources>  
        <localNameSpace:LocalType x:Key="localType" />  
      </Grid.Resources>  
      ...  
    </Grid>  
</Page>  
```  
  
 Si un archivo [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] es localizable o hace referencia a un tipo definido localmente, se necesita un segundo paso de compilación de marcado, el cual requiere la ejecución de [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) y, a continuación, de [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).  
  
## Ejemplo  
 En el siguiente ejemplo se muestra cómo convertir tres archivos `Page` [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] en archivos de formato binario.  `Page1` contiene una referencia a un tipo, `Class1`, que está en el espacio de nombres de la raíz del proyecto y por consiguiente, no se convierte en archivo de formato binario en este paso la de compilación de marcado.  En su lugar, se ejecuta [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) y, después, [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass1"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MarkupCompilePass1Task">  
    <MarkupCompilePass1   
      AssemblyName="WPFMSBuildSample"  
      Language="C#"  
      OutputType="WinExe"  
      OutputPath="obj\Debug\"  
      ApplicationMarkup="App.xaml"  
      PageMarkup="Page1.xaml;Page2.xaml;Page3.xaml"  
      SourceCodeFiles="Class1.cs"  
      References="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />  
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