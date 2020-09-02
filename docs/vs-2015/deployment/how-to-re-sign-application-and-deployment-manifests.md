---
title: 'Cómo: volver a firmar los manifiestos de aplicación y de implementación | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d5956ad23fe22c7c36b712fac61df268586142df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697555"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Cómo: Volver a firmar manifiestos de aplicación e implementación
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Después de realizar cambios en las propiedades de implementación en el manifiesto de aplicación para las aplicaciones de Windows Forms, las aplicaciones Windows Presentation Foundation (XBAP) o las soluciones de Office, debe volver a firmar los manifiestos de aplicación e implementación con un certificado. Este proceso ayuda a garantizar que no se instalen archivos alterados en los equipos de los usuarios finales.  
  
 Otro escenario en el que podría volver a firmar los manifiestos es cuando los clientes quieren firmar los manifiestos de aplicación e implementación con su propio certificado.  
  
## <a name="re-signing-the-application-and-deployment-manifests"></a>Volver a firmar los manifiestos de aplicación e implementación  
 En este procedimiento se supone que ya ha realizado cambios en el archivo de manifiesto de la aplicación (. manifest). Para obtener más información, vea [Cómo: cambiar las propiedades de implementación](https://msdn.microsoft.com/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Para volver a firmar la aplicación y los manifiestos de implementación con Mage.exe  
  
1. Abra una ventana **del símbolo del sistema de Visual Studio** .  
  
2. Cambie los directorios a la carpeta que contiene los archivos de manifiesto que desea firmar.  
  
3. Escriba el siguiente comando para firmar el archivo de manifiesto de la aplicación. Reemplace ManifestFileName por el nombre del archivo de manifiesto más la extensión. Reemplace Certificate por la ruta de acceso completa o relativa del archivo de certificado y reemplace password por la contraseña del certificado.  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Por ejemplo, puede ejecutar el siguiente comando para firmar un manifiesto de aplicación para un complemento, una aplicación de Windows Forms o una aplicación de Explorador Windows Presentation Foundation. Los certificados temporales creados por Visual Studio no se recomiendan para la implementación en entornos de producción.  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4. Escriba el siguiente comando para actualizar y firmar el archivo de manifiesto de implementación, reemplazando los nombres de marcador de posición como en el paso anterior.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Por ejemplo, puede ejecutar el siguiente comando para actualizar y firmar un manifiesto de implementación para un complemento de Excel, una aplicación Windows Forms o una aplicación de Explorador Windows Presentation Foundation.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5. También puede copiar el manifiesto de implementación principal (publicar \\ *appname*. Application) en el directorio de implementación de la versión (publish\Application files \\ *appname*_*version*).  
  
## <a name="updating-and-re-signing-the-application-and-deployment-manifests"></a>Actualizar y volver a firmar los manifiestos de aplicación e implementación  
 En este procedimiento se supone que ya ha realizado cambios en el archivo de manifiesto de la aplicación (. manifest), pero que hay otros archivos que se han actualizado. Cuando se actualizan los archivos, también debe actualizarse el hash que representa el archivo.  
  
#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Para actualizar y volver a firmar los manifiestos de aplicación e implementación con Mage.exe  
  
1. Abra una ventana **del símbolo del sistema de Visual Studio** .  
  
2. Cambie los directorios a la carpeta que contiene los archivos de manifiesto que desea firmar.  
  
3. Quite la extensión de archivo. deploy de los archivos de la carpeta de salida de publicación.  
  
4. Escriba el siguiente comando para actualizar el manifiesto de aplicación con los nuevos hash para los archivos actualizados y firmar el archivo de manifiesto de la aplicación. Reemplace ManifestFileName por el nombre del archivo de manifiesto más la extensión. Reemplace Certificate por la ruta de acceso completa o relativa del archivo de certificado y reemplace password por la contraseña del certificado.  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Por ejemplo, puede ejecutar el siguiente comando para firmar un manifiesto de aplicación para un complemento, una aplicación de Windows Forms o una aplicación de Explorador Windows Presentation Foundation. Los certificados temporales creados por Visual Studio no se recomiendan para la implementación en entornos de producción.  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5. Escriba el siguiente comando para actualizar y firmar el archivo de manifiesto de implementación, reemplazando los nombres de marcador de posición como en el paso anterior.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Por ejemplo, puede ejecutar el siguiente comando para actualizar y firmar un manifiesto de implementación para un complemento de Excel, una aplicación Windows Forms o una aplicación de Explorador Windows Presentation Foundation.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6. Vuelva a agregar la extensión de archivo. deploy a los archivos, excepto los archivos de manifiesto de aplicación y de implementación.  
  
7. También puede copiar el manifiesto de implementación principal (publicar \\ *appname*. Application) en el directorio de implementación de la versión (publish\Application files \\ *appname*_*version*).  
  
## <a name="see-also"></a>Consulte también  
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce y Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Introducción a la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md)   
 [Cómo: habilitar la configuración de seguridad de ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Cómo: establecer una zona de seguridad para una aplicación ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Cómo: establecer permisos personalizados para una aplicación ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Cómo: depurar una aplicación ClickOnce con permisos restringidos](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Cómo: agregar un editor de confianza a un equipo cliente para aplicaciones ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Cómo: configurar el comportamiento del mensaje de confianza de ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)
