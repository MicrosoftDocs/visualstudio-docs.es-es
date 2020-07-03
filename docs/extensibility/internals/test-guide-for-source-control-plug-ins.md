---
title: Guía de pruebas para complementos de control de código fuente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 321d61175068f135aae87bff73f13ac800f4793c
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905150"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Guía de pruebas para los complementos de control de código fuente
En esta sección se proporcionan instrucciones para probar el complemento de control de código fuente con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Se proporciona una amplia introducción a las áreas de pruebas más comunes, así como algunas de las áreas más complicadas que pueden ser problemáticas. Esta información general no pretende ser una lista exhaustiva de casos de prueba.

> [!NOTE]
> Algunas correcciones de errores y mejoras en el IDE más reciente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pueden revelar problemas con los complementos de control de código fuente existentes que anteriormente no se habían encontrado al usar versiones anteriores de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Se recomienda encarecidamente que pruebe el complemento de control de código fuente existente para las áreas enumeradas en esta sección, incluso si no se han realizado cambios en el complemento desde la versión anterior de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="common-preparation"></a>Preparación común
 Se requiere un equipo con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y el complemento de control de código fuente de destino instalado. Se puede usar una segunda máquina configurada de forma similar para algunas de las pruebas de control de código fuente abiertas.

## <a name="definition-of-terms"></a>Definición de términos
 Para la finalidad de esta guía de pruebas, use las siguientes definiciones de términos:

 Proyecto de cliente cualquier tipo de proyecto disponible en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que admita la integración de control de código fuente (por ejemplo,, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] o [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] ).

 Proyecto web hay cuatro tipos de proyectos web: sistema de archivos, IIS local, sitios remotos y FTP.

- Los proyectos de sistema de archivos se crean en una ruta de acceso local, pero no requieren la instalación de Internet Information Services (IIS), ya que se accede a ellos internamente a través de una ruta de acceso UNC, y se pueden colocar bajo el control de código fuente desde el IDE, de forma muy similar a los proyectos de cliente.

- Los proyectos locales de IIS funcionan con IIS que está instalado en el mismo equipo y a los que se tiene acceso con una dirección URL que apunta a la máquina local.

- Los proyectos de sitios remotos también se crean en los servicios de IIS, pero se colocan bajo control de código fuente en el equipo del servidor IIS y no desde dentro del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- El acceso a los proyectos FTP se realiza a través de un servidor FTP remoto, pero no se pueden colocar bajo control de código fuente.

  Inscripción otro término para la solución o proyecto bajo control de código fuente.

  Versión almacene la base de datos de control de código fuente a la que se obtiene acceso a través de la API del complemento de control de código fuente.

## <a name="test-areas-covered-in-this-section"></a>Áreas de prueba descritas en esta sección

- [Área de prueba 1: agregar a o abrir desde el control de código fuente](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

  - Caso 1A: Agregar solución al control de código fuente

  - Caso 1B: abrir la solución desde el control de código fuente

  - Caso 1C: Agregar solución desde el control de código fuente

- [Área de prueba 2: obtener de control de código fuente](../../extensibility/internals/test-area-2-get-from-source-control.md)

- [Área de prueba 3: extraer o deshacer la desprotección](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

  - Caso 3: desproteger o deshacer la desprotección

  - Caso 3A: extraer del repositorio

  - Caso 3B: desconexión desconectada

  - Caso 3C: editar consulta/guardar consulta (QEQS)

  - Caso 3D: desprotección silenciosa

  - Caso 3e: deshacer la desprotección

- [Área de prueba 4: insertar en el repositorio](../../extensibility/internals/test-area-4-check-in.md)

  - Caso 4A: elementos modificados

  - Caso 4B: agregar archivos

  - Caso 4C: agregar proyectos

- [Área de prueba 5: cambiar control de código fuente](../../extensibility/internals/test-area-5-change-source-control.md)

  - Caso 5A: enlace

  - Caso 5B: desenlazar

  - Caso 5C: reenlace

- [Área de prueba 6: eliminar](../../extensibility/internals/test-area-6-delete.md)

- [Área de prueba 7: compartir](../../extensibility/internals/test-area-7-share.md)

- [Área de prueba 8: cambio de complementos](../../extensibility/internals/test-area-8-plug-in-switching.md)

  - Caso 8A: cambio automático

  - Caso 8B: cambio basado en la solución

## <a name="see-also"></a>Vea también
- [Complementos de control de código fuente](../../extensibility/source-control-plug-ins.md)
