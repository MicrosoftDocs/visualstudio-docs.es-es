---
title: "C&#243;mo: Especificar una direcci&#243;n URL de soporte para requisitos previos individuales en una implementaci&#243;n de ClickOnce | Microsoft Docs"
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
  - "implementación ClickOnce, requisitos previos"
  - "implementación ClickOnce, direcciones URL"
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# C&#243;mo: Especificar una direcci&#243;n URL de soporte para requisitos previos individuales en una implementaci&#243;n de ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Una implementación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] puede comprobar varios requisitos previos que deben estar disponibles en el equipo cliente para que se ejecute la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Entre ellos se encuentran la versión mínima necesaria de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], la versión del sistema operativo y los ensamblados que deben estar preinstalados en la memoria caché global de ensamblados \(GAC\).  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], sin embargo, no puede instalar estos requisitos previos; si no encuentra un requisito previo, simplemente detiene la instalación y muestra un cuadro de diálogo en el que se explica por qué se produjo un error en la instalación.  
  
 Hay dos métodos para instalar los requisitos previos.  Puede instalarlos mediante una aplicación de arranque.  Opcionalmente, puede especificar una dirección URL de soporte para los requisitos previos individuales, que se muestra a los usuarios en el cuadro de diálogo si no se encuentra el requisito previo.  La página a la que hace referencia esa dirección URL puede contener vínculos a las instrucciones para instalar el requisito previo necesario.  Si una aplicación no especifica una dirección URL de soporte para un requisito previo individual, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] muestra la dirección URL de soporte especificada en el manifiesto de implementación para la aplicación en conjunto si se ha definido.  
  
 Si bien [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], Mage.exe y MageUI.exe pueden utilizarse para generar implementaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], ninguna de estas herramientas admite directamente que se especifique una dirección URL de soporte para los requisitos previos individuales.  En este documento se describe cómo se modifica el manifiesto de aplicación y el manifiesto de implementación para incluir estas direcciones URL de soporte.  
  
### Especificar una dirección URL de soporte para un requisito previo individual  
  
1.  Abra el manifiesto de aplicación \(el archivo .manifest\) de la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] en un editor de texto.  
  
2.  Para un requisito previo del sistema operativo, agregue el atributo `supportUrl` al elemento `dependentOS`:  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3.  Para un requisito previo para una versión determinada de Common Language Runtime, agregue el atributo `supportUrl` a la entrada `dependentAssembly` que especifica la dependencia de Common Language Runtime:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4.  Para un requisito previo para un ensamblado que se debe preinstalar en la caché global de ensamblados, establezca `supportUrl` para el elemento `dependentAssembly` que especifica el ensamblado necesario:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5.  Opcional.  En las aplicaciones que tienen como destino .NET Framework 4, abra el manifiesto de implementación \(el archivo .application\) de la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] en un editor de texto.  
  
6.  Como requisito previo de .NET Framework 4, agregue el atributo `supportUrl` al elemento `compatibleFrameworks`:  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7.  Después de modificar manualmente el manifiesto de aplicación, deberá volver a firmarlo mediante su certificado digital; a continuación, deberá actualizarlo y firmar también el manifiesto de implementación.  Debe utilizar las herramientas del SDK Mage.exe o MageUI.exe para realizar esta tarea, ya que si vuelve a generar estos archivos mediante [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], se borrarán los cambios manuales.  Para obtener más información acerca de cómo se usa Mage.exe para volver a firmar los manifiestos, vea [Cómo: Volver a firmar manifiestos de aplicación e implementación](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## Seguridad de .NET Framework  
 La dirección URL de soporte no se muestra en el cuadro de diálogo si la aplicación se marca para ejecutarse en confianza parcial.  
  
## Vea también  
 [Mage.exe \(Herramienta de generación y edición de manifiestos\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks\> \(Elemento\)](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce y Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Requisitos previos para la implementación de aplicaciones](../deployment/application-deployment-prerequisites.md)