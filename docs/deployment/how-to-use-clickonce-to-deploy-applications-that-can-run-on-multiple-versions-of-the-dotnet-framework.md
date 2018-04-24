---
title: 'Cómo: usar ClickOnce para implementar aplicaciones que se pueden ejecutar en varias versiones de .NET Framework | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, multiple .NET Framework versions
- ClickOnce deployment, multiple .NET Framework versions
- deploying applications [ClickOnce], multiple .NET Framework versions
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c05d1317c2b8040baf23c98cff8a032f14f47798
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>Cómo: Usar ClickOnce para implementar aplicaciones que se pueden ejecutar en varias versiones de .NET Framework
Puede implementar una aplicación que tenga como destino varias versiones de .NET Framework mediante la tecnología de implementación de ClickOnce. Esto requiere que generar y actualizar los manifiestos de aplicación e implementación.  
  
> [!NOTE]
>  Antes de cambiar la aplicación para varias versiones de .NET Framework de destino, debe asegurarse de que la aplicación se ejecuta con varias versiones de .NET Framework. Common language runtime de versión es diferente entre [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] frente a .NET Framework 2.0, .NET Framework 3.0 y 3.5 de .NET Framework.  
  
 Este proceso requiere los pasos siguientes:  
  
1.  Generar los manifiestos de aplicación e implementación.  
  
2.  Cambiar el manifiesto de implementación para obtener una lista de varias versiones de .NET Framework.  
  
3.  Cambiar el archivo app.config para obtener una lista de las versiones compatibles del runtime de .NET Framework.  
  
4.  Cambiar el manifiesto de aplicación para marcar los ensamblados dependientes como ensamblados de .NET Framework.  
  
5.  Firme el manifiesto de aplicación.  
  
6.  Actualizar y firmar el manifiesto de implementación.  
  
### <a name="to-generate-the-application-and-deployment-manifests"></a>Para generar los manifiestos de aplicación e implementación  
  
-   Utilice el Asistente para publicación o en la página Publicar del Diseñador de proyectos para publicar la aplicación y generar los archivos de manifiesto de implementación y aplicación. Para obtener más información, consulte [Cómo: publicar una aplicación ClickOnce sin usar el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) o [Publish Page, Project Designer](../ide/reference/publish-page-project-designer.md).  
  
### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>Para cambiar el manifiesto de implementación para obtener una lista de varias versiones de .NET Framework  
  
1.  En el directorio de publicación, abra el manifiesto de implementación mediante el Editor de XML en Visual Studio. El manifiesto de implementación tiene la extensión de nombre de archivo Application.  
  
2.  Reemplace el código XML entre las `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` y `</compatibleFrameworks>` elementos con XML que enumera las versiones de .NET Framework compatibles para la aplicación.  
  
     En la tabla siguiente muestra algunas de las versiones de .NET Framework disponibles y el XML correspondiente que puede agregar al manifiesto de implementación.  
  
    |Versión de .NET Framework|XML|  
    |----------------------------|---------|  
    |Cliente 4|\<Framework targetVersion = "4.0" profile = supportedRuntime "Cliente" = "4.0.30319" / >|  
    |4 completo|\<Framework targetVersion = "4.0" profile = supportedRuntime "Completa" = "4.0.30319" / >|  
    |3.5 cliente de|\<Framework targetVersion = "3.5" profile = supportedRuntime "Cliente" = "2.0.50727" / >|  
    |3.5 completa|\<Framework targetVersion = "3.5" profile = supportedRuntime "Completa" = "2.0.50727" / >|  
    |3.0|\<Framework targetVersion = supportedRuntime "3.0" = "2.0.50727" / >|  
  
### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>Para cambiar el archivo app.config para obtener una lista de las versiones compatibles del runtime de .NET Framework  
  
1.  En el Explorador de soluciones, abra el archivo App.config con el Editor de XML en Visual Studio.  
  
2.  Reemplace (o agregue) el código XML entre las `<startup>` y `</startup>` elementos con XML que enumera los tiempos de ejecución de .NET Framework admitidos para la aplicación.  
  
     En la tabla siguiente muestra algunas de las versiones de .NET Framework disponibles y el XML correspondiente que puede agregar al manifiesto de implementación.  
  
    |Versión de runtime de .NET framework|XML|  
    |------------------------------------|---------|  
    |Cliente 4|\<versión de supportedRuntime = sku de "v4.0.30319" = ". NETFramework, Version = v4.0, perfil de cliente de = "/ >|  
    |4 completo|\<versión de supportedRuntime = sku de "v4.0.30319" = ". NETFramework, Version = v4.0 "/ >|  
    |3.5 completa|\<version="v2.0.50727"/ supportedRuntime >|  
    |3.5 cliente de|\<versión de supportedRuntime = "v2.0.50727" sku = "Cliente" / >|  
  
### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>Para cambiar el manifiesto de aplicación para marcar los ensamblados dependientes como ensamblados de .NET Framework  
  
1.  En el directorio de publicación, abra el manifiesto de aplicación mediante el Editor de XML en Visual Studio. El manifiesto de implementación tiene la extensión de nombre de archivo manifest.  
  
2.  Agregar `group="framework"` a la dependencia XML para los ensamblados de centinela (`System.Core`, `WindowsBase`, `Sentinel.v3.5Client`, y `System.Data.Entity`). Por ejemplo, el código XML debe ser similar al siguiente:  
  
    ```  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3.  Actualizar el número de versión de la `<assemblyIdentity>` elemento para Microsoft.Windows.CommonLanguageRuntime en el número de versión de .NET Framework que es el denominador común. Por ejemplo, si la aplicación tiene como destino .NET Framework 3.5 y [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)], use el 2.0.50727.0 número de versión y el código XML deben ser similar al siguiente:  
  
    ```  
    <dependency>  
      <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
        <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
      </dependentAssembly>  
    </dependency>  
    ```  
  
### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>Para actualizar y volver a firmar la aplicación y la implementación de manifiestos  
  
-   Actualizar y volver a firmar los manifiestos de aplicación e implementación. Para obtener más información, consulta [Cómo: Volver a firmar manifiestos de aplicación e implementación](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="see-also"></a>Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [\<compatibleFrameworks > elemento](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [\<dependencia > elemento](../deployment/dependency-element-clickonce-application.md)   
 [Manifiesto de implementación de ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Esquema de los archivos de configuración](/dotnet/framework/configure-apps/file-schema/index)