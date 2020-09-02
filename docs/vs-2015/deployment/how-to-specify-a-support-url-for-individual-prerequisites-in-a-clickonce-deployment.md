---
title: 'Cómo: especificar una dirección URL de soporte para requisitos previos individuales en una implementación ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1907b619bcc616c73d9b9e37af30722c02bf100e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65679974"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Cómo: Especificar una dirección URL de soporte para requisitos previos individuales en una implementación de ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implementación puede probar una serie de requisitos previos que deben estar disponibles en el equipo cliente para que la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación se ejecute. Entre ellas se incluye la versión mínima necesaria de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , la versión del sistema operativo y los ensamblados que deben preinstalarse en la caché de ensamblados global (GAC). [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]sin embargo, no puede instalar ninguno de estos requisitos previos. Si no se encuentra un requisito previo, simplemente detiene la instalación y muestra un cuadro de diálogo que explica por qué se produjo un error en la instalación.  
  
 Existen dos métodos para instalar los requisitos previos. Puede instalarlos con una aplicación de programa previo. También puede especificar una dirección URL de soporte técnico para los requisitos previos individuales, que se muestra a los usuarios en el cuadro de diálogo si no se encuentra el requisito previo. La página a la que se hace referencia en esa dirección URL puede contener vínculos a instrucciones para instalar el requisito previo necesario. Si una aplicación no especifica una dirección URL de soporte técnico para un requisito previo individual, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] muestra la dirección URL de soporte especificada en el manifiesto de implementación para la aplicación en su conjunto, si se ha definido.  
  
 Aunque [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se pueden usar Mage.exe y MageUI.exe para generar [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implementaciones, ninguna de estas herramientas admite directamente la especificación de una dirección URL de soporte técnico para los requisitos previos individuales. En este documento se describe cómo modificar el manifiesto de aplicación de la implementación y el manifiesto de implementación para incluir estas direcciones URL de soporte técnico.  
  
### <a name="specifying-a-support-url-for-an-individual-prerequisite"></a>Especificación de una dirección URL de soporte técnico para un requisito previo individual  
  
1. Abra el manifiesto de aplicación (el archivo. manifest) de la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación en un editor de texto.  
  
2. Para un requisito previo del sistema operativo, agregue el `supportUrl` atributo al `dependentOS` elemento:  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3. Para un requisito previo para una versión determinada del Common Language Runtime, agregue el `supportUrl` atributo a la `dependentAssembly` entrada que especifica la dependencia de Common Language Runtime:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4. Para un requisito previo de un ensamblado que debe preinstalarse en la caché global de ensamblados, establezca `supportUrl` para el `dependentAssembly` elemento que especifica el ensamblado necesario:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5. Opcional. En el caso de las aplicaciones que tienen como destino el .NET Framework 4, abra el manifiesto de implementación (el archivo. Application) de la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación en un editor de texto.  
  
6. Para obtener un requisito previo de .NET Framework 4, agregue el `supportUrl` atributo al `compatibleFrameworks` elemento:  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7. Una vez que haya modificado manualmente el manifiesto de aplicación, debe volver a firmar el manifiesto de aplicación con el certificado digital y, a continuación, actualizar y volver a firmar también el manifiesto de implementación. Debe usar las herramientas del SDK de Mage.exe o MageUI.exe para realizar esta tarea, ya que la regeneración de estos archivos con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] borra los cambios manuales. Para obtener más información sobre el uso de Mage.exe para volver a firmar los manifiestos, consulte [Cómo: Volver a firmar manifiestos de aplicación e implementación](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="net-framework-security"></a>Seguridad de .NET Framework  
 La dirección URL de soporte no se muestra en el cuadro de diálogo si la aplicación está marcada para ejecutarse en confianza parcial.  
  
## <a name="see-also"></a>Consulte también  
 [Mage.exe (Herramienta de generación y edición de manifiestos)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks> Element](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce y Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Requisitos previos de la implementación de aplicaciones](../deployment/application-deployment-prerequisites.md)
