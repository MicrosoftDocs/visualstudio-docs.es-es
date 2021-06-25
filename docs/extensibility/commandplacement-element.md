---
title: Elemento CommandPlacement | Microsoft Docs
description: El elemento CommandPlacement permite incluir botones, grupos y menús en más de un grupo o menú.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 69be89fb2773be9de632b8059cf217303daaede7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901999"
---
# <a name="commandplacement-element"></a>Elemento CommandPlacement
El elemento CommandPlacement permite incluir botones, grupos y menús en más de un grupo o menú. Mediante el uso del elemento CommandPlacement, no es necesario volver a definir completamente estos elementos para modificar la apariencia de una interfaz de usuario.

 Para obtener más información, vea [Crear grupos reutilizables de botones.](../extensibility/creating-reusable-groups-of-buttons.md)

## <a name="syntax"></a>Sintaxis

```
<CommandPlacement guid="guidMyCommandSet" id="MyCommand" priority="0x001" >
  <Parent>... </Parent>
</CommandPlacement>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|guid|Necesario. Guid del conjunto de comandos, tal como se define en el [elemento Symbols](../extensibility/symbols-element.md).|
|id|Necesario. Identificador del menú, grupo o comando que se va a colocar, tal como se define en `Symbols Element` .|
|priority|Necesario. Determina la posición visual del elemento en su elemento primario.|
|Condición|Opcional. Vea [Aattributes condicionales.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|Parent|Necesario. Menú o grupo que hospeda el elemento que se va a colocar.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CommandPlacements](../extensibility/commandplacements-element.md)|Especifica grupos de elementos CommandPlacements y CommandPlacement.|

## <a name="example"></a>Ejemplo

```
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>Consulte también
- [Elemento CommandPlacements](../extensibility/commandplacements-element.md)
- [Visual Studio archivos de tabla de comandos (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
