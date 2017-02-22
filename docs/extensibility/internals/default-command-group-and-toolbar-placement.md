---
title: "Comando predeterminado, el grupo y la ubicaci&#243;n de la barra de herramientas | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "comandos [Visual Studio], grupos predeterminados"
  - "barras de herramientas [Visual Studio], de forma predeterminada"
  - "comandos [Visual Studio], editor predeterminado"
  - "grupos de comandos"
  - "comandos [Visual Studio], IDE predeterminado"
  - "comandos [Visual Studio], el producto de forma predeterminada"
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
caps.latest.revision: 30
caps.handback.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
---
# Comando predeterminado, el grupo y la ubicaci&#243;n de la barra de herramientas
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Uniformidad de producto y la estabilidad, la interfaz de usuario muestra determinados grupos de comandos de forma predeterminada, y [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proporciona definiciones para los comandos y los grupos de comandos. VSPackages también puede utilizar los comandos estándar y los grupos de comandos.  
  
 Los grupos de comandos predeterminados se dividen en tres categorías: IDE de comandos, los comandos de producto y los comandos del editor.  
  
## Comandos IDE predeterminada  
 La barra de herramientas IDE predeterminada incluye comandos compartidas por todos los productos incluidos en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Incluye comandos relacionados con operaciones de proyectos genérico, como el **Guardar** comando y el **Agregar elemento** comando. VSPackages no debe sumar o restar de esta barra de herramientas, con una excepción: si el producto o VSPackage agrega una nueva ventana de herramientas, la ventana se debe agregar a la lista de ventanas de herramientas disponibles en la **vista** menú. Nuevos productos o VSPackages puede agregar su propia barra de herramientas.  
  
## Comandos de producto predeterminados  
 Cada producto puede proporcionar el IDE con su propia barra de herramientas predeterminada que contiene importantes y comandos usados con frecuencia. Sin embargo, es mejor, use los menús y barras de herramientas siempre que sea posible existentes y complementarlas con otras barras de herramientas específicas de las tareas según sea necesario.  
  
 El campo de prioridad de una barra de herramientas determina su posición de fila. Prioridad de cero coloca la barra de herramientas en la tercera fila \(fila 3\), debajo de la barra de menús \(fila 1\) y la **estándar** \(fila 2\) de la barra de herramientas. Por lo tanto, otras barras de herramientas aparecen en la fila \(prioridad \+ 3\). Barras de herramientas posteriores se colocan en la misma fila, si hay espacio; de lo contrario, se mueven automáticamente a la siguiente fila.  
  
## Comandos del Editor predeterminado  
 Un VSPackage que proporciona un editor personalizado debe proporcionar una barra de herramientas predeterminada que contiene más importantes y comandos usados con frecuencia en ese editor. Debe aparecer la barra de herramientas del editor cuando el editor está activo y debe estar oculto cuando el editor no está activo. Esta visibilidad se controla en el `VisibilityConstraints Element` del archivo vsct.  
  
 Barras de herramientas del editor se deben colocar por debajo de las barras de herramientas IDE y producto.  
  
## Vea también  
 [Grupos, menús y comandos definidos por el IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)