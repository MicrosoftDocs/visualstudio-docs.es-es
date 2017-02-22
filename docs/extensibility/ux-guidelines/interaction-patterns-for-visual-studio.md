---
title: "Patrones de interacci&#243;n para Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# Patrones de interacci&#243;n para Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## Información general  
 Un patrón de diseño, en general, es el núcleo de un diseño que se puede aplicar en situaciones específicas para solucionar problemas con conjuntos similares de restricciones. Diseñadores de características y el sistema utilizan estos patrones de diseño como a partir de puntos, que pueden adaptarse a su situación específica.  
  
 Visual Studio tiene una biblioteca de patrones comunes de interacción que deben tenerse en cuenta al crear nuevas características. Existen dos contextos de núcleo para nuestros modelos de diseño: el cliente Visual Studio \(devenv\) y Visual Studio Online. Algunos problemas de diseño, hay un patrón ubicuo que funciona bien en todas las situaciones. Sin embargo, en muchos casos, la solución podría ser diferente para la interfaz de usuario que se presenta en un explorador y que se hospeda en una aplicación cliente.  
  
### Tipos de patrón de Visual Studio Client  
  
|Tipo de patrón|Descripción|Ejemplos|  
|--------------------|-----------------|--------------|  
|**Patrones de nivel de aplicación**|Alto nivel patrones comunes de la aplicación, determinar o mostrar el contexto de la aplicación y que contiene modelos de composición y control dentro de ellos|-   Ventanas de herramientas<br />-   Ventanas de documento|  
|**Patrones compuestos**|Patrones comunes que pueden abarcar los patrones de aplicación o un modelo reconocido formada por varios controles en una configuración de distinto|-   Cambiar de vista<br />-   Generadores de lista<br />-   Mostrar datos<br />-   Notificaciones<br />-   Validación<br />-   Modelos de selección|  
|**Patrones de control**|Obtener información específica acerca de los controles de bajo nivel cómo espera que se comporten|-   Vistas de árbol<br />-   Edición dentro de un control de cuadrícula|  
  
## Patrones de aplicaciones  
 En un nivel alto, la interfaz de Visual Studio incluye varias ventanas, cuadros de diálogo, comandos y barras de herramientas dentro de un único IDE. La jerarquía de Visual Studio determina los menús de contexto y las unidades. Los puntos de integración clave en la interfaz de usuario del IDE son ventanas de documentos, ventanas de herramientas, proyectos, la estructura del comando, el editor de texto, el cuadro de herramientas, la ventana Propiedades y herramientas \> Opciones.  
  
 Hay patrones de uso básico para cada uno de los puntos de integración clave de la interfaz de usuario del IDE:  
  
-   [Menús y comandos de Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)  
  
-   [Patrones de aplicaciones de Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)  
  
    -   [Interacciones de ventana](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)  
  
    -   [Ventanas de herramientas](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)  
  
    -   [Convenciones de editor de documentos](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)  
  
    -   [Cuadros de diálogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)  
  
    -   [Proyectos](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)  
  
## Patrones de control comunes  
 Patrones de control son principalmente acerca de los controles de forma individuales, se espera que se comportan. Se trata de un área en la que la coherencia es más importante.  
  
 Los controles más comunes en Visual Studio deben seguir las directrices de escritorio Windows. Nuestras directrices sólo incluyen las áreas en que necesitamos aumentar las convenciones comunes con las interacciones de específico de Visual Studio o lugares en los que se sustituyen a las directrices completamente con el fin de adaptarse a Visual Studio para satisfacer las necesidades de nuestros usuarios sofisticados.  
  
-   [Patrones de Control comunes para Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)  
  
    -   [Controles comunes](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)  
  
    -   [Controles de texto](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
    -   [Botones e hipervínculos](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
## Patrones compuestos  
 Hay varias maneras de que los usuarios esperan para realizar tareas. Siempre que sea posible, características deben diseñarse para usar esos patrones de interacción y de diseño visual.  
  
 Aunque hay muchos patrones compuestos dentro de Visual Studio, algunas de las más importantes con respecto a la coherencia son:  
  
-   [Patrones compuestos para Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)  
  
    -   [Interfaz de usuario y leerlo de objeto](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
    -   [Modelos de selección](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
    -   [Persistencia y guardar la configuración](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
    -   [Entrada táctil](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)