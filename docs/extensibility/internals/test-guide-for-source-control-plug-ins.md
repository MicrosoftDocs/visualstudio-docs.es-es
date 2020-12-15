---
title: Guía de pruebas para los complementos de control de código fuente | Microsoft Docs
description: Obtenga información sobre cómo probar el complemento de control de código fuente con Visual Studio. En esta información general se incluyen áreas de pruebas comunes.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: a288beb618b0b539f53270928366349f47aee9e9
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487730"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Guía de pruebas para los complementos de control de código fuente
En esta sección se proporcionan instrucciones para probar el complemento de control de código fuente con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Se proporciona una amplia introducción a las áreas de pruebas más comunes, así como algunas de las más complicadas que pueden ser problemáticas. Esta introducción no pretende ser una lista exhaustiva de casos de prueba.

> [!NOTE]
> Algunas correcciones de errores y mejoras en el IDE de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] más reciente pueden revelar problemas con complementos de control de código fuente existentes que no se han encontrado previamente al usar versiones anteriores de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Se recomienda encarecidamente que pruebe el complemento de control de código fuente existente para las áreas enumeradas en esta sección, incluso si no se ha modificado desde la versión anterior de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="common-preparation"></a>Preparación común
 Se necesita un equipo con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y el complemento de control de código fuente de destino instalado. Se puede usar un segundo equipo configurado de forma similar para algunas de las pruebas Abrir desde el control de código fuente.

## <a name="definition-of-terms"></a>Definición de términos
 Para la finalidad de esta guía de pruebas, use las siguientes definiciones de términos:

 Proyecto de cliente: cualquier tipo de proyecto disponible en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que admita la integración de control de código fuente (por ejemplo, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] o [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]).

 Proyecto web: hay cuatro tipos de proyectos web: Sistema de archivos, IIS local, Sitios remotos y FTP.

- Los proyectos de sistema de archivos se crean en una ruta de acceso local, pero no necesitan la instalación de Internet Information Services (IIS), ya que se accede a ellos internamente a través de una ruta de acceso UNC, y se pueden colocar bajo el control de código fuente desde el IDE, de forma muy similar a los proyectos de cliente.

- Los proyectos IIS locales funcionan con IIS instalado en el mismo equipo, y se accede a ellos con una dirección URL que apunta al equipo local.

- Los proyectos de sitios remotos también se crean en IIS, pero se colocan bajo el control de código fuente en el equipo del servidor IIS y no desde dentro del IDE de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- El acceso a los proyectos FTP se realiza a través de un servidor FTP remoto, pero no se pueden colocar bajo el control de código fuente.

  Inscripción: otro término para la solución o proyecto bajo el control de código fuente.

  Almacén de versión: la base de datos de control de código fuente a la que se accede a través de la API del complemento de control de código fuente.

## <a name="test-areas-covered-in-this-section"></a>Áreas de prueba descritas en esta sección

- [Área de prueba 1: Incorporación y apertura desde el control de código fuente](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

  - Caso 1a: Adición de la solución al control de código fuente

  - Caso 1b: Apertura de la solución desde el control de código fuente

  - Caso 1c: Adición de la solución desde el control de código fuente

- [Área de prueba 2: Obtención desde el control de código fuente](../../extensibility/internals/test-area-2-get-from-source-control.md)

- [Área de prueba 3: Extracción del repositorio y cancelación de la operación](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

  - Caso 3: Extracción del repositorio y cancelación de la operación

  - Caso 3a: Desproteger

  - Caso 3b: Desconexión de la restauración

  - Caso 3c: Edición o guardado de consultas (QEQS)

  - Caso 3d: Restauración silenciosa

  - Caso 3e: Deshacer desprotección

- [Área de prueba 4: Inserción en el repositorio](../../extensibility/internals/test-area-4-check-in.md)

  - Caso 4a: Elementos modificados

  - Caso 4b: Adición de archivos

  - Caso 4c: Adición de proyectos

- [Área de prueba 5: Cambio del control de código fuente](../../extensibility/internals/test-area-5-change-source-control.md)

  - Caso 5a: Bind

  - Caso 5b: Unbind

  - Caso 5c: Reenlace

- [Área de prueba 6: Eliminar](../../extensibility/internals/test-area-6-delete.md)

- [Área de prueba 7: Compartir](../../extensibility/internals/test-area-7-share.md)

- [Área de prueba 8: Cambio de los complementos](../../extensibility/internals/test-area-8-plug-in-switching.md)

  - Caso 8a: Cambio automático

  - Caso 8b: Cambio basado en la solución

## <a name="see-also"></a>Consulte también
- [Complementos de control de código fuente](../../extensibility/source-control-plug-ins.md)
