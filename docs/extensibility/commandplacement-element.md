---
title: Elemento CommandPlacement (Elemento CommandPlacement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcf9f23b5e860b895baa4c2a7a783f2ee15fcc77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739736"
---
# <a name="commandplacement-element"></a>Elemento CommandPlacement
El elemento CommandPlacement permite incluir botones, grupos y menús en más de un grupo o menú. Mediante el uso de la CommandPlacement elemento, no es necesario redefinir completamente estos elementos para modificar el aspecto de una interfaz de usuario.

 Para obtener más información, consulte [Crear grupos de botones reutilizables.](../extensibility/creating-reusable-groups-of-buttons.md)

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
|guid|Necesario. El guid del conjunto de [comandos,](../extensibility/symbols-element.md)tal como se define en el elemento Símbolos .|
|id|Necesario. El identificador del menú, grupo o comando que se `Symbols Element`va a colocar, tal como se define en el archivo .|
|priority|Necesario. Determina la posición visual del elemento en su elemento primario.|
|Condición|Opcional. Consulte [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|Parent|Necesario. El menú o grupo que hospeda el elemento que se va a colocar.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CommandPlacements](../extensibility/commandplacements-element.md)|Especifica grupos de CommandPlacements y CommandPlacement elementos.|

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
- [Archivos de tabla de comandos de Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
