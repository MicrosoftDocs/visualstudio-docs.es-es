---
title: 'Cómo: incluir requisitos previos con una aplicación ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9639da1f735095f6d04a59d1f2302f822423e006
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "77557677"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Cómo: Incluir requisitos previos mediante una aplicación ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para poder distribuir el software necesario con una aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], primero debe descargar los paquetes del instalador para esos requisitos previos en el equipo de desarrollo. Al publicar una aplicación y elegir **descargar los requisitos previos desde la misma ubicación que mi aplicación**, se producirá un error si los paquetes del instalador no están en la carpeta **paquetes** .  
  
> [!NOTE]
> Para agregar un paquete de instalador para el .NET Framework, consulte [Guía de implementación de .NET Framework para desarrolladores](/dotnet/framework/deployment/deployment-guide-for-developers).  
  
## <a name="to-add-an-installer-package-by-using-packagexml"></a><a name="Package"></a> Para agregar un paquete del instalador mediante Package.xml  
  
1. En el Explorador de archivos, abra la carpeta **Packages**.  
  
     De forma predeterminada, la ruta de acceso es C:\Archivos de programa\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages en un sistema de 32 bits y C:\Archivos de programa (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages en un sistema de 64 bits.  
  
2. Abra la carpeta del requisito previo que desea agregar y, después, abra la carpeta de idioma para la versión instalada de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (por ejemplo, **es** para español).  
  
3. En el Bloc de notas, abra el archivo **Package.xml**.  
  
4. Busque el elemento **Name** que contiene `http://go.microsoft.com/fwlink` y copie la dirección URL. Incluya a la parte **LinkID**.  
  
    > [!NOTE]
    > Si no contiene ningún elemento **Name** `http://go.microsoft.com/fwlink` , abra el archivo **Product.xml** en la carpeta raíz del requisito previo y busque la cadena **fwlink** .  
  
    > [!IMPORTANT]
    > Algunos requisitos previos tienen varios paquetes de instalador (por ejemplo, para los sistemas de 32 o 64 bits). Si hay varios elementos **Name** que contienen **fwlink**, debe repetir los pasos restantes para cada uno de ellos.  
  
5. Pegue la dirección URL en la barra de direcciones del explorador y, después, cuando se le pregunte si desea ejecutar o guardar, elija **Guardar**.  
  
     Este paso descarga el archivo de instalador en el equipo.  
  
6. Copie el archivo en la carpeta raíz de los requisitos previos.  
  
     Por ejemplo, para los requisitos previos de Windows Installer 4.5, copie el archivo en la carpeta \Packages\WindowsInstaller4_5.  
  
     Ahora puede distribuir el paquete del instalador con la aplicación.  
  
## <a name="see-also"></a>Consulte también  
 [Cómo: instalar los requisitos previos con una aplicación ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
