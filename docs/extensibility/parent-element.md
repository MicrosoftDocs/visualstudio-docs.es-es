---
title: Elemento primario | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c018505ba06762bf8426f266b24ee1835313c29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702225"
---
# <a name="parent-element"></a>Elemento primario
El elemento primario de un botón o un cuadro combinado solo puede ser un grupo. El elemento primario de un menú o grupo puede ser cualquier otro menú o grupo. En un [elemento CommandPlacement](../extensibility/commandplacement-element.md), este elemento es obligatorio; en todas las demás instancias es opcional. Si se omite este elemento, el elemento primario de `Group_Undefined:0` será implícito.

## <a name="syntax"></a>Sintaxis

```xml
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|guid|Necesario. GUID del identificador del comando GUID/ID.|
|id|Necesario. Identificador del identificador del comando GUID/ID.|

### <a name="child-elements"></a>Elementos secundarios
 Ninguno

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos los elementos que representan comandos que un VSPackage proporciona al entorno de desarrollo integrado (IDE). Por ejemplo, elementos de menú, menús, barras de herramientas y cuadros combinados.|
|[Buttons, elemento](../extensibility/buttons-element.md)|Elementos del [elemento Button](../extensibility/button-element.md) de grupos.|
|[Menus (elemento)](../extensibility/menus-element.md)|Define todos los menús que implementa un VSPackage.|
|[Elemento Groups](../extensibility/groups-element.md)|Contiene entradas que definen los grupos de comandos de un VSPackage.|

## <a name="see-also"></a>Consulte también
- [Archivos de tabla de comandos de Visual Studio (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
