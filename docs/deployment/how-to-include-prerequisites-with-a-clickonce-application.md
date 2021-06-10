---
title: Incluir requisitos previos (aplicación ClickOnce)
description: Obtenga información sobre cómo obtener paquetes del instalador para los requisitos previos que se distribuirán para la aplicación ClickOnce para el equipo de desarrollo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b41529182b7cca8cea8f94206601b7a818d35420
ms.sourcegitcommit: 6aa55db5e1fe19d4d17886e0bfe140dbd186f8ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/10/2021
ms.locfileid: "111877746"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Cómo: Incluir requisitos previos mediante una aplicación ClickOnce
Para poder distribuir el software necesario con una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], primero debe descargar los paquetes del instalador para esos requisitos previos en el equipo de desarrollo. Si publica una aplicación y elige **Descargar los requisitos previos desde la misma ubicación que mi aplicación**, se producirá un error si los paquetes del instalador no están en la carpeta **Packages**.

> [!NOTE]
> Para agregar un paquete de instalador para el .NET Framework, consulte .NET Framework Deployment Guide for Developers ( Guía de implementación de aplicaciones para [desarrolladores).](/dotnet/framework/deployment/deployment-guide-for-developers)

## <a name="to-add-an-installer-package-by-using-packagexml"></a><a name="Package"></a> Para agregar un paquete del instalador mediante Package.xml

1. En el Explorador de archivos, abra la carpeta **Packages**.

    De forma predeterminada, la ruta de acceso es `%ProgramFiles(x86)%\Microsoft SDKs\ClickOnce Bootstrapper\Packages\` .

>[!NOTE]
> A partir de Visual Studio paquetes de arranque de la versión update 7 de 2019 también se detectarán en la ruta de acceso *<VS Install Path> \MSBuild\Microsoft\VisualStudio\BootstrapperPackages*.

2. Abra la carpeta del requisito previo que desea agregar y, después, abra la carpeta de idioma para la versión instalada de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (por ejemplo, **es** para español).

3. En el Bloc de notas, abra el archivo *Package.xml*.

4. Busque el **elemento Name** que contiene y copie la `http://go.microsoft.com/fwlink` dirección URL. Incluya a la parte **LinkID**.

   > [!NOTE]
   > Si ningún **elemento Name** contiene , abra el archivoProduct.xmlen la carpeta raíz para el requisito previo y `http://go.microsoft.com/fwlink` busque la cadena **fwlink.** 

   > [!IMPORTANT]
   > Algunos requisitos previos tienen varios paquetes de instalador (por ejemplo, para los sistemas de 32 o 64 bits). Si hay varios elementos **Name** que contienen **fwlink**, debe repetir los pasos restantes para cada uno de ellos.

5. Pegue la dirección URL en la barra de direcciones del explorador y, después, cuando se le pregunte si desea ejecutar o guardar, elija **Guardar**.

    Este paso descarga el archivo de instalador en el equipo.

6. Copie el archivo en la carpeta raíz de los requisitos previos.

    Por ejemplo, para el requisito .NET Framework 4.7.2, copie el archivo en la carpeta *\Packages\DotNetFX472.*

    Ahora puede distribuir el paquete del instalador con la aplicación.

## <a name="see-also"></a>Vea también
- [Cómo: Instalar requisitos previos con una aplicación ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
