---
title: "C&#243;mo: Volver a firmar manifiestos de aplicaci&#243;n e implementaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "implementación ClickOnce, firmar manifiestos"
  - "implementar aplicaciones [ClickOnce], firmar manifiestos"
  - "implementar aplicaciones, firmar manifiestos"
  - "aplicaciones de Office, firmar manifiestos"
  - "desarrollo de Office en Visual Studio, firmar manifiestos"
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# C&#243;mo: Volver a firmar manifiestos de aplicaci&#243;n e implementaci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Después de realizar cambios en las propiedades de implementación del manifiesto de aplicación para las aplicaciones de Windows Forms y Windows Presentation Foundation \(xbap\) o las soluciones de Office, debe volver a firmar los manifiestos de aplicación e implementación con un certificado.  Este proceso ayuda a garantizar que no se instalen archivos alterados en los equipos de los usuarios finales.  
  
 Otro escenario donde se deberían volver a firmar los manifiestos es cuando los clientes desean firmar los manifiestos de aplicación e implementación con su propio certificado.  
  
## Volver a firmar los manifiestos de implementación y aplicación  
 En este procedimiento se supone que ya ha realizado los cambios en el archivo de manifiesto de la aplicación \(.manifest\).  Para obtener más información, vea [Cómo: Cambiar propiedades de implementación](http://msdn.microsoft.com/es-es/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### Para volver a firmar los manifiestos de implementación y aplicación con Mage.exe  
  
1.  Abra una ventana **Símbolo del sistema de Visual Studio**.  
  
2.  Cambie los directorios a la carpeta que contiene los archivos de manifiesto que desea firmar.  
  
3.  Escriba el comando siguiente para firmar el archivo de manifiesto de aplicación.  Reemplace ManifestFileName con el nombre del archivo de manifiesto más la extensión.  Reemplace Certificate por la ruta de acceso relativa o completa del archivo de certificado y reemplace Password por la contraseña para el certificado.  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Por ejemplo, podría ejecutar el comando siguiente para firmar un manifiesto de aplicación para un complemento, una aplicación de Windows Forms o una aplicación Explorador de Windows Presentation Foundation.  No se recomienda el uso de certificados temporales creados por Visual Studio para la implementación en entornos de producción.  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4.  Escriba el comando siguiente para actualizar y firmar el archivo de manifiesto de implementación y reemplace los nombres de los marcadores de posición como en el paso anterior.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Por ejemplo, podría ejecutar el comando siguiente para actualizar y firmar un manifiesto de implementación de un complemento de Excel, una aplicación de Windows Forms o una aplicación de explorador de Windows Presentation Foundation.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  De manera opcional, copie el manifiesto de implementación principal \(publish\\*appname*.application\) en el directorio de implementación de la versión \(publish\\Application Files\\*appname*\_*versión*\).  
  
## Actualizar y volver a firmar los manifiestos de implementación y aplicación  
 En este procedimiento, se supone que ya ha realizado los cambios en el archivo del manifiesto de aplicación \(.manifest\), pero que hay otros archivos que se han actualizado.  Durante la actualización de los archivos, también se ha de actualizar el hash que representa el archivo.  
  
#### Para actualizar y volver a firmar los manifiestos de implementación y aplicación con Mage.exe  
  
1.  Abra una ventana **Símbolo del sistema de Visual Studio**.  
  
2.  Cambie los directorios a la carpeta que contiene los archivos de manifiesto que desea firmar.  
  
3.  Quite la extensión .deploy de los archivos en la carpeta de salida de publicación.  
  
4.  Escriba el siguiente comando para actualizar el manifiesto de aplicación con el nuevo hash para los archivos actualizados y firmar el archivo del manifiesto de aplicación.  Reemplace ManifestFileName con el nombre del archivo de manifiesto más la extensión.  Reemplace Certificate por la ruta de acceso relativa o completa del archivo de certificado y reemplace Password por la contraseña para el certificado.  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Por ejemplo, podría ejecutar el comando siguiente para firmar un manifiesto de aplicación para un complemento, una aplicación de Windows Forms o una aplicación Explorador de Windows Presentation Foundation.  No se recomienda el uso de certificados temporales creados por Visual Studio para la implementación en entornos de producción.  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Escriba el comando siguiente para actualizar y firmar el archivo de manifiesto de implementación y reemplace los nombres de los marcadores de posición como en el paso anterior.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Por ejemplo, podría ejecutar el comando siguiente para actualizar y firmar un manifiesto de implementación de un complemento de Excel, una aplicación de Windows Forms o una aplicación de explorador de Windows Presentation Foundation.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6.  Vuelva a agregar la extensión .deploy a los archivos, excepto a los archivos del manifiesto de implementación y del manifiesto de aplicación.  
  
7.  De manera opcional, copie el manifiesto de implementación principal \(publish\\*appname*.application\) en el directorio de implementación de la versión \(publish\\Application Files\\*appname*\_*versión*\).  
  
## Vea también  
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce y Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Información general sobre la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md)   
 [Cómo: Habilitar la configuración de seguridad para aplicaciones ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Cómo: Establecer una zona de seguridad para una aplicación ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Cómo: Establecer permisos personalizados para una aplicación ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Cómo: Depurar una aplicación ClickOnce con permisos restringidos](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Cómo: Agregar un publicador de confianza a un equipo cliente para aplicaciones ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Cómo: Configurar el comportamiento del mensaje relativo a la confianza de ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)