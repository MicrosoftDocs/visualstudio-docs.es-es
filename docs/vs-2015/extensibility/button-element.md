---
title: Elemento de botón | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ad49fd053a10938dcc9f038ff7385bcd93c6253f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47567051"
---
# <a name="button-element"></a>Button (Elemento)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [elemento Button](https://docs.microsoft.com/visualstudio/extensibility/button-element).  
  
Define un elemento que el usuario puede interactuar con. Los botones pueden ser de distintos tipos: botón, MenuButton y SplitDropDown.  
  
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
|guid|Requerido. GUID del identificador de comando/identificador de GUID.|  
|id|Requerido. Id. del identificador de comando/identificador de GUID.|  
|priority|Opcional. Un valor numérico que especifica la prioridad.|  
|type|Opcional. Un valor enumerado que especifica el tipo de botón.<br /><br /> Si no se especifica, utiliza el botón.<br /><br /> Botón<br /> Un comando estándar que aparece en las barras de herramientas (normalmente como un botón icónico), los menús y menús contextuales.<br /><br /> MenuButton<br /> Un elemento de menú que no se ejecuta un comando, pero genera otro menú.<br /><br /> SplitDropDown<br /> Controles, como los botones Deshacer y rehacer de la barra de herramientas estándar en Microsoft Word.|  
|Condición|Opcional. Consulte [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Parent (Elemento)](../extensibility/parent-element.md)|Opcional. El elemento primario del botón.|  
|[Icon (Elemento)](../extensibility/icon-element.md)|Opcional. El icono asociado con el botón.|  
|[Command Flag (Elemento)](../extensibility/command-flag-element.md)|Requerido. Los valores válidos de CommandFlag para un botón son los siguientes.<br /><br /> -AllowParams<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DontCache<br /><br /> -DynamicItemStart<br /><br /> -DynamicVisibility<br /><br /> -FixMenuController<br /><br /> -IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -NoShowOnMenuController<br /><br /> -Pict<br /><br /> -PostExec<br /><br /> -ProfferedCmd<br /><br /> -RouteToDocs<br /><br /> -TextCascadeUseBtn<br /><br /> -TextMenuUseButton<br /><br /> -TextoCambia<br /><br /> -TextChangesButton<br /><br /> -TextContextUseButton<br /><br /> -TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly|  
|[Strings (Elemento)](../extensibility/strings-element.md)|Requerido. El elemento secundario [ButtonText (elemento)](../extensibility/buttontext-element.md) debe definirse.|  
|Anotación|Comentario opcional.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Buttons (Elemento)](../extensibility/buttons-element.md)|Agrupa los elementos de botón.|  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente define un botón en un archivo .vsct.  
   
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
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

