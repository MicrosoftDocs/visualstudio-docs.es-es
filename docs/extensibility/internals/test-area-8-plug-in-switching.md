---
title: 'Zona de prueba 8: Conmutación de plug-ins ? Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 799fb04936a24004d73ce4c8aa3ec654490f3f62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704386"
---
# <a name="test-area-8-plug-in-switching"></a>Área de prueba 8: cambio de complementos
El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE) tiene la interfaz de usuario (UI) para cambiar el complemento de control de código fuente actual. Esta área de prueba proporciona casos de prueba para el proceso de selección del complemento que se usará para el control de código fuente de la solución.

## <a name="command-menu-access"></a>Acceso al menú de comandos
 Las [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] siguientes rutas de menú del entorno de desarrollo integrado se utilizan en los casos de prueba.

- Complemento de control de código fuente actual: **Opciones de herramientas** -> **Options** -> Selección de**complemento**de**control** -> de código fuente .

- Cambiar el enlace de control de código **fuente:** -> **Control** -> de código fuente de archivos**Cambiar control de código fuente**...

## <a name="common-expected-behavior"></a>Comportamiento esperado común
 Cambiar el complemento de control de código fuente para una solución es posible sin salir de Visual Studio o volver a cargar la solución. Además, el complemento de control de código fuente actual cambia automáticamente al que usa una solución cuando se carga esa solución.

## <a name="test-cases"></a>Casos de prueba
 Los siguientes son casos de prueba específicos para el área de prueba de conmutación de plug-in.

### <a name="case-8a-automatic-change"></a>Caso 8a: Cambio automático

#### <a name="expected-behavior"></a>Comportamiento esperado
 Cuando un usuario carga una solución que está bajo control de código fuente, la solución se carga automáticamente y se selecciona el complemento de control de código fuente adecuado como actual.

| Acción | Pasos de prueba | Resultados esperados para verificar |
| - | - | - |
| Cambio automático del plug-in de control de código fuente | 1. Seleccione plug-in bajo prueba como actual **(Opciones** -> **de herramientas** -> Selección**de plug-in**de control -> de**código**fuente .)<br />2. Cree un nuevo proyecto.<br />3. Agregue la solución al control de código fuente.<br />4. Seleccione otro plug-in [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)](por ejemplo, ).<br />5. Acepte el mensaje de la solución de descarga.<br />6. Vuelva a abrir la solución desde el disco. | La solución está abierta.<br /><br /> Plug-in bajo prueba es el plug-in de control de código fuente actual. |

### <a name="case-8b-solution-based-change"></a>Caso 8b: Cambio basado en soluciones

#### <a name="expected-behavior"></a>Comportamiento esperado
 La solución puede cambiar su complemento de control de código fuente asociado.

| Acción | Pasos de prueba | Resultados esperados para verificar |
|----------------------------------| - | - |
| Cambio de plug-in para una solución | 1. Seleccione plug-in en test como actual (**Tools** -> **Options** -> **Source Control** -> **Plug-in Selection**).<br />2. Cree un nuevo proyecto y solución.<br />3. Agregue la solución al control de código fuente.<br />4. Desvincule la solución del control de código fuente (mediante el cuadro de diálogo **Cambiar control de código fuente).**<br />5. Seleccione otro plug-in [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)](por ejemplo, ).<br />6. Vuelva a cargar la solución del disco si se descarga.<br />7. Agregue la solución al control de código fuente.<br />8. Desvincule la solución del control de código fuente (mediante el cuadro de diálogo **Cambiar control de código fuente).**<br />9. Seleccione el plug-in en prueba de nuevo.<br />10. Vuelva a cargar la solución del disco si se descarga.<br />11. Enlazar la solución a la ubicación original (mediante el cuadro de diálogo **Cambiar control de código fuente).** | Solución se agrega al control de código fuente mediante el complemento seleccionado. |

## <a name="see-also"></a>Vea también
- [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
