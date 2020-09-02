---
title: Elemento combinado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: daa89266d653743a743f42e5f0b8e11c954adc1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184411"
---
# <a name="combo-element"></a>Combo (Elemento)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Define comandos que aparecen en un cuadro combinado. Hay cuatro tipos de cuadros combinados, como se indica a continuación: DropDownCombo, DynamicCombo, IndexCombo y MRUCombo.  
  
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
|guid|Necesario. GUID del identificador del comando GUID/ID.|  
|id|Necesario. IDENTIFICADOR del identificador del comando GUID/ID.|  
|defaultWidth|Necesario. Un entero que especifica un ancho de píxel para el cuadro combinado.|  
|idCommandList|Necesario. IDENTIFICADOR que se envía al destino de la comandos activa para recuperar la lista de elementos que se van a mostrar en el cuadro combinado. El identificador estará en el mismo ámbito GUID que el control.|  
|priority|Opcional. Valor numérico que especifica la prioridad.|  
|type|Opcional. Valor enumerado que especifica el tipo de botón.<br /><br /> Si no se especifica, usa el botón.<br /><br /> DropDownCombo<br /> El VSPackage es responsable de rellenar el contenido de este cuadro combinado. El usuario no puede escribir nada en el cuadro de texto de esta lista desplegable.<br /><br /> DynamicCombo<br /> El VSPackage es responsable de rellenar el contenido de este cuadro combinado. El usuario puede editar este cuadro combinado y seleccionar también los elementos que contenga.<br /><br /> IndexCombo<br /> Lo mismo que DynamicCombo, salvo que genera el índice del elemento en lugar de su texto.<br /><br /> MRUCombo<br /> Lo rellena el entorno de desarrollo integrado (IDE) en nombre del VSPackage.  El usuario puede editar en este cuadro combinado. El IDE recuerda hasta las 16 últimas entradas por cuadro combinado.<br /><br /> Cuando el usuario selecciona algo en el cuadro combinado o escribe algo nuevo, el IDE notifica al VSPackage adecuado.|  
|Condición|Opcional. Vea [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|Parent|Opcional. Elemento primario del botón.|  
|CommandFlag|Necesario. Vea [elemento de marca de comando](../extensibility/command-flag-element.md). Los valores válidos de CommandFlag para un botón son los siguientes.<br /><br /> -CaseSensitive<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - DefaultInvisible<br /><br /> - DynamicVisibility<br /><br /> -FilterKeys<br /><br /> - IconAndText<br /><br /> - NoAutoComplete<br /><br /> - NoButtonCustomize<br /><br /> -Nocustomizate<br /><br /> - NoKeyCustomize<br /><br /> - StretchHorizontally|  
|Cadenas|Necesario. Vea el [elemento Strings](../extensibility/strings-element.md). Se debe definir el elemento ButtonText secundario.|  
|Anotación|Comentario opcional.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Commands, elemento](../extensibility/commands-element.md)|Representa la colección de comandos de la barra de herramientas de VSPackage.|  
  
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
  
## <a name="see-also"></a>Consulte también  
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
