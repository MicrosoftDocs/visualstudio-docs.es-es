---
title: Elemento de botón | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d4bfa27ac2a71e53418ac1be1f9a377f06aede7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53870182"
---
# <a name="button-element"></a>Elemento de botón
Define un elemento que el usuario puede interactuar con. Los botones pueden ser de distintos tipos: Botón MenuButton y SplitDropDown.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">  
  <Parent>... </Parent>  
  <Icon>... </Icon>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Button>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|guid|Obligatorio. GUID del identificador de comando/identificador de GUID.|  
|id|Obligatorio. Id. del identificador de comando/identificador de GUID.|  
|priority|Opcional. Un valor numérico que especifica la prioridad.|  
|type|Opcional. Un valor enumerado que especifica el tipo de botón.<br /><br /> Si no se especifica, utiliza el botón.<br /><br /> Botón<br /> Un comando estándar que aparece en las barras de herramientas (normalmente como un botón icónico), los menús y menús contextuales.<br /><br /> MenuButton<br /> Un elemento de menú que no se ejecuta un comando, pero genera otro menú.<br /><br /> SplitDropDown<br /> Controles, como los botones Deshacer y rehacer de la barra de herramientas estándar en Microsoft Word.|  
|Condición|Opcional. Consulte [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Elemento primario](../extensibility/parent-element.md)|Opcional. El elemento primario del botón.|  
|[Icon (elemento)](../extensibility/icon-element.md)|Opcional. El icono asociado con el botón.|  
|[Elemento de marcador de comando](../extensibility/command-flag-element.md)|Obligatorio. Los valores válidos de CommandFlag para un botón son los siguientes.<br /><br /> -AllowParams<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DontCache<br /><br /> -DynamicItemStart<br /><br /> -DynamicVisibility<br /><br /> -FixMenuController<br /><br /> -IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -NoShowOnMenuController<br /><br /> -Pict<br /><br /> -PostExec<br /><br /> -ProfferedCmd<br /><br /> -RouteToDocs<br /><br /> -TextCascadeUseBtn<br /><br /> -TextMenuUseButton<br /><br /> -TextoCambia<br /><br /> -TextChangesButton<br /><br /> -TextContextUseButton<br /><br /> -TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly|  
|[Strings (elemento)](../extensibility/strings-element.md)|Obligatorio. El elemento secundario [ButtonText (elemento)](../extensibility/buttontext-element.md) debe definirse.|  
|Anotación|Comentario opcional.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Buttons (elemento)](../extensibility/buttons-element.md)|Agrupa los elementos de botón.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se define un botón en un *.vsct* archivo.  

 ```xml
<Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
    <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
    <Icon guid="guidImages" id="bmpPic1" />
    <CommandFlag>TextChanges</CommandFlag>
    <Strings>
          <CommandName>cmdidMyCommand</CommandName>
          <ButtonText>My Command name</ButtonText>
    </Strings>
</Button>
 ```
 
## <a name="see-also"></a>Vea también  
 [Archivos visuales Studio comando table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)