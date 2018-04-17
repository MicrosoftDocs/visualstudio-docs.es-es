---
title: Instrucciones de selección de ubicación de comando | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c406a5a34ea2556d367c8f7af8a9fda70fcc2676
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="command-placement-guidelines"></a>Instrucciones de selección de ubicación de comando
Prácticas recomendadas para la colocación de comandos en el entorno de desarrollo integrado (IDE) de Visual Studio varían según el tamaño del conjunto de comandos. Comandos se definen y se sitúa de acuerdo con la información de archivos de vsct.  
  
## <a name="best-practices-for-all-command-sets"></a>Prácticas recomendadas para todos los conjuntos de comandos  
 Para cada conjunto de comandos, siga estas instrucciones:  
  
-   Preparar un gráfico de la estructura del comando de antemano. Identificar los comandos, cuadros combinados, grupos de comandos y menús contextuales que se usará en más de una ubicación.  
  
-   Deben estar relacionado con los comandos que aparecen en el mismo grupo.  
  
-   Grupos que contienen un solo comando son aceptables.  
  
-   Paquetes no deben agregar una gran cantidad de comandos a menús de Visual Studio existentes. En su lugar, deben crear menús o submenús para hospedar los nuevos comandos.  
  
-   Cuando coloca un comando en un menú existente, el nombre del comando para que se desactive su propósito y no confundirse con los comandos existentes.  
  
## <a name="best-practices-for-small-command-sets"></a>Prácticas recomendadas para conjuntos de comandos pequeño  
 Si está desarrollando un VSPackage que tiene unos pocos comandos, seguir estas directrices:  
  
-   Cuando sea posible, use la [elemento primario](../../extensibility/parent-element.md) de un comando, el cuadro combinado, el grupo o el menú secundario para colocarla en el grupo adecuado.  
  
-   Asignar a estos grupos a los menús mostrados por el VSPackage.  
  
-   El elemento primario de un menú secundario o un comando debe ser un [elemento Group](../../extensibility/group-element.md). Asignar comandos y menús secundarios a grupos y, a continuación, asignar a los grupos a los menús primarios.  
  
-   Puede colocar un comando en grupos adicionales mediante la adición de un [CommandPlacements elemento](../../extensibility/commandplacements-element.md) sección después de la definición del comando y, a continuación, agregar a la `CommandPlacements Element` una [CommandPlacement elemento](../../extensibility/commandplacement-element.md) para cada uno grupo adicional.  
  
## <a name="best-practices-for-large-command-sets"></a>Prácticas recomendadas para conjuntos de comandos de gran tamaño  
 Si el paquete de VS tendrá muchos comandos que va a aparecer en varios contextos, seguir estas directrices:  
  
-   Asegúrese de menús, los grupos y los comandos automáticamente relaciones jerárquicas. Es decir, no asigne un `Parent Element` en la definición del elemento.  
  
-   Use `CommandPlacement Element` entradas en la `CommandPlacements Element` sección para colocar los menús, los grupos y los comandos en los archivos y grupos de menús principal.  
  
-   En la `CommandPlacements` sección, las entradas que rellenan un menú determinado o grupo debe ser adyacente entre sí. Esto ayuda a mejorar la legibilidad y hace el `Priority` clasificaciones más fáciles de determinar.  
  
## <a name="see-also"></a>Vea también  
 [¿Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)