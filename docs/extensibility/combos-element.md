---
title: Elemento de cuadro combinado | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: ef48d2d2-0c47-4f93-8cfe-52026b6c463e
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2c729f92992ddea109a7024452457bd56d281b89
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="combos-element"></a>Elemento de cuadro combinado
Grupos de [elemento combinado](../extensibility/combo-element.md) elementos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<Combos>  
  <Combo>... </Combo>  
  <Combo>... </Combo>  
</Combos>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|Condición|Opcional. Vea [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Combos (Elemento)](../extensibility/combos-element.md)|Agrupa elementos combinados.|  
|[Combo (Elemento)](../extensibility/combo-element.md)|Define los comandos que aparecen en un cuadro combinado.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Commands (Elemento)](../extensibility/commands-element.md)|Representa la colección de comandos en la barra de herramientas de VSPackage.|  
  
## <a name="example"></a>Ejemplo  
  
```  
<Combos>  
  <Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
    defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    <Strings>  
      <ButtonText>Select Insert Options</ButtonText>  
    </Strings>  
  </Combo>  
  
  <Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
    priority="0x0500" type="DropDownCombo" defaultWidth="100"  
    idCommandList="cmdidGetInsertOptionsList">  
    <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    <Strings>  
      <ButtonText>Select Insert Options</ButtonText>  
    </Strings>  
  </Combo>  
</Combos>  
```  
  
## <a name="see-also"></a>Vea también  
 [¿Cómo VSPackages agregar elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)