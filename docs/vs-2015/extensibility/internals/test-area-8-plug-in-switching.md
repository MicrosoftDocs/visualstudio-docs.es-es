---
title: 'El área de prueba 8: Cambio de complementos | Microsoft Docs'
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
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 103946f29cb893672b29d7671a74acf1c26bc50e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793820"
---
# <a name="test-area-8-plug-in-switching"></a>Área de prueba 8: cambio de complementos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] el entorno de desarrollo integrado (IDE) tiene la interfaz de usuario (UI) para cambiar el complemento de control de código fuente actual. Esta área de prueba proporciona los casos de prueba para el proceso de seleccionar qué complemento que se usará para el control de código fuente de la solución.  
  
## <a name="command-menu-access"></a>Acceso al menú de comandos  
 La siguiente [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] rutas de menú del entorno de desarrollo integrado que se usan en los casos de prueba.  
  
-   Complemento de control de código fuente actual: **herramientas** -> **opciones** -> **Control de código fuente** -> **selección de complemento** .  
  
-   Cambiar origen de enlace de control: **archivo** -> **Control de código fuente** -> **cambiar Control de código fuente**...  
  
## <a name="common-expected-behavior"></a>Comportamiento esperado comunes  
 Es posible cambiar el complemento para una solución de control de origen sin salir de Visual Studio ni volver a cargar la solución. Además, el complemento de control de código fuente actual cambia automáticamente a la utilizada por una solución cuando se carga esa solución.  
  
## <a name="test-cases"></a>Casos de prueba  
 Los siguientes son casos de prueba concretos para el área de prueba de conmutación complemento.  
  
### <a name="case-8a-automatic-change"></a>Caso 8a: cambios automático  
  
#### <a name="expected-behavior"></a>Comportamiento esperado  
 Cuando un usuario carga una solución que está bajo control de código fuente, la solución se carga automáticamente y el complemento de control de origen correspondiente se selecciona como actual.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|----------------|--------------------------------|  
|Cambio de complemento de control de origen automática|1.  Seleccione complemento bajo prueba como actual (**herramientas** -> **opciones** -> **Control de código fuente** -> **complemento Selección**.)<br />2.  Cree un nuevo proyecto.<br />3.  Agregue la solución al control de código fuente.<br />4.  Seleccione otro complemento (por ejemplo, [!INCLUDE[vsvss](../../includes/vsvss-md.md)]).<br />5.  Acepte Descargando mensaje de solución.<br />6.  Vuelva a abrir la solución desde el disco.|Se abre la solución.<br /><br /> Complemento sometida a prueba es el complemento de control de código fuente actual.|  
  
### <a name="case-8b-solution-based-change"></a>Caso 8b: cambio de solución  
  
#### <a name="expected-behavior"></a>Comportamiento esperado  
 La solución puede tener su complemento de control de código fuente asociado puede cambiar.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|----------------|--------------------------------|  
|Cambio de complemento para una solución|1.  Seleccione complemento bajo prueba como actual (**herramientas** -> **opciones** -> **Control de código fuente** -> **complemento Selección**).<br />2.  Cree un nuevo proyecto y solución.<br />3.  Agregue la solución al control de código fuente.<br />4.  Desenlazar la solución desde control de código fuente (mediante el **cambiar Control de código fuente** cuadro de diálogo).<br />5.  Seleccione otro complemento (por ejemplo, [!INCLUDE[vsvss](../../includes/vsvss-md.md)]).<br />6.  Si descarga, vuelva a cargar la solución desde el disco.<br />7.  Agregue la solución al control de código fuente.<br />8.  Desenlazar la solución desde control de código fuente (mediante **cambiar Control de código fuente** cuadro de diálogo).<br />9. Seleccione el complemento sometida a prueba de nuevo.<br />10. Recargue la solución desde el disco si se descargan.<br />11. Enlazar la solución en la ubicación original (con el **cambiar Control de código fuente** cuadro de diálogo).|Solución se agrega al control de código fuente utilizando el complemento.|  
  
## <a name="see-also"></a>Vea también  
 [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

