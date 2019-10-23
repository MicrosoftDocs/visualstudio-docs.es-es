---
title: 'Área de prueba 8: cambio de complementos | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb815a773351c1bb6212962a639e2758114a0e2c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722431"
---
# <a name="test-area-8-plug-in-switching"></a>Área de prueba 8: cambio de complementos
El entorno de desarrollo integrado (IDE) de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tiene la interfaz de usuario (UI) para cambiar el complemento de control de código fuente actual. Esta área de prueba proporciona casos de prueba para el proceso de selección del complemento que se va a usar para el control de código fuente de la solución.

## <a name="command-menu-access"></a>Acceso al menú de comandos
 En los casos de prueba se usan las siguientes rutas de menú del entorno de desarrollo integrado de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- Complemento de control de código fuente actual: **herramientas**  -> **Opciones**  -> **control de código fuente**  -> **selección del complemento**.

- Cambiar enlace de control de código fuente: **archivo**  -> **control de código fuente**  -> **Cambiar control de código fuente**...

## <a name="common-expected-behavior"></a>Comportamiento esperado común
 Es posible cambiar el complemento de control de código fuente para una solución sin salir de Visual Studio ni volver a cargar la solución. Además, el complemento de control de código fuente actual cambia automáticamente al que usa una solución cuando se carga esa solución.

## <a name="test-cases"></a>Casos de prueba
 Los siguientes son casos de prueba específicos para el área de prueba de cambio de complemento.

### <a name="case-8a-automatic-change"></a>Caso 8A: cambio automático

#### <a name="expected-behavior"></a>Comportamiento esperado
 Cuando un usuario carga una solución que está bajo control de código fuente, la solución se carga automáticamente y el complemento de control de código fuente adecuado se selecciona como actual.

| Acción | Pasos de prueba | Resultados esperados que se van a comprobar |
| - | - | - |
| Cambio automático de complemento de control de código fuente | 1. Seleccione el complemento en probar como actual (**herramientas**  -> **Opciones**  -> **control de código fuente**  -> **selección de complemento**).<br />2. cree un nuevo proyecto.<br />3. agregar la solución al control de código fuente.<br />4. Seleccione otro complemento (por ejemplo, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />5. aceptar la solicitud de descarga de la solución.<br />6. Vuelva a abrir la solución desde el disco. | La solución está abierta.<br /><br /> El complemento en pruebas es el complemento de control de código fuente actual. |

### <a name="case-8b-solution-based-change"></a>Caso 8B: cambio basado en la solución

#### <a name="expected-behavior"></a>Comportamiento esperado
 La solución puede tener el complemento de control de código fuente asociado cambiado.

| Acción | Pasos de prueba | Resultados esperados que se van a comprobar |
|----------------------------------| - | - |
| Cambio de complemento para una solución | 1. Seleccione el complemento en probar como actual (**herramientas**  -> **Opciones**  -> **control de código fuente**  -> **selección de complemento**).<br />2. cree un nuevo proyecto y una solución.<br />3. agregar la solución al control de código fuente.<br />4. desenlazar la solución del control de código fuente (mediante el cuadro de diálogo **Cambiar control de código fuente** ).<br />5. Seleccione otro complemento (por ejemplo, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />6. Vuelva a cargar la solución desde el disco si se ha descargado.<br />7. agregar la solución al control de código fuente.<br />8. desenlazar la solución del control de código fuente (mediante el cuadro de diálogo **Cambiar control de código fuente** ).<br />9. Seleccione el complemento en prueba de nuevo.<br />10. Vuelva a cargar la solución desde el disco si se ha descargado.<br />11. enlazar la solución a la ubicación original (mediante el cuadro de diálogo **Cambiar control de código fuente** ). | La solución se agrega al control de código fuente mediante el complemento seleccionado. |

## <a name="see-also"></a>Vea también
- [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)