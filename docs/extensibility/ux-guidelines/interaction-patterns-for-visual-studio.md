---
title: Patrones de interacción para Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 094e16fea46e459dd64338ffa5daf3f7b98afb90
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="interaction-patterns-for-visual-studio"></a>Patrones de interacción para Visual Studio
## <a name="overview"></a>Información general  
 Un modelo de diseño, por lo general, es el núcleo de un diseño que se pueden aplicar en situaciones específicas para solucionar problemas con conjuntos similares de restricciones. Diseñadores de características y de sistema usar estos patrones de diseño como a partir de puntos, ya que, a continuación, se pueden personalizar para su situación concreta.  
  
 Visual Studio tiene una biblioteca de patrones de interacción comunes que deben tenerse en cuenta al generar nuevas características. Existen dos contextos de núcleo para nuestro patrones de diseño: el cliente Visual Studio (devenv) y Visual Studio Online. Para algunos problemas de diseño, hay un modelo ubicuo que funciona correctamente en todas las situaciones. Sin embargo, en muchos casos, la solución podría ser diferente para la interfaz de usuario que se muestran en un explorador y que se hospeda en una aplicación cliente.  
  
### <a name="visual-studio-client-pattern-types"></a>Tipos de patrón de Visual Studio Client  
  
|Tipo de modelo|Descripción|Ejemplos|  
|------------------|-----------------|--------------|  
|**Patrones de nivel de aplicación**|Patrones de alto nivel comunes a la aplicación, determinar o mostrar el contexto de la aplicación y que contiene los patrones de control y compuestos dentro de ellos|: Las ventanas de herramientas<br />: Ventanas de documento|  
|**Patrones compuestos**|Los patrones comunes que pueden extender a patrones de aplicación o un modelo reconocido formada por varios controles en una configuración de distinto|: Cambiar de vista<br />: Generadores de lista<br />-Mostrar datos<br />-Notificaciones<br />: Validación<br />: Modelos de selección|  
|**Patrones de control**|Obtener información específica acerca de los controles de bajo nivel de cómo se espera que se comportan|: Vistas de árbol<br />-Edición dentro de un control de cuadrícula|  
  
## <a name="application-patterns"></a>Patrones de aplicación  
 En un nivel alto, la interfaz de Visual Studio incluye varias ventanas, cuadros de diálogo, comandos y barras de herramientas dentro de un único IDE. La jerarquía de Visual Studio determina los menús de contexto y las unidades. Los puntos clave de integración en la interfaz de usuario del IDE son ventanas de documento, las ventanas de herramientas, proyectos, la estructura del comando, el editor de texto, el cuadro de herramientas, la ventana Propiedades y herramientas > Opciones.  
  
 Hay patrones de uso básico para cada uno de los puntos clave de integración en la interfaz de usuario del IDE:  
  
-   [Menús y comandos para Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)  
  
-   [Patrones de aplicaciones para Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)  
  
    -   [Interacciones de ventana](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)  
  
    -   [Ventanas de herramientas](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)  
  
    -   [Convenciones de editor de documentos](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)  
  
    -   [Cuadros de diálogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)  
  
    -   [Proyectos](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)  
  
## <a name="common-control-patterns"></a>Patrones de control comunes  
 Patrones de control son principalmente acerca de los controles de forma individuales, se espera que se comportan. Se trata de un área en la que es más importante coherencia.  
  
 Los controles más comunes en Visual Studio deben seguir las directrices de escritorio Windows. Nuestras directrices solo incluyen las áreas en el que se deba aumentar las convenciones comunes con las interacciones de específicos de Visual Studio o en lugares en el que se sustituyen a las instrucciones por completo con el fin de personalizar Visual Studio para satisfacer las necesidades de nuestros usuarios sofisticados.  
  
-   [Patrones de control comunes para Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)  
  
    -   [Controles comunes](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)  
  
    -   [Controles de texto](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
    -   [Botones e hipervínculos](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
## <a name="composite-patterns"></a>Patrones compuestos  
 Hay varias maneras de que los usuarios esperan para realizar tareas. Siempre que sea posible, se deben diseñar características para utilizar esos patrones de interacción y de diseño visual.  
  
 Aunque hay muchos patrones compuestos dentro de Visual Studio, algunos de los más importantes con respecto a la coherencia son:  
  
-   [Patrones compuestos para Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)  
  
    -   [Interfaz de usuario en el objeto y el examen](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
    -   [Modelos de selección](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
    -   [Persistencia y guardar la configuración](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
    -   [Entrada táctil](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)