---
title: Detectar los requisitos del sistema | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: 51
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1c9bdb2a9f33f848ed0ba879aa178efd8dd96016
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582679"
---
# <a name="detecting-system-requirements"></a>Detección de requisitos del sistema
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [detectar requisitos del sistema](https://docs.microsoft.com/visualstudio/extensibility/internals/detecting-system-requirements).  
  
Un VSPackage no puede funcionar a menos que esté instalado Visual Studio. Cuando utiliza Microsoft Windows Installer para administrar la instalación del paquete de VS, puede configurar el instalador para detectar si está instalado Visual Studio. También puede configurar para comprobar el sistema para otros requisitos, por ejemplo, una versión concreta de Windows o una cantidad determinada de RAM.  
  
## <a name="detecting-visual-studio-editions"></a>Detectar las ediciones de Visual Studio  
 Para determinar si está instalada una edición de Visual Studio, compruebe que el valor de la clave del registro de instalación es (REG_DWORD) 1 en la carpeta adecuada, como se muestra en la tabla siguiente. Tenga en cuenta que hay una jerarquía de las ediciones de Visual Studio:  
  
1.  Empresa  
  
2.  Profesional  
  
3.  comunidad  
  
 Cuando se instala una edición "superior", se agregan las claves del registro para esa edición, así como para las ediciones "inferiores". Es decir, si está instalada la versión Enterprise edition, la clave de instalación se establece en 1 Enterprise, así como para las ediciones Professional y Community. Por lo tanto, deberá comprobar solo la edición "mayor" que necesita.  
  
> [!NOTE]
>  En la versión de 64 bits del editor del registro, se muestran las claves de 32 bits en HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\. Las claves de Visual Studio están bajo HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\.  
  
|Producto|Key|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Visual Studio 2015 Shell (integrado y aislado)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detecting-when-visual-studio-is-running"></a>Detectar cuándo se ejecuta Visual Studio  
 No se puede registrar el VSPackage correctamente si se ejecuta Visual Studio cuando se instala el paquete VSPackage. El instalador debe detectar cuándo se está ejecutando Visual Studio y, a continuación, rechace la instalación del programa. Windows Installer no permite usar entradas de la tabla para habilitar la detección de este tipo. En su lugar, debe crear una acción personalizada, como sigue: Use el `EnumProcesses` función para detectar el proceso devenv.exe y, a continuación, establezca una propiedad de instalador que se usa en una condición de inicio o condicionalmente mostrar un cuadro de diálogo que pide al usuario que cierre Visual Studio.  
  
## <a name="see-also"></a>Vea también  
 [Instalación de VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

