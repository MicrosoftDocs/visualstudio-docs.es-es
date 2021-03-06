---
title: Elemento UsedCommands | Microsoft Docs
description: Los elementos UsedCommands agrupan elementos UsedCommand y otras agrupaciones UsedCommands. El elemento UsedCommands es opcional.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UsedCommands
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 5e000ee0-a919-46e9-9277-2a0659f1eb78
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 21233527c9fcfb97fd45a8eeed60c04927df8ba1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903039"
---
# <a name="usedcommands-element"></a>UsedCommands (Elemento)
Los elementos UsedCommands agrupan elementos UsedCommand y otras agrupaciones UsedCommands.

 El elemento UsedCommands es opcional. Si no llama a comandos definidos fuera del paquete, no tiene que incluir esta sección en el archivo .vsct.

## <a name="syntax"></a>Sintaxis

```
<UsedCommands condition="Defined(DEBUG)">
  <UsedCommand ... />
</UsedCommands>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|Condición|Opcional. Vea [Atributos condicionales.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[UsedCommand (Elemento)](../extensibility/usedcommand-element.md)|Comando que implementa otro código.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[CommandTable (Elemento)](../extensibility/commandtable-element.md)|Define todos los elementos que representan comandos (por ejemplo, elementos de menú, menús, barras de herramientas y cuadros combinados) que un VSPackage proporciona al entorno de desarrollo integrado (IDE).|

## <a name="example"></a>Ejemplo

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>Consulte también
- [UsedCommand (Elemento)](../extensibility/usedcommand-element.md)
- [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
