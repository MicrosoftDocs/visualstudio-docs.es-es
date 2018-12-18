---
title: 'Cómo: firmar archivos de instalación con SignTool.exe (ClickOnce) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, signtool.exe
- deploying applications [ClickOnce], re-signing setup.exe
- ClickOnce deployment, signtool.exe
- ClickOnce applications, re-signing setup.exe
- ClickOnce deployment, re-signing setup.exe
ms.assetid: 545a4005-d283-4110-9821-c78a9833c250
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b66d9440ebcf62c59049b45769a2244fc773480e
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081506"
---
# <a name="how-to-sign-setup-files-with-signtoolexe-clickonce"></a>Cómo: firmar archivos de instalación con SignTool.exe (ClickOnce)
Puede usar *SignTool.exe* para firmar un programa de instalación (*setup.exe*). Este proceso ayuda a garantizar que no se instalen archivos alterados en los equipos de los usuarios finales.  
  
 De forma predeterminada, ClickOnce tiene manifiestos firmados y un programa de instalación firmado. Sin embargo, si más tarde quiere cambiar los parámetros del programa de instalación, debe firmarlo. Si cambia los parámetros una vez firmado el programa de instalación, la firma se daña.  
  
 El procedimiento siguiente genera manifiestos sin firmar y un programa de instalación sin firmar. Después, se habilita la firma de ClickOnce en Visual Studio para generar manifiestos firmados. El programa de instalación se deja sin firmar para que el cliente pueda firmar el ejecutable con su propio certificado.  
  
### <a name="to-generate-an-unsigned-setup-program-and-sign-later"></a>Para generar un programa de instalación sin firmar y firmarlo más adelante  
  
1.  En el equipo de desarrollo, instale el certificado con el que quiere firmar el manifiesto.  
  
2.  Seleccione el proyecto en **el Explorador de soluciones**.  
  
3.  En el **proyecto** menú, haga clic en *ProjectName* **propiedades**.  
  
4.  En el **firma** página, desactive **firmar los manifiestos de ClickOnce**.  
  
5.  En el **publicar** página, haga clic en **requisitos previos**.  
  
6.  Compruebe que todos los requisitos previos están seleccionados y, a continuación, haga clic en **Aceptar**.  
  
7.  En el **publicar** página, compruebe la configuración de publicación y, a continuación, haga clic en **publicar ahora**.  
  
     La solución publica el manifiesto de la aplicación sin firmar, el manifiesto de implementación sin firmar, los archivos específicos de la versión y el programa de instalación sin firmar en la ubicación de la carpeta de publicación.  
  
8.  En el **publicar** página, haga clic en **requisitos previos**.  
  
9. En el **requisitos previos** cuadro de diálogo, desactive **crear programa de instalación para instalar los componentes necesarios**.  
  
10. En el **publicar** página, compruebe la configuración de publicación y, a continuación, haga clic en **publicar ahora**.  
  
     La solución publica el manifiesto de la aplicación firmado, el manifiesto de implementación firmado y los archivos específicos de la versión en la ubicación de la carpeta de publicación. El proceso de publicación no sobrescribe el programa de instalación sin firmar.  
  
11. En el sitio del cliente, abra un símbolo del sistema.  
  
12. Cambie al directorio que contiene el *.exe* archivo.  
  
13. Inicio de sesión el *.exe* archivo con el siguiente comando:  
  
    ```cmd  
    signtool sign /sha1 CertificateHash Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
     Por ejemplo, para firmar el programa de instalación, use uno de los comandos siguientes:  
  
    ```cmd  
    signtool sign /sha1 CCB... Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Cómo: volver a firmar manifiestos de aplicación e implementación](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
