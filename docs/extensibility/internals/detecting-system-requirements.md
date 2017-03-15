---
title: "Detectar los requisitos del sistema | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configurar, VSPackages"
  - "condiciones de inicio"
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: 50
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 50
---
# Detectar los requisitos del sistema
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un VSPackage no funcionará a menos que esté instalado Visual Studio. Cuando utiliza Microsoft Windows Installer para administrar la instalación de su paquete VSPackage, puede configurar el instalador para detectar si está instalado Visual Studio. También puede configurar para que compruebe el sistema para otros requisitos, por ejemplo, una versión concreta de Windows o una determinada cantidad de RAM.  
  
## Detectar ediciones de Visual Studio  
 Para determinar si está instalada una edición de Visual Studio, compruebe que el valor de la clave del registro de instalación es \(REG\_DWORD\) 1 en la carpeta adecuada, como se muestra en la tabla siguiente. Tenga en cuenta que hay una jerarquía de las ediciones de Visual Studio:  
  
1.  Empresa  
  
2.  Profesional  
  
3.  comunidad  
  
 Cuando se instala una edición "superior", se agregan las claves del registro para esa edición, así como para las ediciones "inferiores". Es decir, si está instalada la versión Enterprise edition, la clave de instalación se establece en 1 para la empresa, así como para las ediciones Professional y la Comunidad. Por lo tanto, deberá comprobar sólo para la edición "superior" que necesita.  
  
> [!NOTE]
>  En la versión de 64 bits del editor del registro, las claves de 32 bits se muestran bajo HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\. Las claves de Visual Studio están bajo HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\DevDiv\\vs\\Servicing\\.  
  
|Producto|Key|  
|--------------|---------|  
|Visual Studio Enterprise 2015|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\enterprise|  
|Visual Studio Professional 2015|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\professional|  
|Visual Studio Community 2015|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\community|  
|Visual Studio 2015 Shell \(integrado y aislado\)|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\isoshell|  
  
## Detectar cuándo se ejecuta Visual Studio  
 No se puede registrar correctamente el VSPackage si Visual Studio se ejecuta cuando se instala el paquete VSPackage. El programa de instalación debe detectar cuándo se ejecuta Visual Studio y, a continuación, rechace la instalación del programa. Windows Installer no permite usar entradas de la tabla para habilitar la detección de este tipo. En su lugar, debe crear una acción personalizada, como sigue: utilice el `EnumProcesses` función para detectar el proceso devenv.exe y, a continuación, establezca una propiedad de instalador que se utiliza en una condición de inicio o condicionalmente mostrar un cuadro de diálogo que pide al usuario que cierre Visual Studio.  
  
## Vea también  
 [Instalación de VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)