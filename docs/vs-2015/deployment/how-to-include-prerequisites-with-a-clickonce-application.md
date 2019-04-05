---
title: Filtrar Incluir requisitos previos mediante una aplicación ClickOnce | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cc9ba407e91ddc8125d2836c8e2bb4329d5ad91f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58999049"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Filtrar Incluir requisitos previos con una aplicación ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para poder distribuir el software necesario con una aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], primero debe descargar los paquetes del instalador para esos requisitos previos en el equipo de desarrollo. Al publicar una aplicación y elija **descargar los requisitos previos desde la misma ubicación que mi aplicación**, se producirá un error si no se encuentran los paquetes del instalador en el **paquetes** carpeta.  
  
> [!NOTE]
>  Para agregar un paquete de instalador para .NET Framework, vea [Guía de implementación de .NET Framework para desarrolladores](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx).  
  
##  <a name="Package"></a> Para agregar un paquete del instalador mediante Package.xml  
  
1.  En el Explorador de archivos, abra la carpeta **Packages**.  
  
     De forma predeterminada, la ruta de acceso es C:\Archivos de programa\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages en un sistema de 32 bits y C:\Archivos de programa (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages en un sistema de 64 bits.  
  
2.  Abra la carpeta del requisito previo que desea agregar y, después, abra la carpeta de idioma para la versión instalada de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (por ejemplo, **es** para español).  
  
3.  En el Bloc de notas, abra el archivo **Package.xml**.  
  
4.  Busque el **nombre** elemento que contiene **http://go.microsoft.com/fwlink**y copie la dirección URL. Incluya a la parte **LinkID**.  
  
    > [!NOTE]
    >  Si no hay ningún **nombre** contiene elemento **http://go.microsoft.com/fwlink**, abra el **Product.xml** de archivos en la carpeta raíz para el requisito previo y busque el **fwlink** cadena.  
  
    > [!IMPORTANT]
    >  Algunos requisitos previos tienen varios paquetes de instalador (por ejemplo, para los sistemas de 32 o 64 bits). Si hay varios elementos **Name** que contienen **fwlink**, debe repetir los pasos restantes para cada uno de ellos.  
  
5.  Pegue la dirección URL en la barra de direcciones del explorador y, después, cuando se le pregunte si desea ejecutar o guardar, elija **Guardar**.  
  
     Este paso descarga el archivo de instalador en el equipo.  
  
6.  Copie el archivo en la carpeta raíz de los requisitos previos.  
  
     Por ejemplo, para los requisitos previos de Windows Installer 4.5, copie el archivo en la carpeta \Packages\WindowsInstaller4_5.  
  
     Ahora puede distribuir el paquete del instalador con la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Instalación de requisitos previos con una aplicación ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
