---
title: 'Cómo: especificar una dirección URL de soporte para requisitos previos individuales en una implementación de ClickOnce | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02dfd64d7a6b3a2ffae49e5693bdac8ebdf2ad0f
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815654"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Cómo: Especificar una dirección URL de soporte para requisitos previos individuales en una implementación de ClickOnce
A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] puede probar la implementación de una serie de requisitos previos que deben estar disponibles en el equipo cliente para la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación se ejecute. Estas dependencias incluyen la versión mínima necesaria de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], la versión del sistema operativo y los ensamblados que deben estar preinstalados en la caché global de ensamblados (GAC). [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], sin embargo, no se puede instalar cualquiera de estos requisitos previos sí; Si no se encuentra un requisito previo, simplemente detiene la instalación y muestra un cuadro de diálogo que explica por qué falló la instalación.  
  
 Hay dos métodos para instalar los requisitos previos. Puede instalarlos mediante una aplicación de programa previo. Como alternativa, puede especificar una dirección URL de soporte para requisitos previos individuales, que se muestra a los usuarios en el cuadro de diálogo si no se encuentra el requisito previo. La página al que hace referencia esa dirección URL puede contener vínculos a las instrucciones para instalar el requisito previo de software. Si una aplicación no especifica una dirección URL de soporte para un requisito previo individual, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] muestra la dirección URL de soporte técnico especificada en el manifiesto de implementación para la aplicación como un todo, si se ha definido.  
  
 Mientras [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], Mage.exe y MageUI.exe pueden utilizar para generar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las implementaciones, ninguna de estas herramientas directamente admite la especificación de una dirección URL de soporte para requisitos previos individuales. Este documento describe cómo modificar la implementación manifiesto de aplicación y el manifiesto de implementación para incluir estas direcciones URL de soporte.  
  
### <a name="specifying-a-support-url-for-an-individual-prerequisite"></a>Especificar una dirección URL de soporte para un requisito previo individual  
  
1.  Abra el manifiesto de aplicación (el `.manifest` archivo) para su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación en un editor de texto.  
  
2.  Para un requisito previo de sistema operativo, agregue el `supportUrl` atribuir a la `dependentOS` elemento:  
  
    ```xml  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3.  Para un requisito previo para una determinada versión de common language runtime, agregue el `supportUrl` atribuir a la `dependentAssembly` entrada que especifica la dependencia de tiempo de ejecución de lenguaje común:  
  
    ```xml  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4.  Para un requisito previo para un ensamblado que debe estar preinstalado en la caché global de ensamblados, establezca la `supportUrl` para el `dependentAssembly` elemento que especifica el ensamblado necesario:  
  
    ```xml  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5.  Opcional. Para las aplicaciones que tienen como destino .NET Framework 4, abra el manifiesto de implementación (el `.application` archivo) para su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación en un editor de texto.  
  
6.  Para un requisito previo de .NET Framework 4, agregue la `supportUrl` atribuir a la `compatibleFrameworks` elemento:  
  
    ```xml  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7.  Una vez que se ha modificado manualmente el manifiesto de aplicación, debe volver a firmar el manifiesto de aplicación con el certificado digital, a continuación, actualizar y volver a firmar el manifiesto de implementación también. Usar las herramientas del SDK Mage.exe o MageUI.exe para realizar esta tarea, como volver a generar estos archivos con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] borra los cambios realizados manualmente. Para obtener más información sobre cómo utilizar Mage.exe para volver a firmar manifiestos, consulte [Cómo: volver a firmar aplicaciones y manifiestos de implementación](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="net-framework-security"></a>Seguridad de .NET Framework  
 La dirección URL de soporte no se muestra en el cuadro de diálogo si la aplicación está marcada para ejecutarse en confianza parcial.  
  
## <a name="see-also"></a>Vea también  
 [Mage.exe (Herramienta de generación y edición de manifiestos)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks > elemento](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce y Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Requisitos previos para la implementación de aplicaciones](../deployment/application-deployment-prerequisites.md)