---
title: Orientaciones para la colocación de comandos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c04ea981fc190b2e0074e767e086303e6950f2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62861671"
---
# <a name="command-placement-guidelines"></a>Instrucciones de selección de ubicación de comando
Procedimientos recomendados para la colocación de comandos en el entorno de desarrollo integrado (IDE) de Visual Studio varían según el tamaño del conjunto de comandos. Los comandos se definen y se coloca según la información de *.vsct* archivos.

## <a name="best-practices-for-all-command-sets"></a>Procedimientos recomendados para todos los conjuntos de comandos
 Para cada conjunto de comandos, siga estas instrucciones:

- Preparar de antemano un gráfico de la estructura del comando. Identificar los comandos, los cuadros combinados, grupos de comandos y menús contextuales que se usará en más de una ubicación.

- Deben estar relacionado con los comandos que aparecen en el mismo grupo.

- Los grupos que contienen un solo comando son aceptables.

- Los paquetes no deben agregar una gran cantidad de comandos a menús existentes de Visual Studio. En su lugar, deben crear menús o submenús para alojar los nuevos comandos.

- Cuando se coloca un comando en un menú existente, el nombre del comando para que su finalidad sea clara y no confundir con los comandos existentes.

## <a name="best-practices-for-small-command-sets"></a>Procedimientos recomendados para los conjuntos de comandos pequeño
 Si está desarrollando un VSPackage que tenga solo unos comandos, también siga estas instrucciones:

- Cuando sea posible, use el [primario](../../extensibility/parent-element.md) elemento de un comando, cuadro combinado, grupo o menú secundario para colocarla en el grupo adecuado.

- Asigne a estos grupos a los menús mostrados por el VSPackage.

- El elemento primario de un menú secundario o un comando debe ser un [grupo](../../extensibility/group-element.md) elemento. Asignar comandos y los menús secundarios a grupos y, a continuación, asignar a los grupos a los menús primarios.

- Puede colocar un comando en grupos adicionales mediante la adición de un [CommandPlacements](../../extensibility/commandplacements-element.md) sección del elemento después de la definición del comando y, a continuación, agregar a la `CommandPlacements` elemento un [CommandPlacement](../../extensibility/commandplacement-element.md) elemento para cada grupo adicional.

## <a name="best-practices-for-large-command-sets"></a>Procedimientos recomendados para los conjuntos de comandos de gran tamaño
 Si el paquete de VS tendrá muchos comandos que va a aparecer en varios contextos, también siga estas instrucciones:

- Asegúrese de menús, grupos y comandos automáticamente relaciones jerárquicas. Es decir, no asigne un `Parent` elemento de la definición del elemento.

- Use `CommandPlacement` entradas de elemento en el `CommandPlacements` colocar menús, grupos y comandos en sus los menús primarios y los grupos de sección del elemento.

- En la `CommandPlacements` sección del elemento, las entradas que rellenan un menú determinado o un grupo deben ser adyacentes entre sí. Esto ayuda a mejorar la legibilidad y hace que el `Priority` clasificaciones determinar con facilidad.

## <a name="see-also"></a>Vea también
- [Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Archivos visuales Studio comando table (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)