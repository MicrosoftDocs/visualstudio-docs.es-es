---
title: 'Cómo: usar ClickOnce para implementar aplicaciones que se pueden ejecutar en varias versiones del .NET Framework | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65679944"
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>Cómo: Usar ClickOnce para implementar aplicaciones que se pueden ejecutar en varias versiones de .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede implementar una aplicación destinada a varias versiones del .NET Framework mediante la tecnología de implementación ClickOnce. Esto requiere que se generen y actualicen los manifiestos de aplicación y de implementación.  
  
> [!NOTE]
> Antes de cambiar la aplicación para que tenga como destino varias versiones del .NET Framework, debe asegurarse de que la aplicación se ejecuta con varias versiones de la .NET Framework. La versión Common Language Runtime es diferente en [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] comparación con .NET Framework 2,0, .NET Framework 3,0 y .NET Framework 3,5.  
  
 Este proceso requiere los siguientes pasos:  
  
1. Generar los manifiestos de aplicación y de implementación.  
  
2. Cambie el manifiesto de implementación para enumerar las versiones de .NET Framework múltiples.  
  
3. Cambie el archivo de app.config para mostrar las versiones compatibles del tiempo de ejecución de .NET Framework.  
  
4. Cambie el manifiesto de aplicación para marcar los ensamblados dependientes como ensamblados de .NET Framework.  
  
5. Firme el manifiesto de aplicación.  
  
6. Actualice y firme el manifiesto de implementación.  
  
### <a name="to-generate-the-application-and-deployment-manifests"></a>Para generar los manifiestos de aplicación e implementación  
  
- Use el Asistente para publicación o la página publicar del diseñador de proyectos para publicar la aplicación y generar los archivos de manifiesto de aplicación y de implementación. Para obtener más información, vea [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación o la](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) [Página publicar, diseñador de proyectos](../ide/reference/publish-page-project-designer.md).  
  
### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>Para cambiar el manifiesto de implementación para mostrar las distintas versiones de .NET Framework  
  
1. En el directorio de publicación, abra el manifiesto de implementación con el editor XML de Visual Studio. El manifiesto de implementación tiene la extensión de nombre de archivo. Application.  
  
2. Reemplace el código XML entre los `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` `</compatibleFrameworks>` elementos y con XML que enumera las versiones de .NET Framework admitidas para la aplicación.  
  
     En la tabla siguiente se muestran algunas de las versiones de .NET Framework disponibles y el XML correspondiente que se puede Agregar al manifiesto de implementación.  
  
    |Versión de .NET Framework|XML|  
    |----------------------------|---------|  
    |4, cliente|\<framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />|  
    |4, completa|\<framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />|  
    |3.5, cliente|\<framework targetVersion="3.5" profile="Client" supportedRuntime="2.0.50727" />|  
    |3.5, completa|\<framework targetVersion="3.5" profile="Full" supportedRuntime="2.0.50727" />|  
    |3.0|\<framework targetVersion="3.0" supportedRuntime="2.0.50727" />|  
  
### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>Para cambiar el archivo de app.config para mostrar las versiones compatibles de .NET Framework runtime  
  
1. En Explorador de soluciones, abra el archivo de App.config con el editor XML de Visual Studio.  
  
2. Reemplace (o agregue) el código XML entre los `<startup>` `</startup>` elementos y con XML que enumera los Runtimes de .NET Framework admitidos para la aplicación.  
  
     En la tabla siguiente se muestran algunas de las versiones de .NET Framework disponibles y el XML correspondiente que se puede Agregar al manifiesto de implementación.  
  
    |Versión del tiempo de ejecución de .NET Framework|XML|  
    |------------------------------------|---------|  
    |4, cliente|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0,Profile=Client" />|  
    |4, completa|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0" />|  
    |3.5, completa|\<supportedRuntime version="v2.0.50727"/>|  
    |3.5, cliente|\<supportedRuntime version="v2.0.50727" sku="Client"/>|  
  
### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>Para cambiar el manifiesto de aplicación para marcar los ensamblados dependientes como ensamblados de .NET Framework  
  
1. En el directorio de publicación, abra el manifiesto de aplicación mediante el editor XML de Visual Studio. El manifiesto de implementación tiene la extensión de nombre de archivo. manifest.  
  
2. Agregue `group="framework"` al XML de dependencia para los ensamblados de Centinela ( `System.Core` , `WindowsBase` , `Sentinel.v3.5Client` y `System.Data.Entity` ). Por ejemplo, el código XML debe ser similar al siguiente:  
  
    ```  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3. Actualice el número de versión del `<assemblyIdentity>` elemento de Microsoft. Windows. CommonLanguageRuntime con el número de versión del .NET Framework que sea el denominador común más bajo. Por ejemplo, si la aplicación tiene como destino .NET Framework 3,5 y [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] , use el número de versión de 2.0.50727.0 y el código XML debería ser similar al siguiente:  
  
    ```  
    <dependency>  
      <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
        <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
      </dependentAssembly>  
    </dependency>  
    ```  
  
### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>Para actualizar y volver a firmar los manifiestos de aplicación e implementación  
  
- Actualice y vuelva a firmar la aplicación y los manifiestos de implementación. Para obtener más información, consulta [How to: Re-sign Application and Deployment Manifests](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="see-also"></a>Consulte también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [\<compatibleFrameworks> Element](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [\<dependency> Element](../deployment/dependency-element-clickonce-application.md)   
 [Manifiesto de implementación de ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Esquema de los archivos de configuración](https://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)
