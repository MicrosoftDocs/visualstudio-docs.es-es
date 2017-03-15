---
title: "Comentarios para el usuario | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "comentarios del modelo de usuario"
  - "contexto, entorno"
  - "IDE, contexto"
  - "IDE, comentarios del usuario"
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Comentarios para el usuario
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En el entorno de desarrollo integrado de \(IDE\) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , comentarios visuales con respecto a la funcionalidad disponible se basa en la selección actual del usuario y el contexto global de la selección.  La tabla siguiente muestra la funcionalidad disponible en diferentes contextos de selección.  
  
|Contexto de selección|funcionalidad disponible|  
|---------------------------|------------------------------|  
|IDE|Global|  
|Conjunto actual del producto|Específico del producto|  
|jerarquía activo|Concreto escrito jerarquía|  
|elemento activo de la jerarquía|Específico del tipo de elemento de la jerarquía|  
|documento activo|Específico del tipo de documento|  
|Ventana superior \(MDI\) de interfaz de múltiples documentos|Concreto escrito ventana|  
|Contexto de selección actual|Específico del contexto de selección|  
  
 Si solo superficie la necesidad de usuarios de funcionalidad y proporciona continuamente la selección coherente y comentarios de contexto del entorno, reduce la complejidad del IDE.  Las reglas siguientes se aplican siempre que una ventana se abre en el IDE:  
  
-   Si la ventana cambia el contexto de la selección, la información de la selección se indica claramente en la ventana, y la ventana ayuda dinámica, si se muestra, se actualiza para reflejar el contexto actual.  
  
-   Si la ventana cambia el contexto global de selección, todos los menús contexto\-específicos, la ventana activa de la jerarquía, y la barra de título de la aplicación se actualizan para reflejar el contexto actual.  
  
-   La ventana debe exponer las propiedades de la selección actual de la ventana de **Propiedades** y opcionalmente, si aparece, el cuadro de diálogo **Páginas de propiedades** .  
  
-   Si la ventana no emerge las propiedades ni cambia de contexto global de selección, comentarios de selección no debe permanecer en la ventana cuando ya no es la ventana activa en el IDE.  
  
-   todas las ventanas de herramientas documento\-específicas deben reflejar continuamente el documento activo.  
  
-   Los menús, las barras de herramientas y la barra de título de la aplicación deben reflejar la ventana superior \(MDI\) del cliente de la interfaz de múltiples documentos.  
  
 Por ejemplo, cuando se abre la vista HTML de un formulario web en un proyecto de aplicación web de Visual Basic y el usuario selecciona una etiqueta de `<td>` , la información se proporciona de la manera siguiente:  
  
-   la selección se indica en la ventana activa y se refleja en la ventana de **Propiedades** .  
  
-   **Cuadro de herramientas** documento\-específico se actualiza para reflejar el documento activo.  
  
-   La barra de herramientas de **Editor** y el menú de **Tabla** se muestran y las actualizaciones de la barra de título para reflejar la ventana del formulario web.  
  
-   La ventana activa de la jerarquía, que es normalmente **Explorador de soluciones**, y la actualización de la barra de título para reflejar el contexto actual y comandos de menú contextuales de **proyecto** ahora se aplican al proyecto de aplicación web activa.  
  
## Vea también  
 [Selección y moneda en el IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md)   
 [Selección y jerarquías](../../extensibility/internals/hierarchies-and-selection.md)