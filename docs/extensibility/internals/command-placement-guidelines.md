---
title: "Instrucciones de selecci&#243;n de ubicaci&#243;n de comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "comandos, conjuntos de comandos pequeño"
  - "conjuntos de comandos pequeño"
  - "conjuntos de comandos"
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
caps.latest.revision: 28
caps.handback.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
---
# Instrucciones de selecci&#243;n de ubicaci&#243;n de comando
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Prácticas recomendadas para colocar los comandos en el entorno de desarrollo integrado \(IDE\) de Visual Studio varían dependiendo del tamaño del conjunto de comandos. Comandos se definen y se sitúa de acuerdo con la información de los archivos .vsct.  
  
## Prácticas recomendadas para todos los conjuntos de comandos  
 Para cada conjunto de comandos, siga estas instrucciones:  
  
-   Preparar de antemano un gráfico de la estructura del comando. Identificar los comandos, cuadros combinados, grupos de comandos y menús contextuales que se usará en más de una ubicación.  
  
-   Deben estar relacionado con los comandos que aparecen en el mismo grupo.  
  
-   Grupos que contienen un solo comando son aceptables.  
  
-   Paquetes no deben agregar muchos comandos a menús existentes de Visual Studio. En su lugar, deben crear menús o submenús para alojar los nuevos comandos.  
  
-   Cuando coloca un comando en un menú existente, el nombre del comando para que su objetivo es clara y no se confundirá con los comandos existentes.  
  
## Prácticas recomendadas para conjuntos de comandos pequeño  
 Si está desarrollando un VSPackage que tenga algunos comandos, también, siga estas directrices:  
  
-   Cuando sea posible, use la [Elemento Parent](../../extensibility/parent-element.md) de un comando, el cuadro combinado, el grupo o el menú secundario para colocarla en el grupo adecuado.  
  
-   Asignar a estos grupos a los menús mostrados por el VSPackage.  
  
-   El elemento primario de un menú secundario o un comando debe ser un [Elemento Group](../../extensibility/group-element.md). Asignar comandos y menús secundarios a grupos y, a continuación, asignar a los grupos a los menús primarios.  
  
-   Puede colocar un comando en grupos adicionales mediante la adición de un [Elemento CommandPlacements](../../extensibility/commandplacements-element.md) sección después de la definición del comando y, a continuación, agregar a la `CommandPlacements Element` un [Elemento CommandPlacement](../../extensibility/commandplacement-element.md) para cada grupo adicional.  
  
## Prácticas recomendadas para conjuntos de comandos de gran tamaño  
 Si su VSPackage tendrá muchos de los comandos que aparecen en varios contextos, también, siga estas directrices:  
  
-   Asegúrese de menús, grupos y comandos automáticamente relaciones jerárquicas. Es decir, no asigne un `Parent Element` en la definición del elemento.  
  
-   Use `CommandPlacement Element` entradas en la `CommandPlacements Element` sección para poner en sus menús primarios y los grupos de menús, grupos y comandos.  
  
-   En la `CommandPlacements` sección, las entradas que rellenan un menú determinado o de grupo debe ser adyacente entre sí. Esto ayuda a mejorar la legibilidad y hace que el `Priority` clasificaciones más fáciles de determinar.  
  
## Vea también  
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)