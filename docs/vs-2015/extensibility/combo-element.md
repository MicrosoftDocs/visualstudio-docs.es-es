---
title: Combo (elemento) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7ccca82d8716b57f854d6527bf462bb6ec687abb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49859790"
---
# <a name="combo-element"></a>Combo (Elemento)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Define los comandos que aparecen en un cuadro combinado. Hay cuatro tipos de cuadros combinados, como sigue: cuadro combinado desplegable, DynamicCombo, IndexCombo y MRUCombo.  
  
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
|guid|Requerido. GUID del identificador de comando/identificador de GUID.|  
|id|Requerido. Id. del identificador de comando/identificador de GUID.|  
|defaultWidth|Requerido. Un entero que especifica un ancho de píxel del cuadro combinado.|  
|idCommandList|Requerido. Un identificador que se envía al destino de comando activo para recuperar la lista de elementos que se mostrará en el cuadro combinado. El identificador estará en el mismo ámbito GUID que el control.|  
|priority|Opcional. Un valor numérico que especifica la prioridad.|  
|type|Opcional. Un valor enumerado que especifica el tipo de botón.<br /><br /> Si no se especifica, utiliza el botón.<br /><br /> Cuadro combinado desplegable<br /> El VSPackage es responsable de rellenar el contenido de este cuadro combinado. El usuario no puede escribir nada en el cuadro de texto de esta lista desplegable.<br /><br /> DynamicCombo<br /> El VSPackage es responsable de rellenar el contenido de este cuadro combinado. El usuario puede editar a este cuadro combinado y también seleccionar elementos en él.<br /><br /> IndexCombo<br /> Igual que DynamicCombo excepto en que genera el índice del elemento en lugar de su texto.<br /><br /> MRUCombo<br /> Rellenado por el entorno de desarrollo integrado (IDE) en nombre de VSPackage.  El usuario puede editar en este cuadro combinado. El IDE recuerda hasta las últimas 16 entradas por cuadro combinado.<br /><br /> Cuando el usuario selecciona algo en el cuadro combinado o entra en algo nuevo, el IDE notifica a VSPackage adecuado.|  
|Condición|Opcional. Consulte [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|Elemento primario|Opcional. El elemento primario del botón.|  
|CommandFlag|Requerido. Consulte [Command Flag (elemento)](../extensibility/command-flag-element.md). Los valores válidos de CommandFlag para un botón son los siguientes.<br /><br /> -CaseSensitive<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DynamicVisibility<br /><br /> -FilterKeys<br /><br /> -IconAndText<br /><br /> -NoAutoComplete<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -StretchHorizontally|  
|Cadenas|Requerido. Consulte [cadenas elemento](../extensibility/strings-element.md). Se debe definir el elemento ButtonText secundario.|  
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

