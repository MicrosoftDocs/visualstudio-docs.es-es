---
title: Elemento CommandPlacement | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14f28c8e2758d2dde9cf38db268abc9fa9b4f863
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="commandplacement-element"></a>Elemento CommandPlacement
El elemento CommandPlacement habilita botones, grupos y menús que se incluirá en más de un grupo o un menú. Mediante el elemento de CommandPlacement, es necesario volver a definir completamente estos elementos con el fin de modificar la apariencia de una interfaz de usuario.  
  
 Para obtener más información, consulte [crear grupos de reutilizable de botones](../extensibility/creating-reusable-groups-of-buttons.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<CommandPlacement guid=guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|guid|Requerido. El guid del conjunto de comandos, tal como se define en el [símbolos elemento](../extensibility/symbols-element.md).|  
|id|Requerido. El identificador del menú, grupo o comando para colocarse, tal como se define en el `Symbols Element`.|  
|priority|Requerido. Determina la posición del elemento visual de su elemento primario.|  
|Condición|Opcional. Vea [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|Elemento primario|Requerido. El menú o el grupo que hospeda el elemento que se va a colocar.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[CommandPlacements (Elemento)](../extensibility/commandplacements-element.md)|Especifica los grupos de elementos CommandPlacements y CommandPlacement.|  
  
## <a name="example"></a>Ejemplo  
  
```  
<CommandPlacements>  
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"  
    priority="0x0300">  
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>  
  </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="see-also"></a>Vea también  
 [Elemento CommandPlacements](../extensibility/commandplacements-element.md)   
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)