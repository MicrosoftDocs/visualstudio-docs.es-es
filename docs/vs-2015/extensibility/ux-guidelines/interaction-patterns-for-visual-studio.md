---
title: Patrones de interacción para Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c6dcb0ccb6a8793649c0b12b6851ba58b9374da9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779377"
---
# <a name="interaction-patterns-for-visual-studio"></a>Patrones de interacción para Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="overview"></a>Información general  
 Un patrón de diseño, en general, es el núcleo de un diseño que se puede aplicar en situaciones específicas para solucionar problemas con conjuntos similares de restricciones. Diseñadores de característica y el sistema utilizan estos patrones de diseño como a partir de puntos, que, a continuación, se pueden adaptados a su situación específica.  
  
 Visual Studio tiene una biblioteca de patrones comunes de interacción que deben tenerse en cuenta al crear las nuevas características. Hay dos contextos de núcleo para nuestros modelos de diseño: el cliente Visual Studio (devenv) y Visual Studio Online. Para algunos problemas de diseño, hay un modelo ubicuo que funciona bien en todas las situaciones. Sin embargo, en muchos casos, la solución podría ser diferente para la interfaz de usuario que se presenta en un explorador y lo que se hospeda en una aplicación cliente.  
  
### <a name="visual-studio-client-pattern-types"></a>Tipos de patrón de Visual Studio Client  
  
|Tipo de patrón|Descripción|Ejemplos|  
|------------------|-----------------|--------------|  
|**Patrones de nivel de aplicación**|Patrones de alto nivel comunes a la aplicación, determinar o mostrar el contexto de la aplicación y que contiene los patrones de control y compuestos dentro de ellos|: Ventanas de herramientas<br />: Ventanas de documento|  
|**Patrones compuestos**|Patrones comunes que pueden abarcar los patrones de aplicación o un modelo reconocido formada por varios controles en una configuración de distinto|: Cambiar de vista<br />-Los generadores de list<br />-Mostrar datos<br />-Notificaciones<br />: Validación<br />: Modelos de selección|  
|**Patrones de control**|Información específica acerca de los controles de bajo nivel de cómo se espera que se comportan|: Vistas de árbol<br />-Edición dentro de un control de cuadrícula|  
  
## <a name="application-patterns"></a>Patrones de aplicación  
 En un nivel alto, la interfaz de Visual Studio incluye varios windows, los cuadros de diálogo, comandos y las barras de herramientas dentro de un único IDE. La jerarquía de Visual Studio determina los menús de contexto y las unidades. Los puntos de integración clave en la interfaz de usuario del IDE son ventanas de documento, las ventanas de herramientas, proyectos, la estructura del comando, el editor de texto, el cuadro de herramientas, la ventana Propiedades y herramientas > Opciones.  
  
 Hay patrones de uso básico de cada uno de los puntos de integración clave en la interfaz de usuario del IDE:  
  
-   [Menús y comandos para Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)  
  
-   [Patrones de aplicaciones para Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)  
  
    -   [Interacciones de ventana](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)  
  
    -   [Ventanas de herramientas](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)  
  
    -   [Convenciones del editor de documentos](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)  
  
    -   [Cuadros de diálogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)  
  
    -   [Proyectos](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)  
  
## <a name="common-control-patterns"></a>Patrones de control comunes  
 Patrones de control son principalmente sobre los controles individuales de cómo se espera que se comportan. Se trata de un área en la que la coherencia es más importante.  
  
 Los controles más comunes en Visual Studio deben seguir las instrucciones de escritorio Windows. Nuestras directrices solo incluyen las áreas en que necesitamos aumentar las convenciones comunes con interacciones específico de Visual Studio o en lugares en el que se sustituyen a las directrices completamente con el fin de adaptar Visual Studio para satisfacer las necesidades de nuestros usuarios sofisticados.  
  
-   [Patrones de control comunes para Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)  
  
    -   [Controles comunes](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)  
  
    -   [Controles de texto](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
    -   [Botones e hipervínculos](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
## <a name="composite-patterns"></a>Patrones compuestos  
 Hay varias maneras de que los usuarios esperan para realizar tareas. Siempre que sea posible, las características deben diseñarse para que use esos patrones de interacción y diseño visual.  
  
 Aunque hay muchos patrones compuestos dentro de Visual Studio, algunas de las más importantes con respecto a la coherencia son:  
  
-   [Patrones compuestos para Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)  
  
    -   [Interfaz de usuario y leerlo de objeto](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
    -   [Modelos de selección](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
    -   [Persistencia y guardar la configuración](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
    -   [Entrada táctil](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)

