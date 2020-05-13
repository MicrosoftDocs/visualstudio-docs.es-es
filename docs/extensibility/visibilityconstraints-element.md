---
title: Elemento VisibilityConstraints (VisibilityConstraints Element) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1aaa9573b883910ac6fa5d921a9bc79ce1c1cf3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698189"
---
# <a name="visibilityconstraints-element"></a>VisibilityConstraints elemento
El elemento VisibilityConstraints determina la visibilidad estática de grupos de comandos y barras de herramientas. La visibilidad se controla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] primero mediante el entorno de desarrollo integrado (IDE) sin cargar el VSPackage.

## <a name="syntax"></a>Sintaxis

```xml
<VisibilityConstraints>
  <VisibilityItem />
  <VisibilityItem />
</VisibilityConstraints>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|Condición|Opcional. Consulte [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento VisibilityItem](../extensibility/visibilityitem-element.md)|Determina la visibilidad estática de comandos y barras de herramientas.|
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Determina la visibilidad estática de grupos de comandos y barras de herramientas.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos los elementos que representan los comandos (por ejemplo, elementos de menú, menús, barras de herramientas y cuadros combinados) que un VSPackage proporciona al IDE.|

## <a name="example"></a>Ejemplo

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Consulte también
- [Elemento VisibilityItem](../extensibility/visibilityitem-element.md)
- [Tabla de comandos de Visual Studio (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
