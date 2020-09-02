---
title: Cómo volver a firmar los manifiestos de aplicación e implementación | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1905ea32a9899a1262e146f264e0a1179f0e8c6e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382203"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Cómo: Volver a firmar manifiestos de aplicación e implementación
Después de realizar cambios en las propiedades de implementación en el manifiesto de aplicación para las aplicaciones de Windows Forms, las aplicaciones Windows Presentation Foundation (XBAP) o las soluciones de Office, debe volver a firmar los manifiestos de aplicación e implementación con un certificado. Este proceso ayuda a garantizar que no se instalen archivos alterados en los equipos de los usuarios finales.

 Otro escenario en el que podría volver a firmar los manifiestos es cuando los clientes quieren firmar los manifiestos de aplicación e implementación con su propio certificado.

## <a name="re-sign-the-application-and-deployment-manifests"></a>Repetición de la firma de manifiestos de implementación y aplicación
 En este procedimiento se supone que ya ha realizado cambios en el archivo de manifiesto de la aplicación (*. manifest*). Para obtener más información, vea [Cómo: cambiar las propiedades de implementación](https://msdn.microsoft.com/library/66052a3a-8127-4964-8147-2477ef5d1472).

#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Para volver a firmar la aplicación y los manifiestos de implementación con Mage.exe

1. Abra una ventana **del símbolo del sistema de Visual Studio** .

2. Cambie los directorios a la carpeta que contiene los archivos de manifiesto que desea firmar.

3. Escriba el siguiente comando para firmar el archivo de manifiesto de la aplicación. Reemplace *ManifestFileName* por el nombre del archivo de manifiesto más la extensión. Reemplace *Certificate* por la ruta de acceso completa o relativa del archivo de certificado y reemplace *password* por la contraseña del certificado.

    ```cmd
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     Por ejemplo, puede ejecutar el siguiente comando para firmar un manifiesto de aplicación para un complemento, una aplicación de Windows Forms o una aplicación de Explorador Windows Presentation Foundation. Los certificados temporales creados por Visual Studio no se recomiendan para la implementación en entornos de producción.

    ```cmd
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

4. Escriba el siguiente comando para actualizar y firmar el archivo de manifiesto de implementación, reemplazando los nombres de marcador de posición como en el paso anterior.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     Por ejemplo, puede ejecutar el siguiente comando para actualizar y firmar un manifiesto de implementación para un complemento de Excel, una aplicación Windows Forms o una aplicación de Explorador Windows Presentation Foundation.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. Opcionalmente, copie el manifiesto de implementación principal (*Publish \\ \<appname> . Application*) en el directorio de implementación de la versión (*publish\Application files \\ \<appname> _ \<version> *).

## <a name="update-and-re-sign-the-application-and-deployment-manifests"></a>Actualizar y volver a firmar los manifiestos de aplicación e implementación
 En este procedimiento se supone que ya ha realizado cambios en el archivo de manifiesto de la aplicación (*. manifest*), pero que hay otros archivos que se han actualizado. Cuando se actualizan los archivos, también debe actualizarse el hash que representa el archivo.

#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Para actualizar y volver a firmar los manifiestos de aplicación e implementación con Mage.exe

1. Abra una ventana **del símbolo del sistema de Visual Studio** .

2. Cambie los directorios a la carpeta que contiene los archivos de manifiesto que desea firmar.

3. Quite la extensión de archivo *. deploy* de los archivos de la carpeta de salida de publicación.

4. Escriba el siguiente comando para actualizar el manifiesto de aplicación con los nuevos hash para los archivos actualizados y firmar el archivo de manifiesto de la aplicación. Reemplace *ManifestFileName* por el nombre del archivo de manifiesto más la extensión. Reemplace *Certificate* por la ruta de acceso completa o relativa del archivo de certificado y reemplace *password* por la contraseña del certificado.

    ```cmd
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     Por ejemplo, puede ejecutar el siguiente comando para firmar un manifiesto de aplicación para un complemento, una aplicación de Windows Forms o una aplicación de Explorador Windows Presentation Foundation. Los certificados temporales creados por Visual Studio no se recomiendan para la implementación en entornos de producción.

    ```cmd
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. Escriba el siguiente comando para actualizar y firmar el archivo de manifiesto de implementación, reemplazando los nombres de marcador de posición como en el paso anterior.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     Por ejemplo, puede ejecutar el siguiente comando para actualizar y firmar un manifiesto de implementación para un complemento de Excel, una aplicación Windows Forms o una aplicación de Explorador Windows Presentation Foundation.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

6. Vuelva a agregar la extensión de archivo *. deploy* a los archivos, excepto los archivos de manifiesto de aplicación y de implementación.

7. Opcionalmente, copie el manifiesto de implementación principal (*Publish \\ \<appname> . Application*) en el directorio de implementación de la versión (*publish\Application files \\ \<appname> _ \<version> *).

## <a name="see-also"></a>Consulte también
- [Protección de las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)
- [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce y Authenticode](../deployment/clickonce-and-authenticode.md)
- [Introducción a la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md)
- [Cómo: habilitar la configuración de seguridad de ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Cómo: establecer una zona de seguridad para una aplicación ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Cómo: establecer permisos personalizados para una aplicación ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Procedimientos para depurar una aplicación ClickOnce con permisos restringidos](securing-clickonce-applications.md)
- [Procedimientos para agregar un publicador de confianza a un equipo cliente para aplicaciones ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Procedimientos para configurar el comportamiento del mensaje relativo a la confianza de ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)