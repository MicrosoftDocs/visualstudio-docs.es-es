---
title: 'Cómo: volver a firmar aplicaciones y manifiestos de implementación | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
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
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 734258871e72e6272abcd61c4efa1a00765f8a32
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49185723"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Cómo: Volver a firmar manifiestos de aplicación e implementación
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Después de realizar cambios en las propiedades de implementación en el manifiesto de aplicación para aplicaciones de Windows Forms, aplicaciones de Windows Presentation Foundation (xbap) o las soluciones de Office, debe volver a firmar la aplicación y los manifiestos de implementación con un certificado. Este proceso ayuda a garantizar que no se instalen archivos alterados en los equipos de usuario final.  
  
 Otro escenario donde se podrían volver a firmar los manifiestos es cuando los clientes desean firmar la aplicación y los manifiestos de implementación con su propio certificado.  
  
## <a name="re-signing-the-application-and-deployment-manifests"></a>Volver a firmar la aplicación y la implementación de manifiestos  
 Este procedimiento se supone que ya ha realizado cambios en el archivo de manifiesto de aplicación (.manifest). Para obtener más información, consulte [Cómo: cambiar las propiedades de implementación](http://msdn.microsoft.com/en-us/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Para volver a firmar la aplicación e implementación de manifiestos con Mage.exe  
  
1.  Abra un **Visual Studio Command Prompt** ventana.  
  
2.  Cambie los directorios a la carpeta que contiene los archivos de manifiesto que se desean iniciar sesión.  
  
3.  Escriba el comando siguiente para firmar el archivo de manifiesto de aplicación. Reemplace ManifestFileName con el nombre de su archivo de manifiesto además de la extensión. Reemplace el certificado con la ruta de acceso completa o relativa del archivo de certificado y contraseña con la contraseña del certificado.  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Por ejemplo, podría ejecutar el comando siguiente para firmar un manifiesto de aplicación para un complemento, una aplicación de Windows Forms o una aplicación de explorador de Windows Presentation Foundation. No se recomiendan los certificados temporales creados por Visual Studio para la implementación en entornos de producción.  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4.  Escriba el siguiente comando para actualizar y firmar el archivo de manifiesto de implementación, reemplazando los nombres de marcador de posición como en el paso anterior.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Por ejemplo, podría ejecutar el siguiente comando para actualizar y firmar un manifiesto de implementación para un complemento de Excel, una aplicación de Windows Forms o una aplicación de explorador de Windows Presentation Foundation.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Si lo desea, copie el manifiesto de implementación principal (publicar\\*appname*.application) en el directorio de implementación de la versión (publish\Application archivos\\*appname*_ *versión*).  
  
## <a name="updating-and-re-signing-the-application-and-deployment-manifests"></a>Actualizar y volver a firmar la aplicación y los manifiestos de implementación  
 Este procedimiento se supone que ya hizo cambios en la aplicación (.manifest) del archivo de manifiesto, pero que hay otros archivos que se actualizaron. Cuando se actualizan los archivos, también debe actualizarse el valor hash que representa el archivo.  
  
#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Para actualizar y volver a firmar la aplicación e implementación de manifiestos con Mage.exe  
  
1.  Abra un **Visual Studio Command Prompt** ventana.  
  
2.  Cambie los directorios a la carpeta que contiene los archivos de manifiesto que se desean iniciar sesión.  
  
3.  Quite la extensión de archivo .deploy de los archivos en la carpeta de salida de la publicación.  
  
4.  Escriba el siguiente comando para actualizar el manifiesto de aplicación con el nuevo hash para los archivos actualizados y firmar el archivo de manifiesto de aplicación. Reemplace ManifestFileName con el nombre de su archivo de manifiesto además de la extensión. Reemplace el certificado con la ruta de acceso completa o relativa del archivo de certificado y contraseña con la contraseña del certificado.  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Por ejemplo, podría ejecutar el comando siguiente para firmar un manifiesto de aplicación para un complemento, una aplicación de Windows Forms o una aplicación de explorador de Windows Presentation Foundation. No se recomiendan los certificados temporales creados por Visual Studio para la implementación en entornos de producción.  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Escriba el siguiente comando para actualizar y firmar el archivo de manifiesto de implementación, reemplazando los nombres de marcador de posición como en el paso anterior.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Por ejemplo, podría ejecutar el siguiente comando para actualizar y firmar un manifiesto de implementación para un complemento de Excel, una aplicación de Windows Forms o una aplicación de explorador de Windows Presentation Foundation.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6.  Agregue la extensión de archivo .deploy a los archivos, excepto los archivos de manifiesto de la aplicación e implementación.  
  
7.  Si lo desea, copie el manifiesto de implementación principal (publicar\\*appname*.application) en el directorio de implementación de la versión (publish\Application archivos\\*appname*_ *versión*).  
  
## <a name="see-also"></a>Vea también  
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce y Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Introducción a la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md)   
 [Cómo: Habilitar la configuración de seguridad de ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Cómo: Establecer una zona de seguridad para una aplicación ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Cómo: Establecer permisos personalizados para una aplicación ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Cómo: Depurar una aplicación ClickOnce con permisos restringidos](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Cómo: Agregar un publicador de confianza a un equipo cliente para aplicaciones ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Cómo: Configurar el comportamiento del mensaje relativo a la confianza de ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)



