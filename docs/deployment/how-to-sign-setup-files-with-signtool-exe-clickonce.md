---
title: 'Cómo: firmar archivos de instalación con SignTool.exe (ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: edc6630bfe8dd5ee1fc48fe0d5abe189a63ab330
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619971"
---
# <a name="how-to-sign-setup-files-with-signtoolexe-clickonce"></a>Cómo: Firmar archivos de instalación con SignTool.exe (ClickOnce)
Puede usar *SignTool.exe* para firmar un programa de instalación (*setup.exe*). Este proceso ayuda a garantizar que no se instalen archivos alterados en los equipos de los usuarios finales.

 De forma predeterminada, ClickOnce tiene manifiestos firmados y un programa de instalación firmado. Sin embargo, si más tarde quiere cambiar los parámetros del programa de instalación, debe firmarlo. Si cambia los parámetros una vez firmado el programa de instalación, la firma se daña.

 El procedimiento siguiente genera manifiestos sin firmar y un programa de instalación sin firmar. Después, se habilita la firma de ClickOnce en Visual Studio para generar manifiestos firmados. El programa de instalación se deja sin firmar para que el cliente pueda firmar el ejecutable con su propio certificado.

### <a name="to-generate-an-unsigned-setup-program-and-sign-later"></a>Para generar un programa de instalación sin firmar y firmarlo más adelante

1.  En el equipo de desarrollo, instale el certificado con el que quiere firmar el manifiesto.

2.  Seleccione el proyecto en el **Explorador de soluciones**.

3.  En el menú **Proyecto**, haga clic en **Propiedades** de *NombreDelProyecto*.

4.  En la página **Firma**, desactive **Firmar los manifiestos de ClickOnce**.

5.  En la página **Publicar**, haga clic en **Requisitos previos**.

6.  Compruebe que se han seleccionado todos los requisitos previos y haga clic en **Aceptar**.

7.  En la página **Publicar**, compruebe la configuración de la publicación y haga clic en **Publicar ahora**.

     La solución publica el manifiesto de la aplicación sin firmar, el manifiesto de implementación sin firmar, los archivos específicos de la versión y el programa de instalación sin firmar en la ubicación de la carpeta de publicación.

8.  En la página **Publicar**, haga clic en **Requisitos previos**.

9. En el cuadro de diálogo **Requisitos previos**, desactive **Crear programa de instalación para instalar los componentes necesarios**.

10. En la página **Publicar**, compruebe la configuración de la publicación y haga clic en **Publicar ahora**.

     La solución publica el manifiesto de la aplicación firmado, el manifiesto de implementación firmado y los archivos específicos de la versión en la ubicación de la carpeta de publicación. El proceso de publicación no sobrescribe el programa de instalación sin firmar.

11. En el sitio del cliente, abra un símbolo del sistema.

12. Cambie al directorio que contiene el archivo *.exe*.

13. Firme el archivo *.exe* con el siguiente comando:

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
- [Procedimientos para volver a firmar manifiestos de aplicación e implementación](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
