---
title: Elemento combinado | Documentos de Microsoft
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
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f170efc945f92d13eda61830ef682ab4cd8fc755
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="combo-element"></a>Elemento combinado
Define los comandos que aparecen en un cuadro combinado. Hay cuatro tipos de cuadros combinados, como se indica a continuación: cuadro combinado desplegable, DynamicCombo, IndexCombo y MRUCombo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">  
  <Parent>... </Parent  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</combo>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|guid|Obligatorio. GUID del identificador de comando/identificador GUID.|  
|id|Obligatorio. Id. del identificador de comando/identificador GUID.|  
|defaultWidth|Obligatorio. Un entero que especifica un ancho en píxeles del cuadro combinado.|  
|idCommandList|Obligatorio. Un identificador que se envía al destino de comando active para recuperar la lista de elementos que deben mostrarse en el cuadro combinado. El identificador estará en el mismo ámbito GUID que el control.|  
|priority|Opcional. Un valor numérico que especifica la prioridad.|  
|type|Opcional. Un valor enumerado que especifica el tipo de botón.<br /><br /> Si no se proporcionan, utiliza el botón.<br /><br /> Cuadro combinado desplegable<br /> El VSPackage es responsable de rellenar el contenido de este cuadro combinado. El usuario no puede escribir nada en el cuadro de texto de desplegable este.<br /><br /> DynamicCombo<br /> El VSPackage es responsable de rellenar el contenido de este cuadro combinado. El usuario puede editar a este combinado y seleccionar elementos en él.<br /><br /> IndexCombo<br /> Igual que DynamicCombo excepto en que genera el índice del elemento en lugar de su texto.<br /><br /> MRUCombo<br /> Rellena el entorno de desarrollo integrado (IDE) en nombre de VSPackage.  El usuario puede editar en este cuadro combinado. El IDE recuerda hasta las últimas 16 entradas por cuadro combinado.<br /><br /> Cuando el usuario selecciona algo en el cuadro combinado, o especifica algo nuevo, el IDE notifica a VSPackage adecuado.|  
|Condición|Opcional. Vea [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|Elemento primario|Opcional. El elemento primario del botón.|  
|CommandFlag|Obligatorio. Vea [comando marca elemento](../extensibility/command-flag-element.md). Los valores válidos de CommandFlag para un botón son los siguientes.<br /><br /> -CaseSensitive<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DynamicVisibility<br /><br /> -FilterKeys<br /><br /> -IconAndText<br /><br /> -NoAutoComplete<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -StretchHorizontally|  
|Cadenas|Obligatorio. Vea [cadenas elemento](../extensibility/strings-element.md). Se debe definir el elemento de ButtonText secundario.|  
|Anotación|Comentario opcional.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Commands (Elemento)](../extensibility/commands-element.md)|Representa la colección de comandos en la barra de herramientas de VSPackage.|  
  
## <a name="example"></a>Ejemplo  
  
```  
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
```  
  
## <a name="see-also"></a>Vea también  
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)