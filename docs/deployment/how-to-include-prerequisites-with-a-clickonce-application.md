---
title: 'Cómo: incluir requisitos previos con una aplicación ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94ed90b9fcdd0c4ffe35789d00de4bbbd4aaa355
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557634"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Cómo: Incluir requisitos previos mediante una aplicación ClickOnce
Para poder distribuir el software necesario con una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], primero debe descargar los paquetes del instalador para esos requisitos previos en el equipo de desarrollo. Si publica una aplicación y elige **Descargar los requisitos previos desde la misma ubicación que mi aplicación**, se producirá un error si los paquetes del instalador no están en la carpeta **Packages**.

> [!NOTE]
> Para agregar un paquete de instalador para el .NET Framework, consulte [Guía de implementación de .NET Framework para desarrolladores](/dotnet/framework/deployment/deployment-guide-for-developers).

## <a name="Package"></a> Para agregar un paquete del instalador mediante Package.xml

1. En el Explorador de archivos, abra la carpeta **Packages**.

    De forma predeterminada, la ruta de acceso es `%ProgramFiles(x86)%\Microsoft SDKs\ClickOnce Bootstrapper\Packages\`.

2. Abra la carpeta del requisito previo que desea agregar y, después, abra la carpeta de idioma para la versión instalada de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (por ejemplo, **es** para español).

3. En el Bloc de notas, abra el archivo *Package.xml*.

4. Busque el elemento **Name** que contiene `http://go.microsoft.com/fwlink`y copie la dirección URL. Incluya a la parte **LinkID**.

   > [!NOTE]
   > Si ningún elemento de **nombre** contiene `http://go.microsoft.com/fwlink`, abra el archivo **product. XML** en la carpeta raíz del requisito previo y busque la cadena **fwlink** .

   > [!IMPORTANT]
   > Algunos requisitos previos tienen varios paquetes de instalador (por ejemplo, para los sistemas de 32 o 64 bits). Si hay varios elementos **Name** que contienen **fwlink**, debe repetir los pasos restantes para cada uno de ellos.

5. Pegue la dirección URL en la barra de direcciones del explorador y, después, cuando se le pregunte si desea ejecutar o guardar, elija **Guardar**.

    Este paso descarga el archivo de instalador en el equipo.

6. Copie el archivo en la carpeta raíz de los requisitos previos.

    Por ejemplo, para los requisitos previos de Windows Installer 4.5, copie el archivo en la carpeta *\Packages\WindowsInstaller4_5*.

    Ahora puede distribuir el paquete del instalador con la aplicación.

## <a name="see-also"></a>Consulte también
- [Cómo: Instalar requisitos previos mediante una aplicación ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
