---
title: Patrones de interacción para Visual Studio ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac917aeb2530570b755e7f1e6fc6de00714a54b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698378"
---
# <a name="interaction-patterns-for-visual-studio"></a>Patrones de interacción para Visual Studio
## <a name="overview"></a>Información general
 Un patrón de diseño, en general, es el núcleo de un diseño que se puede aplicar en situaciones específicas para resolver problemas con conjuntos similares de restricciones. Los diseñadores de características y sistemas utilizan estos patrones de diseño como puntos de partida, que luego se pueden adaptar a su situación específica.

 Visual Studio tiene una biblioteca de patrones de interacción comunes que se deben tener en cuenta al crear nuevas características. Hay dos contextos principales para nuestros patrones de diseño: Visual Studio Client (devenv) y Visual Studio Online. Para algunos problemas de diseño, hay un patrón ubicuo que funciona bien en todas las situaciones. En muchos casos, sin embargo, la solución puede ser diferente para la interfaz de usuario que se presenta en un explorador y la que se hospeda en una aplicación cliente.

### <a name="visual-studio-client-pattern-types"></a>Tipos de patrones de cliente de Visual Studio

|Tipo de patrón|Descripción|Ejemplos|
|------------------|-----------------|--------------|
|**Patrones de nivel de aplicación**|Patrones de alto nivel comunes a la aplicación, determinando o mostrando el contexto de la aplicación y conteniendo patrones compuestos y de control dentro de ellos|- Ventanas de herramientas<br />- Ventanas de documentos|
|**Patrones compuestos**|Patrones comunes que pueden abarcar patrones de aplicación, o un patrón reconocido compuesto por varios controles en una configuración distinta|- Conmutación de vista<br />- Constructores de listas<br />- Visualización de datos<br />- Notificaciones<br />- Validación<br />- Modelos de selección|
|**Patrones de control**|Detalles sobre cómo se espera que se comporten los controles de bajo nivel|- Vistas a los árboles<br />- Edición dentro de un control de cuadrícula|

## <a name="application-patterns"></a>Patrones de aplicación
 En un nivel alto, la interfaz de Visual Studio consta de varias ventanas, cuadros de diálogo, comandos y barras de herramientas dentro de un único IDE. La jerarquía de Visual Studio determina los menús de contexto e unidades. Los puntos clave de integración en la interfaz de usuario del IDE son ventanas de documento, ventanas de herramientas, proyectos, la estructura de comandos, el editor de texto, el cuadro de herramientas, la ventana Propiedades y Herramientas > Opciones.

 Hay patrones de uso básicos para cada uno de los puntos de integración clave en la interfaz de usuario del IDE:

- [Menús y comandos para Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Patrones de aplicaciones para Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [Interacciones de ventanas](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [Ventanas de herramientas](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [Convenciones del editor de documentos](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [Diálogos](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [Proyectos](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Patrones de control comunes
 Los patrones de control se basan principalmente en cómo se espera que se comporten los controles individuales. Este es un área en la que la consistencia es más crítica.

 Los controles más comunes de Visual Studio deben seguir las directrices de Desktop Windows. Nuestras directrices solo incluyen áreas en las que necesitamos aumentar las convenciones comunes con interacciones específicas de Visual Studio, o lugares en los que reemplazamos las directrices por completo con el fin de adaptar Visual Studio para satisfacer las necesidades de nuestros usuarios sofisticados.

- [Patrones de control comunes para Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [Controles comunes](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [Controles de texto](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [Botones e hipervínculos](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Patrones compuestos
 Hay varias maneras en que los usuarios esperan realizar tareas. Siempre que sea posible, las características deben diseñarse para utilizar esos patrones tanto para la interacción como para el diseño visual.

 Aunque hay muchos patrones compuestos en Visual Studio, algunos de los más importantes con respecto a la coherencia son:

- [Patrones compuestos para Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [Interfaz de usuario en el objeto y miradas](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [Modelos de selección](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [Configuración de persistencia y ahorro](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [Entrada táctil](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
