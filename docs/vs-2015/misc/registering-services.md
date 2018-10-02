---
title: Registrar servicios | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, registering
ms.assetid: c4ebac40-0374-4dda-948e-06fdda0e9c81
caps.latest.revision: 8
manager: douge
ms.openlocfilehash: f56c73bbb09c659a76083e511d79d487402477ac
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577866"
---
# <a name="registering-services"></a>Registrar servicios
Para admitir la carga a petición, un proveedor de servicios debe registrar sus servicios globales con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Durante el desarrollo, proveedores de servicios administrados registran servicios e invalidaciones de servicio agregando atributos al código fuente para los paquetes y, a continuación, compilar los paquetes en el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE. Esta opción ejecuta la utilidad RegPkg.exe en el ensamblado resultante, registra el paquete y lo prepara para la implementación. Para obtener más información, consulte [Cómo: registrar un servicio](../misc/how-to-register-a-service.md).  
  
 Los proveedores de servicios no administrado deben registrar los servicios que se proporcionan con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en los servicios de sección o el servicio invalida la sección del registro del sistema. En el siguiente fragmento de un archivo .reg se muestra cómo se puede registrar el servicio, SVsTextManager:  
  
```  
[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
@="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
"Name"="SVsTextManager"  
```  
  
 En el ejemplo anterior, el número de versión es la versión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], como 7.1 u 8.0, la clave {F5E7E71D-1401-11d1-883B-0000F87579D2} es el identificador de servicio (SID) del servicio, SVsTextManager y el valor de predeterminada {} F5E7E720-1401-11D1-883B-0000F87579D2} es el GUID del Administrador de texto VSPackage, que ofrece el servicio del paquete.  
  
## <a name="remote-services-and-background-threads"></a>Servicios remotos y subprocesos en segundo plano  
 Los servicios que ofrezca no están disponibles automáticamente de forma remota ni para los subprocesos en segundo plano. Para que estén disponibles, debe compilar y registrar una biblioteca de tipos.  
  
 Con código no administrado que utilice la biblioteca de Visual Studio (VSL), puede registrar la biblioteca de tipos de esta manera:  
  
```  
#define VSL_REGISTER_TYPE_LIB TRUE  
#include <VSLPackageDllEntryPoints.cpp>  
```  
  
 Con código administrado, puede agregar un paso posterior a la compilación similar al siguiente:  
  
```  
regasm /tlb MyAssembly.dll  
```  
  
## <a name="see-also"></a>Vea también  
 [Uso y provisión de servicios](../extensibility/using-and-providing-services.md)   
 [Conceptos básicos del servicio](../extensibility/internals/service-essentials.md)