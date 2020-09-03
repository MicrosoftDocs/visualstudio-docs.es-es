---
title: Guía de pruebas para complementos de control de código fuente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6790e61eddc81045bb168028ee7aeef7a0492e3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825748"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Guía de pruebas para los complementos de control de código fuente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En esta sección se proporcionan instrucciones para probar el complemento de control de código fuente con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Se proporciona una amplia introducción a las áreas de pruebas más comunes, así como algunas de las áreas más complicadas que pueden ser problemáticas. Esta información general no pretende ser una lista exhaustiva de casos de prueba.  
  
> [!NOTE]
> Algunas correcciones de errores y mejoras en el IDE más reciente [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pueden revelar problemas con los complementos de control de código fuente existentes que anteriormente no se habían encontrado al usar versiones anteriores de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Se recomienda encarecidamente que pruebe el complemento de control de código fuente existente para las áreas enumeradas en esta sección, incluso si no se han realizado cambios en el complemento desde la versión anterior de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="common-preparation"></a>Preparación común  
 Se requiere un equipo con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] y el complemento de control de código fuente de destino instalado. Se puede usar una segunda máquina configurada de forma similar para algunas de las pruebas de control de código fuente abiertas.  
  
## <a name="definition-of-terms"></a>Definición de términos  
 Para la finalidad de esta guía de pruebas, use las siguientes definiciones de términos:  
  
 Proyecto de cliente  
 Cualquier tipo de proyecto disponible en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] que admita la integración de control de código fuente (por ejemplo,, [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] o [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] ).  
  
 proyecto web  
 Hay cuatro tipos de proyectos web: sistema de archivos, IIS local, sitios remotos y FTP.  
  
- Los proyectos de sistema de archivos se crean en una ruta de acceso local, pero no requieren la instalación de Internet Information Services (IIS), ya que se accede a ellos internamente a través de una ruta de acceso UNC, y se pueden colocar bajo el control de código fuente desde el IDE, de forma muy similar a los proyectos de cliente.  
  
- Los proyectos locales de IIS funcionan con IIS que está instalado en el mismo equipo y a los que se tiene acceso con una dirección URL que apunta a la máquina local.  
  
- Los proyectos de sitios remotos también se crean en los servicios de IIS, pero se colocan bajo control de código fuente en el equipo del servidor IIS y no desde dentro del [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
- El acceso a los proyectos FTP se realiza a través de un servidor FTP remoto, pero no se pueden colocar bajo control de código fuente.  
  
  Inscripción  
  Otro término para la solución o el proyecto bajo control de código fuente.  
  
  Almacén de versiones  
  La base de datos de control de código fuente a la que se obtiene acceso a través de la API del complemento de control de código fuente.  
  
## <a name="test-areas-covered-in-this-section"></a>Áreas de prueba descritas en esta sección  
  
- [Área de prueba 1: Incorporación y apertura desde el control de código fuente](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)  
  
  - Caso 1A: Agregar solución al control de código fuente  

  - Caso 1B: abrir la solución desde el control de código fuente  

  - Caso 1C: Agregar solución desde el control de código fuente  

- [Área de prueba 2: Obtención desde el control de código fuente](../../extensibility/internals/test-area-2-get-from-source-control.md)  
  
- [Área de prueba 3: Extracción del repositorio y cancelación de la operación](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)  
  
  - Caso 3: desproteger o deshacer la desprotección  

  - Caso 3A: extraer del repositorio  

  - Caso 3B: desconexión desconectada  

  - Caso 3C: editar consulta/guardar consulta (QEQS)  

  - Caso 3D: desprotección silenciosa  

  - Caso 3e: deshacer la desprotección  
  
- [Área de prueba 4: Inserción en el repositorio](../../extensibility/internals/test-area-4-check-in.md)  
  
  - Caso 4A: elementos modificados  

  - Caso 4B: agregar archivos  

  - Caso 4C: agregar proyectos  
  
- [Área de prueba 5: Cambio del control de código fuente](../../extensibility/internals/test-area-5-change-source-control.md)  
  
  - Caso 5A: enlace  

  - Caso 5B: desenlazar  

  - Caso 5C: reenlace  

- [Área de prueba 6: Eliminar](../../extensibility/internals/test-area-6-delete.md)  

- [Área de prueba 7: Compartir](../../extensibility/internals/test-area-7-share.md)  

- [Área de prueba 8: Cambio de los complementos](../../extensibility/internals/test-area-8-plug-in-switching.md)  

  - Caso 8A: cambio automático  

  - Caso 8B: cambio basado en la solución  

## <a name="see-also"></a>Consulte también  
 [Complementos de control de código fuente](../../extensibility/source-control-plug-ins.md)
