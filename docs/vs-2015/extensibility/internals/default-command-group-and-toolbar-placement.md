---
title: Predeterminado de comando, grupo y la ubicación de la barra de herramientas | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
caps.latest.revision: 31
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fb7144842cba237a11d94435f56782a8d2de90b6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49195746"
---
# <a name="default-command-group-and-toolbar-placement"></a>Ubicación predeterminada de comando, grupo y barra de herramientas
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Para obtener uniformidad de producto y estabilidad, la interfaz de usuario muestra determinados grupos de comandos de forma predeterminada, y [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] proporciona definiciones para los comandos y los grupos de comandos. Los VSPackages también puede usar los comandos estándar y los grupos de comandos.  
  
 Los grupos de comandos predeterminados se dividen en tres categorías: IDE comandos, comandos de producto y los comandos del editor.  
  
## <a name="default-ide-commands"></a>Comandos IDE predeterminados  
 La barra de herramientas IDE predeterminada incluye comandos compartidos por todos los productos incluidos en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Incluye comandos relacionados con operaciones de proyectos genérico, como el **guardar** comando y el **Agregar elemento** comando. Los VSPackages no debe sumar o restar de esta barra de herramientas, con una excepción: si el producto o VSPackage agrega una nueva ventana de herramientas, la ventana se agregan a la lista de ventanas de herramientas disponibles en el **vista** menú. Nuevos productos o los paquetes VSPackage pueden agregar su propia barra de herramientas.  
  
## <a name="default-product-commands"></a>Comandos de producto de forma predeterminada  
 Cada producto puede proporcionar el IDE con su propia barra de herramientas predeterminada que contiene importantes y comandos usados con frecuencia. Sin embargo, es mejor, usar los menús y barras de herramientas siempre que sea posible existentes y complementarlas con otras barras de herramientas específicas de las tareas según sea necesario.  
  
 El campo prioridad para una barra de herramientas determina su posición de fila. Prioridad de cero, coloca la barra de herramientas en la tercera fila (fila 3), debajo de la barra de menús (fila 1) y el **estándar** (fila 2) de la barra de herramientas. Por lo tanto, otras barras de herramientas aparecen en la fila (prioridad + 3). Las barras de herramientas posteriores se colocan en la misma fila, si hay espacio; en caso contrario, se mueven automáticamente a la siguiente fila.  
  
## <a name="default-editor-commands"></a>Comandos del Editor predeterminado  
 Un VSPackage que proporciona un editor personalizado debe proporcionar una barra de herramientas predeterminada que contiene las más importantes y comandos usados con frecuencia en ese editor. Debería aparecer la barra de herramientas del editor cuando el editor está activo y debe estar oculto cuando el editor no está activo. Esta visibilidad se controla en el `VisibilityConstraints Element` del archivo .vsct.  
  
 Las barras de herramientas del editor se deben colocar por debajo de las barras de herramientas IDE y producto.  
  
## <a name="see-also"></a>Vea también  
 [Grupos, menús y comandos definidos por el IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [Adición de elementos de la interfaz de usuario por VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

