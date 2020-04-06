---
title: Elemento UsedCommand (Elemento UsedCommand) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65030c3fe24c3456b0c4c99a667362d2a4c67703
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698826"
---
# <a name="usedcommand-element"></a>UsedCommand (Elemento)
Permite que un VSPackage tenga acceso a un comando que se define en otro archivo .vsct. Por ejemplo, si el VSPackage usa el comando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Copy** estándar, definido por el shell, puede agregar el comando a un menú o barra de herramientas sin volver a implementarlo.

## <a name="syntax"></a>Sintaxis

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|guid|Necesario. GUID del par de identificadorGUID que identifica el comando.|
|id|Necesario. El identificador del par de identificadorGUID que identifica el comando.|
|Condición|Opcional. Consulte [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|None||

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[UsedCommands (Elemento)](../extensibility/usedcommands-element.md)|Agrupa los elementos UsedCommand y otras agrupaciones UsedCommands.|

## <a name="remarks"></a>Observaciones
 Al agregar un `<UsedCommands>` comando al elemento, un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage informa al entorno que el VSPackage requiere el comando. Debe agregar `<UsedCommand>` un elemento para cualquier comando que requiera el paquete que podría no incluirse en todas las versiones y configuraciones de Visual Studio. Por ejemplo, si el paquete llama a un comando específico de Visual C++, el comando `<UsedCommand>` no estará disponible para los usuarios de Visual Web Developer a menos que incluya un elemento para el comando.

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
