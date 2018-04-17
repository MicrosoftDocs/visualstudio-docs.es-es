---
title: Guía de pruebas para los complementos de Control de código fuente | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 37af6a289b59b6066a71836e4d44e380b584ec70
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="test-guide-for-source-control-plug-ins"></a>Guía de pruebas para los complementos de Control de código fuente
Esta sección proporciona instrucciones para probar el complemento con control de código fuente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Se proporciona una amplia información general de las áreas de pruebas más comunes, así como algunas de las áreas más intrincadas que pueden ser problemáticas. Esta información general no pretende ser una lista exhaustiva de casos de prueba.  
  
> [!NOTE]
>  Algunas correcciones de errores y mejoras en la versión más reciente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE puede revelar problemas con origen control complementos existentes que previamente no han encontrado durante el uso de las versiones anteriores de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Se recomienda encarecidamente que pruebe el control de código fuente existente complemento para las áreas que se enumeran en esta sección, incluso si no se han realizado ningún cambio en el complemento desde la versión anterior de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="common-preparation"></a>Preparación comunes  
 Una máquina con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y el complemento de control de código fuente de destino instalado, es necesario. Un segundo equipo configurado de forma similar puede utilizarse para algunos de lo que está abierto de pruebas de Control de código fuente.  
  
## <a name="definition-of-terms"></a>Definición de términos  
 Con el propósito de esta guía de prueba, use las siguientes definiciones de términos:  
  
 Proyecto de cliente  
 Cualquier tipo de disponible en proyecto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que admite la integración del control de código fuente (por ejemplo, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], o [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]).  
  
 Proyecto Web  
 Hay cuatro tipos de proyectos Web: sistema de archivos, IIS Local, sitios remotos y FTP.  
  
-   Se crean proyectos de sistema de archivos en una ruta de acceso local, pero no requieren Internet Information Services (IIS) para instalarse cuando se tiene acceso internamente a través de una ruta de acceso UNC y puede colocarse bajo control de código fuente desde el IDE, como proyectos de cliente.  
  
-   Proyectos IIS locales funcionan con IIS que está instalado en el mismo equipo y se tiene acceso con una dirección URL que apunta a la máquina local.  
  
-   También se crean proyectos de sitios remotos en los servicios de IIS, pero se colocan en el control de código fuente en el equipo del servidor IIS y no desde dentro de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
-   Se tiene acceso a los proyectos FTP a través de un servidor FTP remoto pero no se puede colocar en el control de código fuente.  
  
 Inscripción  
 Otro término de la solución o proyecto bajo control de código fuente.  
  
 Almacén de versiones  
 La base de datos de control de código fuente que se tiene acceso a través de la API de complementos de Control de código fuente.  
  
## <a name="test-areas-covered-in-this-section"></a>Áreas de pruebas que se tratan en esta sección  
  
-   [Área de prueba 1: Agregar a / Open de Control de código fuente](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)  
  
    -   Caso 1a: Agregar solución al Control de código fuente  
  
    -   Caso 1b: Abrir solución desde el Control de código fuente  
  
    -   Caso c de 1: agregar la solución de Control de código fuente  
  
-   [Área de prueba 2: obtener de control de código fuente](../../extensibility/internals/test-area-2-get-from-source-control.md)  
  
-   [Zona de ensayo 3: Extraer del repositorio / Deshacer desprotección](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)  
  
    -   Caso 3: Extraer del repositorio / Deshacer desprotección  
  
    -   Caso 3a: extraer del repositorio  
  
    -   Caso 3b: desconectado desprotección  
  
    -   Caso 3C: Editar consulta/guardar (QEQS)  
  
    -   Mayúsculas y minúsculas 3d: Retirada silenciosa  
  
    -   Caso 3e: Deshacer desprotección  
  
-   [Área de prueba 4: insertar en el repositorio](../../extensibility/internals/test-area-4-check-in.md)  
  
    -   Caso 4a: modificar elementos  
  
    -   Caso 4b: agregar archivos  
  
    -   Caso 4c: agregar proyectos  
  
-   [Área de prueba 5: cambiar control de código fuente](../../extensibility/internals/test-area-5-change-source-control.md)  
  
    -   Caso 5a: enlazar  
  
    -   Caso 5b: desenlazar  
  
    -   Caso 5c: reenlazar  
  
-   [Área de prueba 6: eliminar](../../extensibility/internals/test-area-6-delete.md)  
  
-   [Área de prueba 7: compartir](../../extensibility/internals/test-area-7-share.md)  
  
-   [Área de prueba 8: cambio de complementos](../../extensibility/internals/test-area-8-plug-in-switching.md)  
  
    -   Caso 8a: cambio automático  
  
    -   Caso 8b: cambio de la solución  
  
## <a name="see-also"></a>Vea también  
 [Complementos de control de código fuente](../../extensibility/source-control-plug-ins.md)