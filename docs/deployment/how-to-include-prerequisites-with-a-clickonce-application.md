---
title: "C&#243;mo: Incluir requisitos previos mediante una aplicaci&#243;n ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# C&#243;mo: Incluir requisitos previos mediante una aplicaci&#243;n ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para poder distribuir el software necesario con una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], primero debe descargar los paquetes del instalador para esos requisitos previos en el equipo de desarrollo.  Si publica una aplicación y elige **Descargar los requisitos previos desde la misma ubicación que mi aplicación**, se producirá un error si los paquetes del instalador no están en la carpeta **Packages**.  
  
> [!NOTE]
>  Para agregar un paquete de instalador para .NET Framework, consulte [Guía de implementación de .NET Framework para desarrolladores](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx).  
  
##  <a name="Package"></a> Para agregar un paquete del instalador mediante Package.xml  
  
1.  En el Explorador de archivos, abra la carpeta **Packages**.  
  
     De forma predeterminada, la ruta de acceso es C:\\Archivos de programa\\Microsoft Visual Studio 14.0\\SDK\\Bootstrapper\\Packages en un sistema de 32 bits y C:\\Archivos de programa \(x86\)\\Microsoft Visual Studio 14.0\\SDK\\Bootstrapper\\Packages en un sistema de 64 bits.  
  
2.  Abra la carpeta del requisito previo que desea agregar y, a continuación, abra la carpeta de idioma para la versión instalada de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(por ejemplo, **es** para español\).  
  
3.  En el Bloc de notas, abra el archivo **Package.xml**.  
  
4.  Busque el elemento **Name** que contiene **http:\/\/go.microsoft.com\/fwlink** y copie la dirección URL.  Incluya a la parte **LinkID**.  
  
    > [!NOTE]
    >  Si no hay ningún elemento **Name** que contenga **http:\/\/go.microsoft.com\/fwlink**, abra el archivo **Product.xml** en la carpeta raíz para el requisito previo y busque la cadena **fwlink**.  
  
    > [!IMPORTANT]
    >  Algunos requisitos previos tienen varios paquetes de instalador \(por ejemplo, para los sistemas de 32 o 64 bits\).  Si hay varios elementos **Name** que contienen **fwlink**, debe repetir los pasos restantes para cada uno de ellos.  
  
5.  Pegue la dirección URL en la barra de direcciones del explorador y, a continuación, cuando se le pregunte si desea ejecutar o guardar, elija **Guardar**.  
  
     Este paso descarga el archivo de instalador en el equipo.  
  
6.  Copie el archivo en la carpeta raíz de los requisitos previos.  
  
     Por ejemplo, para los requisitos previos de Windows Installer 4.5, copie el archivo en la carpeta \\Packages\\WindowsInstaller4\_5.  
  
     Ahora puede distribuir el paquete del instalador con la aplicación.  
  
## Vea también  
 [Cómo: Instalar requisitos previos mediante una aplicación ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)