---
title: Guía de prueba para complementos de control de código fuente ( Source Control Plug-ins) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: e6b3f8e76e977472a3459697a650b32dae657c22
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704375"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Guía de pruebas para los complementos de control de código fuente
En esta sección se proporcionan instrucciones para [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]probar el complemento de control de código fuente con . Se proporciona una amplia visión general de las áreas de prueba más comunes, así como algunas de las áreas más complejas que pueden ser problemáticas. Esta descripción general no pretende ser una lista exhaustiva de casos de prueba.

> [!NOTE]
> Algunas correcciones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] errores y mejoras en el IDE más reciente pueden descubrir problemas con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]los complementos de control de código fuente existentes que no se encontraban anteriormente al usar versiones anteriores de . Se recomienda encarecidamente que pruebe el complemento de control de código fuente existente para las áreas enumeradas en esta [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]sección, incluso si no se han realizado cambios en el complemento desde la versión anterior de .

## <a name="common-preparation"></a>Preparación común
 Se requiere [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] una máquina con el complemento de control de código fuente de destino instalado. Una segunda máquina configurada de forma similar se puede utilizar para algunas de las pruebas De abierto desde control de código fuente.

## <a name="definition-of-terms"></a>Definición de Términos
 Para los fines de esta guía de prueba, utilice las siguientes definiciones de términos:

 Proyecto de cliente Cualquier [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tipo de proyecto disponible [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]que [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]admita la integración de controles de código fuente (por ejemplo, , , o [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]).

 Proyecto web Hay cuatro tipos de proyectos web: sistema de archivos, IIS local, sitios remotos y FTP.

- Los proyectos del sistema de archivos se crean en una ruta de acceso local, pero no requieren que Internet Information Services (IIS) se instale a medida que se accede a ellos internamente a través de una ruta de acceso UNC y se pueden colocar bajo control de código fuente desde dentro del IDE, al igual que los proyectos de cliente.

- Los proyectos locales de IIS funcionan con IIS que está instalado en el mismo equipo y se tiene acceso con una dirección URL que apunta al equipo local.

- Los proyectos de sitios remotos también se crean en servicios IIS, pero se colocan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bajo control de código fuente en el equipo servidor IIS y no desde dentro del IDE.

- Se accede a los proyectos FTP a través de un servidor FTP remoto, pero no se pueden colocar bajo control de código fuente.

  Inscripción Otro término para la solución o proyecto bajo control de código fuente.

  Almacén de versiones La base de datos de control de código fuente a la que se tiene acceso a través de la API de complemento de Control de código fuente.

## <a name="test-areas-covered-in-this-section"></a>Zonas de prueba cubiertas en esta sección

- [Zona de prueba 1: Añadir a/Abrir desde el Control de código fuente](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

  - Caso 1a: Agregar solución al control de código fuente

  - Caso 1b: Solución abierta desde el control de código fuente

  - Caso 1c: Agregar solución desde el Control de código fuente

- [Área de prueba 2: obtener de control de código fuente](../../extensibility/internals/test-area-2-get-from-source-control.md)

- [Zona de prueba 3: Desproteger/Deshacer pago](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

  - Caso 3: Desproteger/Deshacer pago

  - Caso 3a: Salida

  - Caso 3b: Pago desconectado

  - Caso 3c: Edición de consultas/guardado de consultas (QEQS)

  - Caso 3d: Silent Checkout

  - Caso 3e: Deshacer pago

- [Área de prueba 4: insertar en el repositorio](../../extensibility/internals/test-area-4-check-in.md)

  - Caso 4a: Artículos modificados

  - Caso 4b: Adición de archivos

  - Caso 4c: Adición de proyectos

- [Área de prueba 5: cambiar control de código fuente](../../extensibility/internals/test-area-5-change-source-control.md)

  - Caso 5a: Enlazar

  - Caso 5b: Desenlazar

  - Caso 5c: Reenlazar

- [Área de prueba 6: eliminar](../../extensibility/internals/test-area-6-delete.md)

- [Área de prueba 7: compartir](../../extensibility/internals/test-area-7-share.md)

- [Área de prueba 8: cambio de complementos](../../extensibility/internals/test-area-8-plug-in-switching.md)

  - Caso 8a: Cambio automático

  - Caso 8b: Cambio basado en soluciones

## <a name="see-also"></a>Vea también
- [Complementos de control de código fuente](../../extensibility/source-control-plug-ins.md)
