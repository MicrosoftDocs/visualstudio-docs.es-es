---
title: Elemento VisibilityItem | Microsoft Docs
description: El elemento VisibilityItem determina la visibilidad estática de los comandos y las barras de herramientas. Las entradas identifican un comando o menú, y un contexto de interfaz de usuario de comando asociado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 637fea7d203e58c59f85794eeb0f8894eb62e777
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863887"
---
# <a name="visibilityitem-element"></a>Elemento VisibilityItem
El `VisibilityItem` elemento determina la visibilidad estática de los comandos y las barras de herramientas. Cada entrada identifica un comando o menú y también un contexto de interfaz de usuario de comando asociado. Visual Studio detecta comandos, menús y barras de herramientas, así como su visibilidad, sin cargar los VSPackages que los definen. El IDE usa el <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> método para determinar si un contexto de la interfaz de usuario de comandos está activo.

 Una vez cargado el VSPackage, Visual Studio espera que la visibilidad del comando esté determinada por el VSPackage en lugar de `VisibilityItem` . Para determinar la visibilidad del comando, puede implementar el controlador de <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> eventos o el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método, en función de cómo haya implementado el comando.

 Un comando o menú que tiene un `VisibilityItem` elemento solo aparece cuando el contexto asociado está activo. Puede asociar un solo comando, menú o barra de herramientas con uno o más contextos de la interfaz de usuario de comandos si incluye una entrada para cada combinación de contexto de comandos. Si un comando o menú está asociado a varios contextos de la interfaz de usuario de comandos, el comando o el menú es visible cuando uno de los contextos de la interfaz de usuario de comandos asociados está activo.

 El `VisibilityItem` elemento solo se aplica a los comandos, menús y barras de herramientas, no a los grupos. Un elemento que no tiene un elemento relacionado `VisibilityItem` es visible siempre que su menú primario esté activo.

## <a name="syntax"></a>Sintaxis

```xml
<VisibilityItem
  guid ="="cmdGuidMyProductCommands"
  id=="cmdidAddWidget"
  context="guidNotViewSourceMode"/>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|guid|Obligatorio. GUID del identificador del comando GUID/ID.|
|id|Obligatorio. IDENTIFICADOR del identificador del comando GUID/ID.|
|context|Obligatorio. Contexto de la interfaz de usuario en el que el comando está visible.|
|Condición|Opcional. Vea [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos secundarios
 Ninguno

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|El `VisibilityConstraints` elemento determina la visibilidad estática de grupos de comandos y barras de herramientas.|

## <a name="remarks"></a>Comentarios
 Los contextos de la interfaz de usuario de Visual Studio estándar se definen en el archivo \VisualStudioIntegration\Common\Inc\vsshlids.h de *ruta de instalación del SDK de Visual Studio*, así como en las <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> clases y. En la clase se define un conjunto más completo de contextos de la interfaz de usuario <xref:Microsoft.VisualStudio.VSConstants> .

## <a name="example"></a>Ejemplo

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Consulte también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>
- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>
- <xref:Microsoft.VisualStudio.VSConstants>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>
- [Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)
- [Tabla de comandos de Visual Studio (. Archivos de Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
