---
title: Patrones de interacción para Visual Studio | Microsoft Docs
description: Obtenga información sobre la biblioteca de patrones de interacción comunes que puede usar al crear nuevas características para Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 05/13/2020
ms.topic: reference
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 13a2ec4332cf8010dc5d214dfd61936725ac2063
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900556"
---
# <a name="interaction-patterns-for-visual-studio"></a>Patrones de interacción para Visual Studio
## <a name="overview"></a>Información general
 Un patrón de diseño, en general, es el núcleo de un diseño que se puede aplicar en situaciones específicas para resolver problemas con conjuntos de restricciones similares. Los diseñadores de características y sistemas usan estos patrones de diseño como puntos de partida, que luego se pueden adaptar a su situación específica.

 Visual Studio una biblioteca de patrones de interacción comunes que se deben tener en cuenta al crear nuevas características. Hay dos contextos principales para nuestros patrones de diseño: Visual Studio Client (devenv) y GitHub Codespaces (anteriormente Visual Studio Online). Para algunos problemas de diseño, hay un patrón ubicuo que funciona bien en todas las situaciones. Sin embargo, en muchos casos, la solución podría ser diferente para la interfaz de usuario que se presenta dentro de un explorador y la que se hospeda en una aplicación cliente.

### <a name="visual-studio-client-pattern-types"></a>Visual Studio de patrones de cliente

|Tipo de patrón|Descripción|Ejemplos|
|------------------|-----------------|--------------|
|**Patrones de nivel de aplicación**|Patrones de alto nivel comunes a la aplicación, determinación o visualización del contexto de la aplicación, y que contienen patrones compuestos y de control dentro de ellos|- Ventanas de herramientas<br />- Ventanas de documentos|
|**Patrones compuestos**|Patrones comunes que pueden abarcar patrones de aplicación o un patrón reconocido que se conste de varios controles en una configuración distinta|- Cambio de vista<br />- Generadores de listas<br />- Mostrar datos<br />- Notificaciones<br />- Validación<br />- Modelos de selección|
|**Patrones de control**|Detalles sobre cómo se espera que se comporten los controles de bajo nivel|- Vistas de árbol<br />- Edición dentro de un control de cuadrícula|

## <a name="application-patterns"></a>Patrones de aplicación
 En un nivel alto, la interfaz Visual Studio consta de varias ventanas, cuadros de diálogo, comandos y barras de herramientas dentro de un único IDE. La Visual Studio de datos determina el contexto y los menús de unidades. Los puntos de integración clave de la interfaz de usuario del IDE son ventanas de documentos, ventanas de herramientas, proyectos, la estructura de comandos, el editor de texto, el cuadro de herramientas, el ventana Propiedades y herramientas > opciones.

 Hay patrones de uso básicos para cada uno de los puntos de integración clave en la interfaz de usuario del IDE:

- [Menús y comandos para Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Patrones de aplicaciones para Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [Interacciones de ventana](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [Ventanas de herramientas](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [Convenciones del editor de documentos](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [Diálogos](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [Proyectos](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Patrones de control comunes
 Los patrones de control son principalmente sobre cómo se espera que se comporten los controles individuales. Se trata de un área en la que la coherencia es más crítica.

 Los controles más comunes de Visual Studio deben seguir las directrices de Windows de escritorio. Nuestras directrices solo incluyen áreas en las que es necesario aumentar las convenciones comunes con interacciones específicas de Visual Studio, o lugares en los que reemplazamos las directrices por completo con el fin de adaptar Visual Studio para satisfacer las necesidades de nuestros usuarios sofisticados.

- [Patrones de control comunes para Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [Controles comunes](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [Controles de texto](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [Botones e hipervínculos](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Patrones compuestos
 Hay varias maneras en que los usuarios esperan realizar tareas. Siempre que sea posible, las características deben diseñarse para usar esos patrones tanto para la interacción como para el diseño visual.

 Aunque hay muchos patrones compuestos en Visual Studio, algunos de los más importantes con respecto a la coherencia son:

- [Patrones compuestos para Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [Interfaz de usuario en objeto y visualización](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [Modelos de selección](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [Persistencia y guardado de la configuración](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [Entrada táctil](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
