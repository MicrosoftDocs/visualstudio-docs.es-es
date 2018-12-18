---
title: Guía de pruebas para los complementos de Control de código fuente | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eea089da8c8e0b7e626f58660a57cd499a93fb7c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778916"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Guía de pruebas para los complementos de control de código fuente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esta sección proporciona instrucciones para probar su complemento con control de código fuente [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Se proporciona una visión general amplia de las áreas más comunes de pruebas, así como algunas de las áreas más complicadas que pueden ser problemáticas. Esta información general no pretende ser una lista exhaustiva de casos de prueba.  
  
> [!NOTE]
>  Algunas correcciones de errores y mejoras en la versión más reciente [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE puede revelar problemas con origen control complementos existentes que previamente no han encontrado durante el uso de las versiones anteriores de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Se recomienda encarecidamente que pruebe el control de código fuente existente complemento para las áreas que se enumeran en esta sección, incluso si no hay cambios realizados al complemento desde la versión anterior de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="common-preparation"></a>Preparación comunes  
 Una máquina con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] y el complemento de control de código fuente de destino instalado, es necesario. Una segunda máquina configurada de forma similar puede utilizarse para algunas de la de apertura desde las pruebas de Control de código fuente.  
  
## <a name="definition-of-terms"></a>Definición de términos  
 Con el propósito de esta guía de prueba, use las siguientes definiciones de términos:  
  
 Proyecto de cliente  
 Cualquier proyecto de los tipos disponibles en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] que admite la integración de control de código fuente (por ejemplo, [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], [!INCLUDE[csprcs](../../includes/csprcs-md.md)], o [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]).  
  
 Proyecto Web  
 Hay cuatro tipos de proyectos Web: sistema de archivos, IIS Local, sitios remotos y FTP.  
  
- Se crean proyectos de sistema de archivos en una ruta de acceso local, pero no requieren Internet Information Services (IIS) para instalarse cuando se tiene acceso internamente a través de una ruta de acceso UNC y pueden colocarse bajo control de código fuente desde el IDE, muy similar a los proyectos de cliente.  
  
- Proyectos IIS locales funcionan con IIS que está instalado en el mismo equipo y se tiene acceso con una dirección URL que apunta a la máquina local.  
  
- También se crean proyectos de sitios remotos en los servicios de IIS, pero están colocados bajo control de código fuente en el equipo del servidor IIS y no desde dentro de la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
- Se tiene acceso a los proyectos FTP a través de un servidor FTP remoto pero no se puede colocar bajo control de código fuente.  
  
  Inscripción  
  Otro término de la solución o proyecto bajo control de código fuente.  
  
  Versión Store  
  La base de datos de control de código fuente que se accede a través de la API de complemento de Control de código fuente.  
  
## <a name="test-areas-covered-in-this-section"></a>En esta sección tratadas de áreas de pruebas  
  
-   [Área de prueba 1: agregar a/abrir desde control de código fuente](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)  
  
    -   Caso 1a: Agregar solución al Control de código fuente  
  
    -   Caso 1b: abrir soluciones desde Control de código fuente  
  
    -   Caso c de 1: agregar la solución desde Control de código fuente  
  
-   [Área de prueba 2: obtener de control de código fuente](../../extensibility/internals/test-area-2-get-from-source-control.md)  
  
-   [Área de prueba 3: extraer del repositorio/cancelar extracción del repositorio](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)  
  
    -   Caso 3: Extraer / Deshacer desprotección  
  
    -   Caso 3a: desproteger  
  
    -   Caso 3b: desconecta la desprotección  
  
    -   Caso 3C: Editar consulta/guardar (QEQS)  
  
    -   Mayúsculas y minúsculas 3d: Retirada silenciosa  
  
    -   Caso 3e: Deshacer desprotección  
  
-   [Área de prueba 4: insertar en el repositorio](../../extensibility/internals/test-area-4-check-in.md)  
  
    -   Caso 4a: modificar elementos  
  
    -   Caso 4b: adición de archivos  
  
    -   Caso 4c: agregar proyectos  
  
-   [Área de prueba 5: cambiar control de código fuente](../../extensibility/internals/test-area-5-change-source-control.md)  
  
    -   Caso 5a: enlazar  
  
    -   Caso 5b: desenlazar  
  
    -   Caso c de 5: volver a enlazar  
  
-   [Área de prueba 6: eliminar](../../extensibility/internals/test-area-6-delete.md)  
  
-   [Área de prueba 7: compartir](../../extensibility/internals/test-area-7-share.md)  
  
-   [Área de prueba 8: cambio de complementos](../../extensibility/internals/test-area-8-plug-in-switching.md)  
  
    -   Caso 8a: cambios automático  
  
    -   Caso 8b: cambio de solución  
  
## <a name="see-also"></a>Vea también  
 [Complementos de control de código fuente](../../extensibility/source-control-plug-ins.md)

