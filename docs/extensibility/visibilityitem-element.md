---
title: Elemento VisibilityItem | Microsoft Docs
description: El elemento VisibilityItem determina la visibilidad estática de los comandos y las barras de herramientas. Las entradas identifican un comando o menú y un contexto de interfaz de usuario de comando asociado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 025e05dd0346c7da0a70985aa579d1673f2ffcaa
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905441"
---
# <a name="visibilityitem-element"></a>Elemento VisibilityItem
El `VisibilityItem` elemento determina la visibilidad estática de los comandos y las barras de herramientas. Cada entrada identifica un comando o un menú, así como un contexto de interfaz de usuario de comandos asociado. Visual Studio detecta comandos, menús y barras de herramientas, y su visibilidad, sin cargar los VSPackages que los definen. El IDE usa el método para determinar si un contexto de interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> usuario de comando está activo.

 Una vez cargado el VSPackage, Visual Studio espera que la visibilidad del comando la determine el VSPackage en lugar de `VisibilityItem` . Para determinar la visibilidad del comando, puede implementar el controlador de eventos o el método , en función de cómo <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> haya implementado el comando.

 Un comando o menú que tiene `VisibilityItem` un elemento solo aparece cuando el contexto asociado está activo. Puede asociar un único comando, menú o barra de herramientas con uno o varios contextos de interfaz de usuario de comandos mediante la inclusión de una entrada para cada combinación de comandos y contexto. Si un comando o menú está asociado a varios contextos de interfaz de usuario de comandos, el comando o menú está visible cuando cualquiera de los contextos de interfaz de usuario de comandos asociados está activo.

 El `VisibilityItem` elemento solo se aplica a comandos, menús y barras de herramientas, no a grupos. Un elemento que no tiene un elemento relacionado está `VisibilityItem` visible cada vez que su menú primario está activo.

## <a name="syntax"></a>Sintaxis

```xml
<VisibilityItem
  guid="cmdGuidMyProductCommands"
  id="cmdidAddWidget"
  context="guidNotViewSourceMode"/>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|guid|Necesario. GUID del identificador de comando GUID/ID.|
|id|Necesario. Identificador del identificador del comando GUID/ID.|
|context|Necesario. Contexto de la interfaz de usuario en el que está visible el comando.|
|Condición|Opcional. Vea [Atributos condicionales.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Elementos secundarios
 Ninguno

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|El `VisibilityConstraints` elemento determina la visibilidad estática de los grupos de comandos y barras de herramientas.|

## <a name="remarks"></a>Observaciones
 Los contextos Visual Studio de interfaz de usuario estándar se definen en la ruta de instalación del SDK de *Visual Studio*\VisualStudioIntegration\Common\Inc\vsshlids.h, así como en las clases <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> y <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> . En la clase se define un conjunto más completo de contextos de interfaz de <xref:Microsoft.VisualStudio.VSConstants> usuario.

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
- [Visual Studio tabla de comandos (. Vsct) Archivos](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
