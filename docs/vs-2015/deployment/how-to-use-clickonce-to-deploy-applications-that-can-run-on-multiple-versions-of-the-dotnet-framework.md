---
title: Procedimiento Usar ClickOnce para implementar aplicaciones que se pueden ejecutar en varias versiones de .NET Framework | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 164fe64f360e41c06ef3f7bfd2d8091a6ebefecd
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65679944"
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>Procedimiento Usar ClickOnce para implementar aplicaciones que se pueden ejecutar en varias versiones de .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede implementar una aplicación que tenga como destino varias versiones de .NET Framework mediante el uso de la tecnología de implementación de ClickOnce. Esto requiere que generar y actualizar los manifiestos de aplicación e implementación.  
  
> [!NOTE]
> Antes de cambiar la aplicación en varias versiones de .NET Framework de destino, debe asegurarse de que se ejecuta la aplicación con varias versiones de .NET Framework. Common language runtime de versión es diferente entre [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] frente a .NET Framework 2.0, .NET Framework 3.0 y .NET Framework 3.5.  
  
 Este proceso requiere los siguientes pasos:  
  
1. Generar los manifiestos de aplicación e implementación.  
  
2. Cambiar el manifiesto de implementación para obtener una lista de las varias versiones de .NET Framework.  
  
3. Cambiar el archivo app.config para obtener una lista de versiones compatibles del runtime de .NET Framework.  
  
4. Cambiar el manifiesto de aplicación para marcar los ensamblados dependientes como ensamblados de .NET Framework.  
  
5. Inicie sesión en el manifiesto de aplicación.  
  
6. Actualizar y firmar el manifiesto de implementación.  
  
### <a name="to-generate-the-application-and-deployment-manifests"></a>Para generar los manifiestos de aplicación e implementación  
  
- Usar el Asistente para publicación o en la página Publicar del Diseñador de proyectos para publicar la aplicación y generar la aplicación y los archivos de manifiesto de implementación. Para obtener más información, vea [Cómo: Publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) o [publicar Page, Project Designer](../ide/reference/publish-page-project-designer.md).  
  
### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>Para cambiar el manifiesto de implementación para obtener una lista de las varias versiones de .NET Framework  
  
1. En el directorio de publicación, abra el manifiesto de implementación mediante el Editor XML en Visual Studio. El manifiesto de implementación tiene la extensión de nombre de archivo .application.  
  
2. Reemplace el código XML entre el `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` y `</compatibleFrameworks>` elementos con XML que se enumeran las versiones compatibles de .NET Framework para la aplicación.  
  
     En la tabla siguiente muestra algunas de las versiones de .NET Framework disponibles y el XML correspondiente que se puede agregar al manifiesto de implementación.  
  
    |Versión de .NET Framework|XML|  
    |----------------------------|---------|  
    |4, cliente|\<Framework targetVersion = "4.0" profile = supportedRuntime "Cliente" = "4.0.30319" / >|  
    |4, completa|\<Framework targetVersion = "4.0" profile = supportedRuntime "Full" = "4.0.30319" / >|  
    |3.5, cliente|\<Framework targetVersion = "3.5" profile = supportedRuntime "Cliente" = "2.0.50727" / >|  
    |3.5, completa|\<Framework targetVersion = "3.5" profile = supportedRuntime "Full" = "2.0.50727" / >|  
    |3.0|\<framework targetVersion="3.0" supportedRuntime="2.0.50727" />|  
  
### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>Para cambiar el archivo app.config para obtener una lista de versiones compatibles del runtime de .NET Framework  
  
1. En el Explorador de soluciones, abra el archivo App.config con el Editor de XML en Visual Studio.  
  
2. Reemplace el código XML entre (o agregue) el `<startup>` y `</startup>` elementos con XML que se enumeran los tiempos de ejecución de .NET Framework admitidos para la aplicación.  
  
     En la tabla siguiente muestra algunas de las versiones de .NET Framework disponibles y el XML correspondiente que se puede agregar al manifiesto de implementación.  
  
    |Versión del runtime de .NET framework|XML|  
    |------------------------------------|---------|  
    |4, cliente|\<supportedRuntime versión = "v4.0.30319" sku = ". NETFramework, Version = v4.0, perfil = Client "/ >|  
    |4, completa|\<supportedRuntime versión = "v4.0.30319" sku = ". NETFramework, Version = v4.0 "/ >|  
    |3.5, completa|\<version="v2.0.50727"/ supportedRuntime >|  
    |3.5, cliente|\<supportedRuntime versión = "v2.0.50727" sku = "Client" / >|  
  
### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>Para cambiar el manifiesto de aplicación para marcar los ensamblados dependientes como ensamblados de .NET Framework  
  
1. En el directorio de publicación, abra el manifiesto de aplicación mediante el Editor XML en Visual Studio. El manifiesto de implementación tiene la extensión de nombre de archivo de manifiesto.  
  
2. Agregar `group="framework"` para el XML de dependencia para los ensamblados de centinela (`System.Core`, `WindowsBase`, `Sentinel.v3.5Client`, y `System.Data.Entity`). Por ejemplo, el código XML debe ser similar al siguiente:  
  
    ```  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3. Actualizar el número de versión de la `<assemblyIdentity>` elemento para Microsoft.Windows.CommonLanguageRuntime al número de versión de .NET Framework que es el mínimo común denominador. Por ejemplo, si la aplicación tiene como destino .NET Framework 3.5 y [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)], use el 2.0.50727.0 número de versión y el código XML deben ser similar al siguiente:  
  
    ```  
    <dependency>  
      <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
        <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
      </dependentAssembly>  
    </dependency>  
    ```  
  
### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>Para actualizar y volver a firmar la aplicación y la implementación de manifiestos  
  
- Actualizar y volver a firmar los manifiestos de aplicación e implementación. Para obtener más información, vea [Cómo: Volver a firmar aplicaciones y manifiestos de implementación](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="see-also"></a>Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [\<compatibleFrameworks > elemento](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [\<dependencia > elemento](../deployment/dependency-element-clickonce-application.md)   
 [Manifiesto de implementación de ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Esquema de los archivos de configuración](https://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)
