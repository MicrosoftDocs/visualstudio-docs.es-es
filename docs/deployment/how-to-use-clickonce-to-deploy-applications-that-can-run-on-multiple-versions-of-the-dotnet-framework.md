---
title: "C&#243;mo: Usar ClickOnce para implementar aplicaciones que se pueden ejecutar en varias versiones de .NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "aplicaciones ClickOnce, varias versiones de .NET Framework"
  - "implementación ClickOnce, varias versiones de .NET Framework"
  - "implementar aplicaciones [ClickOnce], varias versiones de .NET Framework"
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# C&#243;mo: Usar ClickOnce para implementar aplicaciones que se pueden ejecutar en varias versiones de .NET Framework
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede implementar una aplicación destinada a varias versiones de .NET Framework gracias a la tecnología de implementación ClickOnce.  Para ello, es preciso generar y actualizar los manifiestos de implementación y aplicación.  
  
> [!NOTE]
>  Antes de cambiar la aplicación para destinarla a varias versiones de .NET Framework, debe asegurarse de que se ejecute con varias versiones de .NET Framework.  La versión de Common Language Runtime varía entre [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] y .NET Framework 2.0, .NET Framework 3.0 y .NET Framework 3.5.  
  
 Este proceso exige los pasos siguientes:  
  
1.  Generar los manifiestos de aplicación e implementación.  
  
2.  Cambiar el manifiesto de implementación de modo que incluya una lista de las diversas versiones de .NET Framework.  
  
3.  Cambiar el archivo app.config de modo que incluya una lista de versiones compatibles del runtime de .NET Framework.  
  
4.  Cambiar el manifiesto de aplicación a fin de marcar los ensamblados dependientes como ensamblados de .NET Framework.  
  
5.  Firmar el manifiesto de aplicación.  
  
6.  Actualizar y firmar el manifiesto de implementación.  
  
### Para generar los manifiestos de aplicación e implementación  
  
-   Utilice el Asistente para publicación o la página Publicar del Diseñador de proyectos para publicar la aplicación y generar los archivos de manifiesto de implementación y aplicación.  Para obtener más información, vea [Cómo: Publicar una aplicación ClickOnce sin usar el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) o [Panel Publicar, Diseñador de proyectos](../ide/reference/publish-page-project-designer.md).  
  
### Para cambiar el manifiesto de implementación de modo que incluya una lista de las diversas versiones de .NET Framework  
  
1.  En el directorio de publicación, abra el manifiesto de implementación mediante el Editor XML de Visual Studio.  El manifiesto de implementación tiene la extensión de nombre de archivo .application.  
  
2.  Reemplace el código XML que figura entre los elementos `</compatibleFrameworks>` y `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` por un XML con la lista de versiones de .NET Framework compatibles con su aplicación.  
  
     En la siguiente tabla se muestran algunas de las versiones de .NET Framework disponibles y el XML correspondiente que puede agregar al manifiesto de implementación.  
  
    |Versión de .NET Framework|XML|  
    |-------------------------------|---------|  
    |4 Client|\<framework targetVersion\="4.0" profile\="Client" supportedRuntime\="4.0.30319" \/\>|  
    |4 \(Versión completa\)|\<framework targetVersion\="4.0" profile\="Full" supportedRuntime\="4.0.30319" \/\>|  
    |3.5 Client|\<framework targetVersion\="3.5" profile\="Client" supportedRuntime\="2.0.50727" \/\>|  
    |3.5 \(Versión completa\)|\<framework targetVersion\="3.5" profile\="Full" supportedRuntime\="2.0.50727" \/\>|  
    |3.0|\<framework targetVersion\="3.0" supportedRuntime\="2.0.50727" \/\>|  
  
### Para cambiar el archivo app.config de modo que incluya una lista de versiones compatibles del runtime de .NET Framework  
  
1.  En el Explorador de soluciones, abra el archivo App.config mediante el Editor XML de Visual Studio.  
  
2.  Reemplace \(o agregue\) el código XML que figura entre los elementos `</startup>` y `<startup>` por un XML con la lista de runtimes de .NET Framework compatibles con su aplicación.  
  
     En la siguiente tabla se muestran algunas de las versiones de .NET Framework disponibles y el XML correspondiente que puede agregar al manifiesto de implementación.  
  
    |Versión de runtime de .NET Framework|XML|  
    |------------------------------------------|---------|  
    |4 Client|\<supportedRuntime version\="v4.0.30319" sku\=".NETFramework,Version\=v4.0,Profile\=Client" \/\>|  
    |4 \(Versión completa\)|\<supportedRuntime version\="v4.0.30319" sku\=".NETFramework,Version\=v4.0" \/\>|  
    |3.5 \(Versión completa\)|\<supportedRuntime version\="v2.0.50727"\/\>|  
    |3.5 Client|\<supportedRuntime version\="v2.0.50727" sku\="Client"\/\>|  
  
### Para cambiar el manifiesto de aplicación a fin de marcar los ensamblados dependientes como ensamblados de .NET Framework  
  
1.  En el directorio de publicación, abra el manifiesto de aplicación mediante el Editor XML de Visual Studio.  El manifiesto de implementación tiene la extensión de nombre de archivo .manifest.  
  
2.  Agregue `group="framework"` al XML de dependencia para los ensamblados de centinela \(`System.Core`, `WindowsBase`, `Sentinel.v3.5Client` y `System.Data.Entity`\).  Por ejemplo, el XML debe tener la apariencia siguiente:  
  
    ```  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3.  Actualice el número de versión del elemento `<assemblyIdentity>` para Microsoft.Windows.CommonLanguageRuntime con el número de versión de .NET Framework que sea el mínimo común denominador.  Por ejemplo, si la aplicación está destinada a .NET Framework 3.5 y [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)], utilice el número de versión 2.0.50727.0; el XML debería tener la apariencia siguiente:  
  
    ```  
    <dependency>  
      <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
        <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
      </dependentAssembly>  
    </dependency>  
    ```  
  
### Para actualizar y volver a firmar los manifiestos de aplicación e implementación  
  
-   Actualice y vuelva a firmar los manifiestos de aplicación e implementación.  Para obtener más información, vea [Cómo: Volver a firmar manifiestos de aplicación e implementación](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [\<compatibleFrameworks\> \(Elemento\)](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [Elemento \<dependency\>](../deployment/dependency-element-clickonce-application.md)   
 [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Esquema de los archivos de configuración](../Topic/Configuration%20File%20Schema%20for%20the%20.NET%20Framework.md)