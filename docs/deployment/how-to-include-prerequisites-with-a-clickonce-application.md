---
title: 'Cómo: incluir requisitos previos mediante una aplicación ClickOnce | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 7283ce590770c1ed2d14ffb79ec71d594c8b21f1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Cómo: Incluir requisitos previos mediante una aplicación ClickOnce
Para poder distribuir el software necesario con una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], primero debe descargar los paquetes del instalador para esos requisitos previos en el equipo de desarrollo. Al publicar una aplicación y elija **descargar los requisitos previos desde la misma ubicación que mi aplicación**, se producirá un error si los paquetes del instalador no están en el **paquetes** carpeta.  
  
> [!NOTE]
>  Para agregar un paquete del instalador de .NET Framework, vea [Guía de implementación de .NET Framework para desarrolladores](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx).  
  
##  <a name="Package"></a> Para agregar un paquete del instalador mediante Package.xml  
  
1.  En el Explorador de archivos, abra el **paquetes** carpeta.  
  
     De forma predeterminada, la ruta de acceso es C:\Archivos de programa\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages en un sistema de 32 bits y C:\Archivos de programa (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages en un sistema de 64 bits.  
  
2.  Abra la carpeta del requisito previo que desea agregar y, a continuación, abra la carpeta de idioma de la versión instalada de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (por ejemplo, **en** para inglés).  
  
3.  En el Bloc de notas, abra el **Package.xml** archivo.  
  
4.  Busque la **nombre** elemento que contiene **http://go.microsoft.com/fwlink**y copie la dirección URL. Incluir el **LinkID** parte.  
  
    > [!NOTE]
    >  Si no hay ningún **nombre** contiene el elemento **http://go.microsoft.com/fwlink**, abra el **Product.xml** un archivo en la carpeta raíz para el requisito previo y busque la **fwlink** cadena.  
  
    > [!IMPORTANT]
    >  Algunos requisitos previos tienen varios paquetes de instalador (por ejemplo, para los sistemas de 32 o 64 bits). Si hay varios **nombre** elementos contienen **fwlink**, debe repetir los pasos restantes para cada uno de ellos.  
  
5.  Pegue la dirección URL en la barra de direcciones del explorador y, a continuación, cuando le pregunte si desea ejecutar o guardar, elija **guardar**.  
  
     Este paso descarga el archivo de instalador en el equipo.  
  
6.  Copie el archivo en la carpeta raíz de los requisitos previos.  
  
     Por ejemplo, para los requisitos previos de Windows Installer 4.5, copie el archivo en la carpeta \Packages\WindowsInstaller4_5.  
  
     Ahora puede distribuir el paquete del instalador con la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Instalar requisitos previos mediante una aplicación ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)