---
title: Elemento UsedCommand | Microsoft Docs
description: El elemento UsedCommand permite que un VSPackage acceda a un comando definido en otro archivo .vsct.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9d120353b9d6191bfcaae38151eb970ab1071b99
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903052"
---
# <a name="usedcommand-element"></a>UsedCommand (Elemento)
Permite que un VSPackage acceda a un comando definido en otro archivo .vsct. Por ejemplo, si el VSPackage usa el comando Copy estándar, que se define mediante el shell, puede agregar el comando a un menú o barra de herramientas sin volver a  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] implementarlo.

## <a name="syntax"></a>Sintaxis

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|guid|Necesario. GUID del par de identificadores GUID que identifica el comando.|
|id|Necesario. Identificador del par de identificadores GUID que identifica el comando.|
|Condición|Opcional. Vea [Atributos condicionales.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|Ninguno||

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[UsedCommands (Elemento)](../extensibility/usedcommands-element.md)|Agrupa elementos UsedCommand y otras agrupaciones UsedCommands.|

## <a name="remarks"></a>Observaciones
 Al agregar un comando al elemento , un VSPackage informa al `<UsedCommands>` entorno de que el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage requiere el comando . Debe agregar un elemento para cualquier comando que requiera el paquete que podría no incluirse en todas las versiones y `<UsedCommand>` configuraciones de Visual Studio. Por ejemplo, si el paquete llama a un comando específico de Visual C++, el comando no estará disponible para los usuarios de Visual Web Developer a menos que incluya un elemento para `<UsedCommand>` el comando.

## <a name="example"></a>Ejemplo

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>Consulte también
- [UsedCommands (Elemento)](../extensibility/usedcommands-element.md)
- [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
