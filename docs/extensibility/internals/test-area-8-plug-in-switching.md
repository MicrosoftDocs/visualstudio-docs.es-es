---
title: "Prueba &#225;rea 8: Cambio de complementos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "control de código fuente [Visual Studio SDK], cambiar los complementos"
  - "origen control complementos, cambiar"
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Prueba &#225;rea 8: Cambio de complementos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

el entorno de desarrollo integrado de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(IDE\) tiene la interfaz de usuario \(UI\) para cambiar el complemento de control de código fuente actual.  Esta área de pruebas proporciona los casos de prueba para el proceso de la cosecha que complemento a utilizar para el control de código fuente de la solución.  
  
## menú de comandos Access  
 Las siguientes rutas de menú del entorno de desarrollo integrado de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se utilizan en los casos de prueba.  
  
-   complemento de control de código fuente actual: **Herramientas** \- \> **Opciones** \- \> **Control de código fuente** \- \> **Selección de complemento**.  
  
-   Enlace del control de código fuente de cambio: **Archivo** \- \> **Control de código fuente** \- \> **Control de código fuente de cambio**…  
  
## El comportamiento esperado común  
 Cambiar el complemento de control de código fuente de una solución es posible sin salga de Visual Studio o volver a cargar la solución.  Además, los cambios actuales del complemento de control de código fuente automáticamente el utilizan una solución cuando esa solución cargada.  
  
## Casos de prueba  
 Los siguientes son casos de prueba concretos para el área de prueba que cambia de complemento.  
  
### caso 8a: cambio automático  
  
#### El comportamiento esperado  
 Cuando un usuario carga una solución que está bajo control de código fuente, la solución se carga automáticamente y el complemento de control de código fuente adecuado es seleccionado como actual.  
  
|Acción|Pasos de prueba|Resultados esperado a comprobar|  
|------------|---------------------|-------------------------------------|  
|Cambio automático del complemento de control de código fuente|1.  Complemento seleccione en pruebas como en ejecución \(**Herramientas** \- \> **Opciones** \- \> **Control de código fuente** \- \> **Selección de complemento**.\)<br />2.  Cree un nuevo proyecto.<br />3.  Agregar la solución al control de código fuente.<br />4.  Seleccione otro complemento \(por ejemplo, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]\).<br />5.  acepte descargar el indicador de la solución.<br />6.  vuelva a abrir la solución desde el disco.|se abre la solución.<br /><br /> El complemento en pruebas es el complemento de control de código fuente actual.|  
  
### caso 8b: cambio Solución\-basado  
  
#### El comportamiento esperado  
 La solución tenga el complemento de control de código fuente asociado cambiado.  
  
|Acción|Pasos de prueba|Resultados esperado a comprobar|  
|------------|---------------------|-------------------------------------|  
|cambio de complemento para una solución|1.  Complemento seleccione en pruebas como en ejecución \(**Herramientas** \- \> **Opciones** \- \> **Control de código fuente** \- \> **Selección de complemento**\).<br />2.  Cree un nuevo proyecto y solución.<br />3.  Agregar la solución al control de código fuente.<br />4.  Desvincular la solución de control de código fuente \(mediante el cuadro de diálogo **Control de código fuente de cambio** \).<br />5.  Seleccione otro complemento \(por ejemplo, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]\).<br />6.  recargue la solución desde el disco si está descargado.<br />7.  Agregar la solución al control de código fuente.<br />8.  Desvincular la solución de control de código fuente \(mediante el cuadro de diálogo **Control de código fuente de cambio** \).<br />9. Complemento seleccione en pruebas de nuevo.<br />10. Solución reload desde el disco si está descargado.<br />11. Enlace la solución en la ubicación original \(mediante el cuadro de diálogo **Control de código fuente de cambio** \).|La solución se agrega al control de código fuente utilizando el complemento seleccionado.|  
  
## Vea también  
 [Guía de pruebas para los complementos de Control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)