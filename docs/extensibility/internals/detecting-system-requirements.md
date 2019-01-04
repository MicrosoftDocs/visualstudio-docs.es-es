---
title: Detectar los requisitos del sistema | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 27fcfa7d7ad7b098bb28a3afee301444c48a46e3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53892408"
---
# <a name="detect-system-requirements"></a>Detectar los requisitos del sistema
Un VSPackage no puede funcionar a menos que esté instalado Visual Studio. Cuando utiliza Microsoft Windows Installer para administrar la instalación del paquete de VS, puede configurar el instalador para detectar si está instalado Visual Studio. También puede configurar para comprobar el sistema para otros requisitos, por ejemplo, una versión concreta de Windows o una cantidad determinada de RAM.  
  
## <a name="detect-visual-studio-editions"></a>Detectar las ediciones de Visual Studio  
 Para determinar si está instalada una edición de Visual Studio, compruebe que el valor de la **instalar** clave del registro es *(REG_DWORD) 1* en la carpeta adecuada, como se menciona en la tabla siguiente. Tenga en cuenta que hay una jerarquía de las ediciones de Visual Studio:  
  
1.  Empresa  
  
2.  Profesional  
  
3.  comunidad  
      
Cuando se instala una edición más reciente, las claves del registro para esa edición se agregan, así como para las ediciones anteriores. Es decir, si se instala la edición Enterprise, el **instalar** clave se establece en *1* para la empresa, así como para las ediciones Professional y Community. Por lo tanto, deberá comprobar solo la edición más reciente que necesita.  
  
> [!NOTE]
>  En la versión de 64 bits del editor del registro, se muestran las claves de 32 bits en **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\**. Las claves de Visual Studio están bajo **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\**.  
  
|Producto|Key|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Visual Studio 2015 Shell (integrado y aislado)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detect-when-visual-studio-is-running"></a>Detectar cuándo se está ejecutando Visual Studio  
 No se puede registrar el VSPackage correctamente si se ejecuta Visual Studio cuando se instala el paquete VSPackage. El instalador debe detectar cuándo se está ejecutando Visual Studio y, a continuación, rechace la instalación del programa. Windows Installer no permite usar entradas de la tabla para habilitar la detección de este tipo. En su lugar, debe crear una acción personalizada, como sigue: Use la `EnumProcesses` función para detectar el *devenv.exe* procesar y, a continuación, establezca una propiedad de instalador que se usa en una condición de inicio o mostrar condicionalmente un cuadro de diálogo que pide al usuario que cierre Visual Studio.  
  
## <a name="see-also"></a>Vea también  
 [Instalar VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)