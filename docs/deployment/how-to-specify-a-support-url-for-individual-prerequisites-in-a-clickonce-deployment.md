---
title: Dirección URL de soporte técnico para los requisitos previos de implementación de ClickOnce
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78ba7398694e097f324695b6357abc0b35f8d3ee
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66745567"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Procedimiento Especificación de una dirección URL de soporte para requisitos previos individuales en una implementación ClickOnce
Un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] puede probar la implementación de una serie de requisitos previos que deben estar disponibles en el equipo cliente para el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación se ejecute. Estas dependencias incluyen la versión mínima necesaria de .NET Framework, la versión del sistema operativo y los ensamblados que deben estar preinstalados en la caché global de ensamblados (GAC). [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], sin embargo, no se puede instalar cualquiera de estos requisitos previos. Si no se encuentra un requisito previo, simplemente detiene la instalación y muestra un cuadro de diálogo que explica el motivo del error de la instalación.

 Hay dos métodos para instalar los requisitos previos. Puede instalarlos mediante una aplicación de programa previo. Como alternativa, puede especificar una dirección URL de soporte para requisitos previos individuales, que se muestra a los usuarios en el cuadro de diálogo si no se encuentra el requisito previo. La página hace referencia a esa dirección URL puede contener vínculos a instrucciones para instalar el requisito previo necesario. Si una aplicación no especifica una dirección URL de soporte para un requisito previo individual, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] muestra la dirección URL de soporte técnico especificada en el manifiesto de implementación para la aplicación como un todo, si está definido.

 Mientras [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], *Mage.exe*, y *MageUI.exe* puede usarse para generar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las implementaciones, ninguna de estas herramientas directamente admite la especificación de una dirección URL de soporte de cliente individual requisitos previos. Este documento describe cómo modificar la implementación manifiesto de aplicación y manifiesto de implementación para incluir estas direcciones URL de soporte.

### <a name="specify-a-support-url-for-an-individual-prerequisite"></a>Especifique una dirección URL de soporte técnico para un requisito previo individual

1. Abra el manifiesto de aplicación (el *.manifest* archivo) para el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación en un editor de texto.

2. Para un requisito previo del sistema operativo, agregue el `supportUrl` atributo a la `dependentOS` elemento:

   ```xml
    <dependency>
       <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">
         <osVersionInfo>
           <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />
         </osVersionInfo>
       </dependentOS>
     </dependency>
   ```

3. Para un requisito previo para una determinada versión de common language runtime, agregue el `supportUrl` atributo a la `dependentAssembly` entrada que especifica la dependencia de tiempo de ejecución de lenguaje común:

   ```xml
     <dependency>
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">
         <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />
       </dependentAssembly>
     </dependency>
   ```

4. Para un requisito previo para un ensamblado que debe estar preinstalado en la caché global de ensamblados, establezca el `supportUrl` para el `dependentAssembly` elemento que especifica el ensamblado necesario:

   ```xml
     <dependency>
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">
         <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />
       </dependentAssembly>
     </dependency>
   ```

5. Opcional. Para las aplicaciones que tienen como destino .NET Framework 4, abra el manifiesto de implementación (el *.application* archivo) para el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación en un editor de texto.

6. Para un requisito previo de .NET Framework 4, agregue el `supportUrl` atributo a la `compatibleFrameworks` elemento:

   ```xml
   <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">
     <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />
     <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />
   </compatibleFrameworks>
   ```

7. Una vez que se ha modificado manualmente el manifiesto de aplicación, debe volver a firmar el manifiesto de aplicación mediante su certificado digital, a continuación, actualizar y volver a firmar el manifiesto de implementación también. Use la *Mage.exe* o *MageUI.exe* herramientas del SDK para realizar esta tarea, como volver a generar estos archivos mediante [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] borra los cambios manuales. Para obtener más información sobre el uso de Mage.exe para volver a firmar los manifiestos, consulte [Cómo: Volver a firmar aplicaciones y manifiestos de implementación](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="net-framework-security"></a>seguridad en .NET Framework
 La dirección URL de soporte técnico no se muestra en el cuadro de diálogo si la aplicación está marcada para ejecutarse en confianza parcial.

## <a name="see-also"></a>Vea también
- [Mage.exe (Herramienta de generación y edición de manifiestos)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [\<compatibleFrameworks > elemento](../deployment/compatibleframeworks-element-clickonce-deployment.md)
- [ClickOnce y Authenticode](../deployment/clickonce-and-authenticode.md)
- [Requisitos previos para la implementación de aplicaciones](../deployment/application-deployment-prerequisites.md)