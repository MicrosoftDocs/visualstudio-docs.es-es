---
title: "Gu&#237;a de pruebas para los complementos de Control de c&#243;digo fuente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "los complementos, control de código fuente"
  - "control de código fuente [Visual Studio SDK], complementos de pruebas"
  - "pruebas, los complementos de control de código fuente"
  - "control de origen pruebas, plug-ins"
  - "origen control complementos, Guía de prueba"
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# Gu&#237;a de pruebas para los complementos de Control de c&#243;digo fuente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Esta sección proporciona orientación para probar el complemento de control de código fuente con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Información general detallada de las zonas de pruebas más comunes, así como algunas áreas más complejas que pueden ser problemáticas se proporciona.  Esta información general no está diseñado para ser una lista exhaustiva de casos de prueba.  
  
> [!NOTE]
>  Algunas correcciones de errores y mejoras en último [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE pueden detectar problemas con los complementos existentes de control de código fuente que no se encontraron previamente mientras que utilicen versiones anteriores de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Se recomienda probar el complemento de control de código fuente existente para las áreas enumeradas en esta sección, incluso si no se ha realizado ningún cambio al complemento desde la versión anterior de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## preparación común  
 Un equipo con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y el complemento de control de código fuente de destino instalado, se requiere.  Un segundo equipo configurado de forma similar se puede utilizar para algo de Abrir de pruebas de control de código fuente.  
  
## definición de términos  
 Con el propósito esta guía de prueba, utilice las siguientes definiciones de términos:  
  
 proyecto de cliente  
 Cualquier tipo de proyecto disponibles en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que admite la integración del control de código fuente \(por ejemplo, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], o [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]\).  
  
 Proyecto web  
 hay cuatro tipos de proyectos web: Sistema de archivos, local internet information services, sitios remotos, y FTP.  
  
-   Los proyectos del sistema de archivos se crean en una ruta de acceso local, pero no requieren el \(IIS\) IIS instalarse como se realiza internamente a través de una ruta UNC, y pueden ser sometidos a control de código fuente desde el IDE, como proyectos de cliente.  
  
-   Trabajo de proyectos locales de IIS con IIS instalado en el mismo equipo y acceso con una dirección URL que señale al equipo local.  
  
-   Los proyectos de sitios remotos también se crean en IIS Services, pero se colocan bajo control de código fuente en el equipo servidor de IIS y no desde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el IDE.  
  
-   Los proyectos de FTP se realiza a través de un servidor FTP remoto pero no pueden colocar bajo control de código fuente.  
  
 inscripción  
 Otro término para la solución o proyecto en control de código fuente.  
  
 almacén de versiones  
 La base de datos de control de código fuente que se está acceso con el complemento de control de código fuente API.  
  
## Áreas de prueba Covered en la sección de Esta  
  
-   [Área de prueba 1: Agregar a abrir desde el Control de código fuente](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)  
  
    -   caso 1a: Agregar la solución al control de código fuente  
  
    -   caso 1b: Solución abierta del control de código fuente  
  
    -   caso 1c: Agregue la solución de control de código fuente  
  
-   [Área de prueba 2: Obtener de Control de código fuente](../../extensibility/internals/test-area-2-get-from-source-control.md)  
  
-   [Área de prueba 3: Desproteger o deshacer desprotección](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)  
  
    -   caso 3: Desproteger y comprobación de deshacer  
  
    -   caso 3a: Desproteger  
  
    -   caso 3b: Desprotección desconectado  
  
    -   caso 3c: Edición de la consulta\/guardar de la consulta \(QEQS\)  
  
    -   caso 3d: Desprotección silencioso  
  
    -   caso 3e: Deshacer desprotección  
  
-   [Zona de ensayo 4: Comprobar](../../extensibility/internals/test-area-4-check-in.md)  
  
    -   caso 4a: elementos modificados  
  
    -   caso 4b: Archivos de suma  
  
    -   caso 4c: Proyectos de suma  
  
-   [Zona de ensayo 5: Control de código fuente de cambio](../../extensibility/internals/test-area-5-change-source-control.md)  
  
    -   caso 5a: enlace  
  
    -   caso 5b: Desenlazar  
  
    -   caso 5c: reencuaderne  
  
-   [Probar área 6: eliminar](../../extensibility/internals/test-area-6-delete.md)  
  
-   [Probar área 7: recurso compartido](../../extensibility/internals/test-area-7-share.md)  
  
-   [Prueba área 8: Cambio de complementos](../../extensibility/internals/test-area-8-plug-in-switching.md)  
  
    -   caso 8a: cambio automático  
  
    -   caso 8b: cambio Solución\-basado  
  
## Vea también  
 [Complementos de Control de código fuente](../../extensibility/source-control-plug-ins.md)