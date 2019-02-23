---
title: Elemento primario | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7220e435090cc688d32a2d6d26917a8c05510d4f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56687918"
---
# <a name="parent-element"></a>Elemento primario
El elemento primario de un cuadro combinado o botón sólo puede ser un grupo. El elemento primario de un menú o un grupo puede ser cualquier otro grupo o menú. En un [CommandPlacement (elemento)](../extensibility/commandplacement-element.md), este elemento es necesario; en todas las demás instancias es opcional. Si se omite este elemento, el elemento primario de `Group_Undefined:0` se implicarse.

## <a name="syntax"></a>Sintaxis

```xml
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|guid|Obligatorio. Identificador de comando de GUID o identificador de GUID.|
|id|Obligatorio. Id. de GUID/ID el identificador de comando.|

### <a name="child-elements"></a>Elementos secundarios
 Ninguna

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[CommandTable (elemento)](../extensibility/commandtable-element.md)|Define todos los elementos que representan los comandos que un paquete VSPackage proporciona al entorno de desarrollo integrado (IDE). Por ejemplo, los elementos de menú, menús, barras de herramientas y cuadros combinados.|
|[Buttons (elemento)](../extensibility/buttons-element.md)|Grupos [elemento Button](../extensibility/button-element.md) elementos.|
|[Menus (elemento)](../extensibility/menus-element.md)|Define todos los menús que implementa un paquete VSPackage.|
|[Elemento Groups](../extensibility/groups-element.md)|Contiene entradas que definen los grupos de comandos de un paquete VSPackage.|

## <a name="see-also"></a>Vea también
- [Archivos visuales Studio comando table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)