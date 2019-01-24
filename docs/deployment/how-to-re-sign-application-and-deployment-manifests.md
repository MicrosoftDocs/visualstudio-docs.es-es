---
title: Procedimiento Volver a firmar aplicaciones y manifiestos de implementación | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d5276f77226930b7ad49aea3253321ed3c8082be
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53937993"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Procedimiento Repetición de la firma de manifiestos de implementación y aplicación
Después de realizar cambios en las propiedades de implementación en el manifiesto de aplicación para aplicaciones de Windows Forms, aplicaciones de Windows Presentation Foundation (xbap) o las soluciones de Office, debe volver a firmar la aplicación y los manifiestos de implementación con un certificado. Este proceso ayuda a garantizar que no se instalen archivos alterados en los equipos de los usuarios finales.  
  
 Otro escenario donde se podrían volver a firmar los manifiestos es cuando los clientes desean firmar la aplicación y los manifiestos de implementación con su propio certificado.  
  
## <a name="re-sign-the-application-and-deployment-manifests"></a>Repetición de la firma de manifiestos de implementación y aplicación  
 Este procedimiento se supone que ya ha realizado cambios en el archivo de manifiesto de aplicación (*.manifest*). Para obtener más información, vea [Cómo: Cambiar propiedades de implementación](https://msdn.microsoft.com/library/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Para volver a firmar la aplicación e implementación de manifiestos con Mage.exe  
  
1.  Abra un **Visual Studio Command Prompt** ventana.  
  
2.  Cambie los directorios a la carpeta que contiene los archivos de manifiesto que se desean iniciar sesión.  
  
3.  Escriba el comando siguiente para firmar el archivo de manifiesto de aplicación. Reemplace *ManifestFileName* con el nombre de su archivo de manifiesto además de la extensión. Reemplace *certificado* con la ruta de acceso completa o relativa del archivo de certificado y reemplace *contraseña* con la contraseña del certificado.  
  
    ```cmd  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Por ejemplo, podría ejecutar el comando siguiente para firmar un manifiesto de aplicación para un complemento, una aplicación de Windows Forms o una aplicación de explorador de Windows Presentation Foundation. No se recomiendan los certificados temporales creados por Visual Studio para la implementación en entornos de producción.  
  
    ```cmd  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4.  Escriba el siguiente comando para actualizar y firmar el archivo de manifiesto de implementación, reemplazando los nombres de marcador de posición como en el paso anterior.  
  
    ```cmd  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Por ejemplo, podría ejecutar el siguiente comando para actualizar y firmar un manifiesto de implementación para un complemento de Excel, una aplicación de Windows Forms o una aplicación de explorador de Windows Presentation Foundation.  
  
    ```cmd  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Si lo desea, copie el manifiesto de implementación principal (*publicar\\\<appname > .application*) en el directorio de implementación de la versión (*publish\Application archivos\\ \<appname > _\<versión >*).  
  
## <a name="update-and-re-sign-the-application-and-deployment-manifests"></a>Actualizar y volver a firmar los manifiestos de aplicación e implementación  
 Este procedimiento se supone que ya ha realizado cambios en el archivo de manifiesto de aplicación (*.manifest*), pero hay otros archivos que se actualizaron. Cuando se actualizan los archivos, también debe actualizarse el valor hash que representa el archivo.  
  
#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Para actualizar y volver a firmar la aplicación e implementación de manifiestos con Mage.exe  
  
1.  Abra un **Visual Studio Command Prompt** ventana.  
  
2.  Cambie los directorios a la carpeta que contiene los archivos de manifiesto que se desean iniciar sesión.  
  
3.  Quitar el *.deploy* carpeta de salida de la extensión de archivo de los archivos de la publicación.  
  
4.  Escriba el siguiente comando para actualizar el manifiesto de aplicación con el nuevo hash para los archivos actualizados y firmar el archivo de manifiesto de aplicación. Reemplace *ManifestFileName* con el nombre de su archivo de manifiesto además de la extensión. Reemplace *certificado* con la ruta de acceso completa o relativa del archivo de certificado y reemplace *contraseña* con la contraseña del certificado.  
  
    ```cmd  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Por ejemplo, podría ejecutar el comando siguiente para firmar un manifiesto de aplicación para un complemento, una aplicación de Windows Forms o una aplicación de explorador de Windows Presentation Foundation. No se recomiendan los certificados temporales creados por Visual Studio para la implementación en entornos de producción.  
  
    ```cmd  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Escriba el siguiente comando para actualizar y firmar el archivo de manifiesto de implementación, reemplazando los nombres de marcador de posición como en el paso anterior.  
  
    ```cmd  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Por ejemplo, podría ejecutar el siguiente comando para actualizar y firmar un manifiesto de implementación para un complemento de Excel, una aplicación de Windows Forms o una aplicación de explorador de Windows Presentation Foundation.  
  
    ```cmd  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6.  Agregar el *.deploy* extensión de archivo a los archivos, excepto los archivos de manifiesto de la aplicación e implementación.  
  
7.  Si lo desea, copie el manifiesto de implementación principal (*publicar\\\<appname > .application*) en el directorio de implementación de la versión (*publish\Application archivos\\ \<appname > _\<versión >*).  
  
## <a name="see-also"></a>Vea también  
 [Protección de las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce y Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Introducción a la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md)   
 [Cómo: Activación de la configuración de seguridad de ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Cómo: Establecimiento de una zona de seguridad para una aplicación ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Cómo: Establecimiento de permisos personalizados para una aplicación ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Cómo: Depuración de una aplicación ClickOnce con permisos restringidos](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Cómo: Adición de un publicador de confianza a un equipo cliente para aplicaciones ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Cómo: Configuración del comportamiento del mensaje sobre la confianza de ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)