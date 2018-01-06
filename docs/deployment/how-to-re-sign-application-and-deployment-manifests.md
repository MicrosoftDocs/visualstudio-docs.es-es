---
title: "Cómo: volver a firmar manifiestos de implementación y aplicación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Office applications, signing manifests
- deploying applications [ClickOnce], signing manifests
- deploying applications, signing manifests
- ClickOnce deployment, signing manifests
- Office development in Visual Studio, signing manifests
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
caps.latest.revision: "17"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: e3c6551269df19c554dfa50409108bf952c4b326
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Cómo: Volver a firmar manifiestos de aplicación e implementación
Después de realizar cambios a las propiedades de implementación en el manifiesto de aplicación para aplicaciones de Windows Forms, aplicaciones de Windows Presentation Foundation (xbap) o las soluciones de Office, debe volver a firmar la aplicación y los manifiestos de implementación con un certificado. Este proceso ayuda a garantizar que no se instalen archivos alterados en los equipos de usuario final.  
  
 Otro escenario donde se podrían volver a firmar los manifiestos es cuando los clientes desean firmar la aplicación y los manifiestos de implementación con su propio certificado.  
  
## <a name="re-signing-the-application-and-deployment-manifests"></a>Manifiestos de volver a firmar la aplicación e implementación  
 Este procedimiento se da por supuesto que ya ha realizado cambios en el archivo de manifiesto de aplicación (.manifest). Para obtener más información, consulte [Cómo: cambiar propiedades de implementación](http://msdn.microsoft.com/en-us/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Para volver a firmar la aplicación y la implementación de los manifiestos con Mage.exe  
  
1.  Abra un **Visual Studio Command Prompt** ventana.  
  
2.  Cambie los directorios a la carpeta que contiene los archivos de manifiesto que desea iniciar sesión.  
  
3.  Escriba el comando siguiente para firmar el archivo de manifiesto de aplicación. Reemplace ManifestFileName con el nombre de su archivo de manifiesto más la extensión. Reemplace el certificado con la ruta de acceso completa o relativa al archivo de certificado y contraseña con la contraseña para el certificado.  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Por ejemplo, podría ejecutar el comando siguiente para firmar un manifiesto de aplicación para un complemento, una aplicación de formularios Windows Forms o una aplicación de explorador de Windows Presentation Foundation. Certificados temporales creados por Visual Studio no se recomiendan para la implementación en entornos de producción.  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4.  Escriba el siguiente comando para actualizar y firmar el archivo de manifiesto de implementación, reemplazando los nombres de marcador de posición como en el paso anterior.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Por ejemplo, podría ejecutar el comando siguiente para actualizar y firmar un manifiesto de implementación para un complemento de Excel, una aplicación de formularios Windows Forms o una aplicación de explorador de Windows Presentation Foundation.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Si lo desea, copie el manifiesto de implementación principal (publicar\\*appname*Application) en el directorio de implementación de la versión (publish\Application archivos\\*appname*_ *versión*).  
  
## <a name="updating-and-re-signing-the-application-and-deployment-manifests"></a>Actualizar y volver a firmar la aplicación y los manifiestos de implementación  
 Este procedimiento se supone que ya ha realizado que cambios en la aplicación (.manifest) del archivo de manifiesto, pero que no hay otros archivos que se actualizaron. Cuando se actualizan los archivos, también debe actualizarse el valor hash que representa el archivo.  
  
#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Para actualizar y volver a firmar la aplicación y la implementación de los manifiestos con Mage.exe  
  
1.  Abra un **Visual Studio Command Prompt** ventana.  
  
2.  Cambie los directorios a la carpeta que contiene los archivos de manifiesto que desea iniciar sesión.  
  
3.  Quite la extensión de archivo ".deploy" de los archivos en la carpeta de salida de publicación.  
  
4.  Escriba el siguiente comando para actualizar el manifiesto de aplicación con el nuevo hash para los archivos actualizados y firmar el archivo de manifiesto de aplicación. Reemplace ManifestFileName con el nombre de su archivo de manifiesto más la extensión. Reemplace el certificado con la ruta de acceso completa o relativa al archivo de certificado y contraseña con la contraseña para el certificado.  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Por ejemplo, podría ejecutar el comando siguiente para firmar un manifiesto de aplicación para un complemento, una aplicación de formularios Windows Forms o una aplicación de explorador de Windows Presentation Foundation. Certificados temporales creados por Visual Studio no se recomiendan para la implementación en entornos de producción.  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Escriba el siguiente comando para actualizar y firmar el archivo de manifiesto de implementación, reemplazando los nombres de marcador de posición como en el paso anterior.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Por ejemplo, podría ejecutar el comando siguiente para actualizar y firmar un manifiesto de implementación para un complemento de Excel, una aplicación de formularios Windows Forms o una aplicación de explorador de Windows Presentation Foundation.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6.  Agregar la extensión de archivo .deploy a los archivos, excepto los archivos de manifiesto de la aplicación y la implementación.  
  
7.  Si lo desea, copie el manifiesto de implementación principal (publicar\\*appname*Application) en el directorio de implementación de la versión (publish\Application archivos\\*appname*_ *versión*).  
  
## <a name="see-also"></a>Vea también  
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce y Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Introducción a la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md)   
 [Cómo: Habilitar la configuración de seguridad de ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Cómo: Establecer una zona de seguridad para una aplicación ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Cómo: Establecer permisos personalizados para una aplicación ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Cómo: Depurar una aplicación ClickOnce con permisos restringidos](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Cómo: agregar un publicador de confianza a un equipo cliente para aplicaciones ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Cómo: Configurar el comportamiento del mensaje relativo a la confianza de ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)