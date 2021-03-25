---
title: 'Área de prueba 8: cambio de complementos | Microsoft Docs'
description: Este área de prueba del control de código fuente proporciona casos de prueba para el proceso de selección del complemento que se va a usar para el control de código fuente de la solución en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2dbc6b9646bcdec8cbdfae9d262397eb0ff74bdc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090777"
---
# <a name="test-area-8-plug-in-switching"></a>Área de prueba 8: Cambio de los complementos
El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE) tiene la interfaz de usuario (UI) para cambiar el complemento de control de código fuente actual. Esta área de prueba proporciona casos de prueba para el proceso de selección del complemento que se va a usar para el control de código fuente de la solución.

## <a name="command-menu-access"></a>Acceso al menú de comandos
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]En los casos de prueba se usan las siguientes rutas de menú del entorno de desarrollo integrado.

- Complemento de control de código fuente actual: opciones de **herramientas**  ->    ->    ->  **selección de complemento** de control de código fuente.

- Cambiar enlace de control de código **Fuente: control** de código fuente de cambio de control de código fuente  ->    ->  ...

## <a name="common-expected-behavior"></a>Comportamiento esperado común
 Es posible cambiar el complemento de control de código fuente para una solución sin salir de Visual Studio ni volver a cargar la solución. Además, el complemento de control de código fuente actual cambia automáticamente al que usa una solución cuando se carga esa solución.

## <a name="test-cases"></a>Casos de prueba
 Los siguientes son casos de prueba específicos para el área de prueba de cambio de complemento.

### <a name="case-8a-automatic-change"></a>Caso 8a: Cambio automático

#### <a name="expected-behavior"></a>Comportamiento esperado
 Cuando un usuario carga una solución que está bajo control de código fuente, la solución se carga automáticamente y el complemento de control de código fuente adecuado se selecciona como actual.

| Acción | Pasos de prueba | Resultados esperados que se van a comprobar |
| - | - | - |
| Cambio automático de complemento de control de código fuente | 1. Seleccione el complemento en prueba como actual (**herramientas**  ->  **Opciones**  ->  complemento de **control de código fuente**  ->  **selección**).<br />2. cree un nuevo proyecto.<br />3. agregar la solución al control de código fuente.<br />4. Seleccione otro complemento (por ejemplo, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ).<br />5. aceptar la solicitud de descarga de la solución.<br />6. Vuelva a abrir la solución desde el disco. | La solución está abierta.<br /><br /> El complemento en pruebas es el complemento de control de código fuente actual. |

### <a name="case-8b-solution-based-change"></a>Caso 8b: Cambio basado en la solución

#### <a name="expected-behavior"></a>Comportamiento esperado
 La solución puede tener el complemento de control de código fuente asociado cambiado.

| Acción | Pasos de prueba | Resultados esperados que se van a comprobar |
|----------------------------------| - | - |
| Cambio de complemento para una solución | 1. Seleccione el complemento en prueba como actual (**herramientas**  ->  **Opciones**  ->  selección complemento de **control de código fuente**  ->  ).<br />2. cree un nuevo proyecto y una solución.<br />3. agregar la solución al control de código fuente.<br />4. desenlazar la solución del control de código fuente (mediante el cuadro de diálogo **Cambiar control de código fuente** ).<br />5. Seleccione otro complemento (por ejemplo, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ).<br />6. Vuelva a cargar la solución desde el disco si se ha descargado.<br />7. agregar la solución al control de código fuente.<br />8. desenlazar la solución del control de código fuente (mediante el cuadro de diálogo **Cambiar control de código fuente** ).<br />9. Seleccione el complemento en prueba de nuevo.<br />10. Vuelva a cargar la solución desde el disco si se ha descargado.<br />11. enlazar la solución a la ubicación original (mediante el cuadro de diálogo **Cambiar control de código fuente** ). | La solución se agrega al control de código fuente mediante el complemento seleccionado. |

## <a name="see-also"></a>Consulte también
- [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
