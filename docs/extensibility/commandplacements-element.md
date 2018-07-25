---
title: CommandPlacements (elemento) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bbbddf7716b34b8367ac014fa65d8ccfc4413e23
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2018
ms.locfileid: "39230771"
---
# <a name="commandplacements-element"></a>CommandPlacements (elemento)
El elemento CommandPlacements agrupa elementos CommandPlacement y otras agrupaciones CommandPlacements.  
  
 CommandPlacements (elemento) es opcional. Si no hay comandos, grupos o menús deben incluirse en una ubicación secundaria, no es necesario incluir en esta sección en su *.vsct* archivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<CommandPlacements>  
  <CommandPlacement>... </CommandPlacement>  
  <CommandPlacement>... </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|Condición|Opcional. Consulte [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|CommandPlacements|Agrupa los elementos de CommandPlacement y otras agrupaciones CommandPlacements.|  
|[CommandPlacement (elemento)](../extensibility/commandplacement-element.md)|Habilita los botones, grupos y los menús que se incluirán en más de un grupo o menú.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[CommandTable (elemento)](../extensibility/commandtable-element.md)|Define todos los elementos que representan comandos.|  
  
## <a name="example"></a>Ejemplo  
  
```xml  
<CommandPlacements>  
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"  
    priority="0x0300">  
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>  
  </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="see-also"></a>Vea también  
 [CommandPlacement (elemento)](../extensibility/commandplacement-element.md)   
 [Archivos visuales Studio comando table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)