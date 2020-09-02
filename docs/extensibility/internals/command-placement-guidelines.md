---
title: Instrucciones de selección de ubicación de comandos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 021a5fd9f9931e3041a431d211c8ab49978bbbab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709568"
---
# <a name="command-placement-guidelines"></a>Instrucciones de selección de ubicación de comandos
Los procedimientos recomendados para colocar comandos en el entorno de desarrollo integrado (IDE) de Visual Studio varían según el tamaño del conjunto de comandos. Los comandos se definen y se colocan según la información de los archivos *. Vsct* .

## <a name="best-practices-for-all-command-sets"></a>Prácticas recomendadas para todos los conjuntos de comandos
 Para cada conjunto de comandos, siga estas instrucciones:

- Preparar un gráfico de la estructura de comandos de antemano. Identifique los comandos, cuadros combinados, grupos de comandos y menús contextuales que se usarán en más de una ubicación.

- Los comandos que aparecen en el mismo grupo deben estar relacionados.

- Los grupos que contienen un solo comando son aceptables.

- Los paquetes no deben agregar muchos comandos a los menús existentes de Visual Studio. En su lugar, deben crear menús o submenús para hospedar los nuevos comandos.

- Al colocar un comando en un menú existente, asigne un nombre al comando para que su finalidad sea clara y no se confunde con los comandos existentes.

## <a name="best-practices-for-small-command-sets"></a>Prácticas recomendadas para conjuntos de comandos pequeños
 Si va a desarrollar un VSPackage que tiene solo algunos comandos, siga estas instrucciones:

- Cuando sea posible, use el elemento [primario](../../extensibility/parent-element.md) de un comando, un cuadro combinado, un grupo o un menú secundario para colocarlo en el grupo adecuado.

- Asigne estos grupos a los menús que muestra el VSPackage.

- El elemento primario de un menú secundario o un comando debe ser un elemento de [Grupo](../../extensibility/group-element.md) . Asigne comandos y menús secundarios a grupos y, a continuación, asigne los grupos a los menús primarios.

- Puede colocar un comando en grupos adicionales agregando una sección del elemento [CommandPlacements](../../extensibility/commandplacements-element.md) después de la definición del comando y, a continuación, agregando al `CommandPlacements` elemento un elemento [CommandPlacement](../../extensibility/commandplacement-element.md) para cada grupo adicional.

## <a name="best-practices-for-large-command-sets"></a>Prácticas recomendadas para conjuntos de comandos grandes
 Si el VSPackage tendrá muchos comandos que aparecerán en varios contextos, siga estas instrucciones:

- Haga que los menús, los grupos y los comandos se autopadres. Es decir, no asigne un `Parent` elemento en la definición del elemento.

- Use `CommandPlacement` las entradas de elementos de la `CommandPlacements` sección de elementos para colocar menús, grupos y comandos en los menús y grupos principales.

- En la `CommandPlacements` sección elemento, las entradas que rellenan un menú o grupo determinado deben ser adyacentes entre sí. Esto ayuda a facilitar la lectura y facilita la determinación de las `Priority` clasificaciones.

## <a name="see-also"></a>Consulte también
- [Cómo agrega VSPackages los elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Archivos de tabla de comandos de Visual Studio (. Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
