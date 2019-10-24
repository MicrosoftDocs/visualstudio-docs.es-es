---
title: Elemento UsedCommand | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44ea8f27cafb166968f66c53dc68398526e0aa5d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718771"
---
# <a name="usedcommand-element"></a>UsedCommand (Elemento)
Permite a un VSPackage obtener acceso a un comando que se define en otro archivo. Vsct. Por ejemplo, si el VSPackage usa el comando **Copy** estándar, que se define en el shell de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], puede Agregar el comando a un menú o barra de herramientas sin volver a implementarlo.

## <a name="syntax"></a>Sintaxis

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|guid|Requerido. GUID del par de IDENTIFICADOres GUID que identifica el comando.|
|identificador|Requerido. IDENTIFICADOR del par de IDENTIFICADOres GUID que identifica el comando.|
|Condición|Opcional. Vea [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|Ninguno||

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[UsedCommands (Elemento)](../extensibility/usedcommands-element.md)|Agrupa los elementos UsedCommand y otras agrupaciones UsedCommands.|

## <a name="remarks"></a>Comentarios
 Al agregar un comando al elemento `<UsedCommands>`, un VSPackage informa al entorno [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que el VSPackage requiere el comando. Debe agregar un elemento `<UsedCommand>` para cualquier comando que el paquete requiera y que no esté incluido en todas las versiones y configuraciones de Visual Studio. Por ejemplo, si el paquete llama a un comando que es específico de C++visual, el comando no estará disponible para los usuarios de Visual Web Developer a menos que incluya un elemento `<UsedCommand>` para el comando.

## <a name="example"></a>Ejemplo

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>Vea también
- [UsedCommands (Elemento)](../extensibility/usedcommands-element.md)
- [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)