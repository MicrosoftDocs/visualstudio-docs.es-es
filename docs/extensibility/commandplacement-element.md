---
title: Elemento CommandPlacement | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 71a53dfcb7ae7cca5b360d2e115c34909ca32f86
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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
|guid|Obligatorio. El guid del conjunto de comandos, tal como se define en el [símbolos elemento](../extensibility/symbols-element.md).|  
|id|Obligatorio. El identificador del menú, grupo o comando para colocarse, tal como se define en el `Symbols Element`.|  
|priority|Obligatorio. Determina la posición del elemento visual de su elemento primario.|  
|Condición|Opcional. Vea [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|Elemento primario|Obligatorio. El menú o el grupo que hospeda el elemento que se va a colocar.|  
  
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