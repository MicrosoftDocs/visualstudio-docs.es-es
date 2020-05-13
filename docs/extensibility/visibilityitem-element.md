---
title: Elemento VisibilityItem (Elemento DeLa)//////// Microsoft Docs
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
ms.openlocfilehash: 9129d64e430d661bbdd8f7682e64c93650570211
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698148"
---
# <a name="visibilityitem-element"></a>Elemento VisibilityItem
El `VisibilityItem` elemento determina la visibilidad estática de comandos y barras de herramientas. Cada entrada identifica un comando o menú, y también un contexto de interfaz de usuario de comandos asociado. Visual Studio detecta comandos, menús y barras de herramientas, y su visibilidad, sin cargar los VSPackages que los definen. El IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> utiliza el método para determinar si un contexto de interfaz de usuario de comando está activo.

 Después de cargar el VSPackage, Visual Studio espera que la visibilidad de comandos sea determinada por el VSPackage en lugar de el `VisibilityItem`. Para determinar la visibilidad del comando, <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> puede implementar <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> el controlador de eventos o el método, dependiendo de cómo haya implementado el comando.

 Un comando o menú `VisibilityItem` que tiene un elemento solo aparece cuando el contexto asociado está activo. Puede asociar un único comando, menú o barra de herramientas con uno o varios contextos de interfaz de usuario de comandos incluyendo una entrada para cada combinación de comando-contexto. Si un comando o menú está asociado a varios contextos de interfaz de usuario de comandos, el comando o menú está visible cuando cualquiera de los contextos de interfaz de usuario de comandos asociados está activo.

 El `VisibilityItem` elemento solo se aplica a comandos, menús y barras de herramientas, no a grupos. Un elemento que no `VisibilityItem` tiene un elemento relacionado es visible siempre que su menú primario está activo.

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
|guid|Necesario. Guid del identificador de comando GUID/ID.|
|id|Necesario. El identificador del identificador de comando GUID/ID.|
|context|Necesario. El contexto de la interfaz de usuario en el que está visible el comando.|
|Condición|Opcional. Consulte [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos secundarios
 None

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[VisibilityConstraints elemento](../extensibility/visibilityconstraints-element.md)|El `VisibilityConstraints` elemento determina la visibilidad estática de grupos de comandos y barras de herramientas.|

## <a name="remarks"></a>Observaciones
 Los contextos estándar de la interfaz de usuario de Visual Studio se definen en la *ruta* <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> de instalación del SDK de Visual Studio . En la <xref:Microsoft.VisualStudio.VSConstants> clase se define un conjunto más completo de contextos de interfaz de usuario.

## <a name="example"></a>Ejemplo

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Consulte también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>
- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>
- <xref:Microsoft.VisualStudio.VSConstants>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>
- [VisibilityConstraints elemento](../extensibility/visibilityconstraints-element.md)
- [Tabla de comandos de Visual Studio (. Vsct) Archivos](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
