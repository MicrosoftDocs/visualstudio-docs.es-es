---
title: Pautas de colocación de comandos ? Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709568"
---
# <a name="command-placement-guidelines"></a>Directrices de colocación de comandos
Los procedimientos recomendados para colocar comandos en el entorno de desarrollo integrado (IDE) de Visual Studio varían en función del tamaño del conjunto de comandos. Los comandos se definen y colocan de acuerdo con la información de los archivos *.vsct.*

## <a name="best-practices-for-all-command-sets"></a>Prácticas recomendadas para todos los conjuntos de comandos
 Para cada conjunto de comandos, siga estas pautas:

- Prepare un gráfico de la estructura de comandos de antemano. Identifique los comandos, cuadros combinados, grupos de comandos y menús contextuales que se utilizarán en más de una ubicación.

- Los comandos que aparecen en el mismo grupo deben estar relacionados.

- Los grupos que contienen un solo comando son aceptables.

- Los paquetes no deben agregar muchos comandos a los menús existentes de Visual Studio. En su lugar, deben crear menús o submenús para hospedar los nuevos comandos.

- Cuando coloque un comando en un menú existente, asigne un nombre al comando para que su propósito sea claro y no se confunda con los comandos existentes.

## <a name="best-practices-for-small-command-sets"></a>Prácticas recomendadas para conjuntos de comandos pequeños
 Si está desarrollando un VSPackage que tiene solo unos pocos comandos, también siga estas directrices:

- Cuando sea posible, utilice el elemento [Parent](../../extensibility/parent-element.md) de un comando, cuadro combinado, grupo o menú secundario para colocarlo en el grupo adecuado.

- Asigne estos grupos a los menús mostrados por el VSPackage.

- El elemento primario de un menú secundario o un comando debe ser un [Group](../../extensibility/group-element.md) elemento. Asigne comandos y menús secundarios a grupos y, a continuación, asigne los grupos a los menús primarios.

- Puede colocar un comando en grupos adicionales agregando una sección de elemento [CommandPlacements](../../extensibility/commandplacements-element.md) después de la definición del comando y, a continuación, agregando al `CommandPlacements` elemento un elemento [CommandPlacement](../../extensibility/commandplacement-element.md) para cada grupo adicional.

## <a name="best-practices-for-large-command-sets"></a>Prácticas recomendadas para grandes conjuntos de comandos
 Si el VSPackage tendrá muchos comandos que aparecerán en varios contextos, también siga estas directrices:

- Haga menús, grupos y comandos de auto-paternidad. Es decir, no `Parent` asigne un elemento en la definición del elemento.

- Utilice `CommandPlacement` entradas de `CommandPlacements` elementos en la sección de elementos para colocar menús, grupos y comandos en sus menús y grupos primarios.

- En `CommandPlacements` la sección de elementos, las entradas que rellenan un menú o grupo determinado deben estar adyacentes entre sí. Esto ayuda a la `Priority` legibilidad y hace que las clasificaciones sean más fáciles de determinar.

## <a name="see-also"></a>Vea también
- [Cómo VSPackages agregan elementos de interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Archivos de tabla de comandos de Visual Studio (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
