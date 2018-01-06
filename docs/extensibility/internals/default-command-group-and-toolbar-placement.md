---
title: "Valor predeterminado de comando, grupo y la ubicación de la barra de herramientas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
caps.latest.revision: "30"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 84e850d44162a964ce6ef8b64be92ce4eeacb86e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="default-command-group-and-toolbar-placement"></a>Comando predeterminado, el grupo y la ubicación de la barra de herramientas
Uniformidad de producto y la estabilidad, la interfaz de usuario muestra determinados grupos de comandos de forma predeterminada, y [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proporciona definiciones de comandos y grupos de comandos. VSPackages también puede utilizar los comandos estándares y grupos de comandos.  
  
 Los grupos de comandos predeterminados se dividen en tres categorías: IDE comandos, los comandos de producto y los comandos del editor.  
  
## <a name="default-ide-commands"></a>Comandos IDE predeterminada  
 La barra de herramientas IDE predeterminada incluye comandos compartidas por todos los productos incluidos en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Incluye comandos relacionados con operaciones de proyecto genérico, como el **guardar** comando y la **Agregar elemento** comando. VSPackages no debe sumar o restar de esta barra de herramientas, con una excepción: si el producto o el VSPackage agrega una nueva ventana de herramientas, la ventana se debe agregar a la lista de las ventanas de herramientas disponibles en la **vista** menú. Nuevos productos o VSPackages puede agregar su propia barra de herramientas.  
  
## <a name="default-product-commands"></a>Comandos de producto de forma predeterminada  
 Cada producto puede proporcionar el IDE con su propia barra de herramientas predeterminada que contiene importantes y comandos usados con frecuencia. Sin embargo, es mejor, use los menús y barras de herramientas siempre que sea posible existentes y complementarlas con otras barras de herramientas específicas de las tareas según sea necesario.  
  
 El campo de prioridad de una barra de herramientas determina su posición de fila. Prioridad de cero, coloca la barra de herramientas en la tercera fila (fila 3), debajo de la barra de menús (fila 1) y la **estándar** (fila 2) de la barra de herramientas. Por lo tanto, otras barras de herramientas aparecen en la fila (prioridad + 3). Barras de herramientas posteriores se colocan en la misma fila, si hay espacio; en caso contrario, se mueven automáticamente a la siguiente fila.  
  
## <a name="default-editor-commands"></a>Comandos del Editor predeterminado  
 Un VSPackage que proporciona un editor personalizado debe proporcionar una barra de herramientas predeterminada que contiene los más importantes y comandos de uso frecuente en dicho editor. La barra de herramientas del editor debe aparecer cuando el editor está activo y debe estar oculto cuando el editor no está activo. Esta visibilidad se controla en el `VisibilityConstraints Element` del archivo vsct.  
  
 Barras de herramientas del editor se deben colocar por debajo de las barras de herramientas IDE y producto.  
  
## <a name="see-also"></a>Vea también  
 [Grupos, los menús y comandos definidos por el IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [Adición de elementos de la interfaz de usuario por VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)