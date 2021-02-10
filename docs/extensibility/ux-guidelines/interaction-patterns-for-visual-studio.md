---
title: Patrones de interacción para Visual Studio | Microsoft Docs
description: Obtenga información sobre la biblioteca de patrones de interacción comunes que puede usar al compilar nuevas características para Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 05/13/2020
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 13d111ea6e812de8290433c416a12dbd252662b5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942885"
---
# <a name="interaction-patterns-for-visual-studio"></a>Patrones de interacción para Visual Studio
## <a name="overview"></a>Información general
 En general, un modelo de diseño es el núcleo de un diseño que se puede aplicar en situaciones específicas para solucionar problemas con conjuntos de restricciones similares. Los diseñadores de características y sistemas usan estos patrones de diseño como puntos de partida, que después se pueden adaptar a su situación específica.

 Visual Studio tiene una biblioteca de patrones de interacción comunes que se deben tener en cuenta al crear nuevas características. Hay dos contextos principales para nuestros patrones de diseño: Visual Studio Client (devenv) y GitHub Codespaces (anteriormente Visual Studio online). En el caso de algunos problemas de diseño, hay un patrón omnipresente que funciona bien en todas las situaciones. En muchos casos, sin embargo, la solución puede ser diferente para la interfaz de usuario que se presenta en un explorador y que se hospeda en una aplicación cliente.

### <a name="visual-studio-client-pattern-types"></a>Tipos de patrón de cliente de Visual Studio

|Tipo de patrón|Descripción|Ejemplos|
|------------------|-----------------|--------------|
|**Patrones de nivel de aplicación**|Modelos de alto nivel comunes a la aplicación, determinar o mostrar el contexto de la aplicación y contener patrones de control y compuestos en ellos.|-Ventanas de herramientas<br />-Ventanas de documento|
|**Patrones compuestos**|Patrones comunes que pueden abarcar varios patrones de aplicación o un patrón reconocido compuesto por varios controles en una configuración distinta|-Ver cambio<br />-Enumerar generadores<br />-Mostrar datos<br />-Notificaciones<br />-Validación<br />-Modelos de selección|
|**Patrones de control**|Detalles sobre cómo se espera que se comporten los controles de bajo nivel|-Vistas de árbol<br />-Edición dentro de un control de cuadrícula|

## <a name="application-patterns"></a>Patrones de aplicación
 En un nivel alto, la interfaz de Visual Studio se compone de varias ventanas, cuadros de diálogo, comandos y barras de herramientas en un solo IDE. La jerarquía de Visual Studio determina los menús de contexto y de unidades. Los puntos de integración clave en la interfaz de usuario del IDE son ventanas de documento, ventanas de herramientas, proyectos, la estructura de comandos, el editor de texto, el cuadro de herramientas, la ventana Propiedades y herramientas > opciones.

 Existen patrones de uso básicos para cada uno de los puntos de integración clave en la interfaz de usuario del IDE:

- [Menús y comandos para Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Patrones de aplicaciones para Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [Interacciones de ventanas](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [Ventanas de herramientas](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [Convenciones del editor de documentos](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [Diálogos](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [Proyectos](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Patrones de control comunes
 Los patrones de control se centran principalmente en la forma en que se espera que se comporten los controles individuales. Se trata de un área en la que la coherencia es más crítica.

 Los controles más comunes de Visual Studio deben seguir las directrices de Windows de escritorio. Nuestras instrucciones solo incluyen áreas en las que necesitamos aumentar las convenciones comunes con las interacciones específicas de Visual Studio, o lugares en los que Reemplazamos las instrucciones por completo para adaptar Visual Studio a fin de satisfacer las necesidades de nuestros sofisticados usuarios.

- [Patrones de control comunes para Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [Controles comunes](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [Controles de texto](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [Botones e hipervínculos](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Patrones compuestos
 Hay varias maneras en las que los usuarios esperan realizar tareas. Siempre que sea posible, las características deben diseñarse para usar esos patrones para la interacción y el diseño visual.

 Aunque existen muchos patrones compuestos en Visual Studio, algunos de los más importantes en lo que respecta a la coherencia son:

- [Patrones compuestos para Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [Interfaz de usuario y inspección de objetos en el objeto](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [Modelos de selección](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [Persistencia y guardado de la configuración](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [Entrada táctil](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
