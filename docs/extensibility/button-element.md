---
title: "Elemento de bot&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Elemento de botones (esquema VSCT XML)"
  - "Elementos del esquema XML de VSCT, botones"
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento de bot&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Define un elemento que el usuario puede interactuar con. Botones pueden ser de tipos diferentes: botón, MenuButton y SplitDropDown.  
  
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
|guid|Obligatorio. GUID del identificador de comando/identificador GUID.|  
|identificador|Obligatorio. Id. del identificador de comando/identificador GUID.|  
|priority|Opcional. Un valor numérico que especifica la prioridad.|  
|tipo|Opcional. Un valor enumerado que especifica el tipo de botón.<br /><br /> Si no se proporcionan, utiliza el botón.<br /><br /> Botón<br /> Un comando estándar que aparece en las barras de herramientas (normalmente como un botón de icono), los menús y menús contextuales.<br /><br /> MenuButton<br /> Un elemento de menú que no se ejecuta un comando, pero genera otro menú.<br /><br /> SplitDropDown<br /> Controles, como los botones de deshacer y rehacer en la barra de herramientas estándar en Microsoft Word.|  
|Condición|Opcional. Vea [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Elemento primario](../extensibility/parent-element.md)|Opcional. El elemento primario del botón.|  
|[Icon (elemento)](../extensibility/icon-element.md)|Opcional. El icono asociado con el botón.|  
|[Elemento de marcador de comando](../extensibility/command-flag-element.md)|Obligatorio. Los valores válidos de CommandFlag para un botón son los siguientes.<br /><br /> -AllowParams<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DontCache<br /><br /> -DynamicItemStart<br /><br /> -DynamicVisibility<br /><br /> -FixMenuController<br /><br /> -IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -NoShowOnMenuController<br /><br /> -Pict<br /><br /> -PostExec<br /><br /> -ProfferedCmd<br /><br /> -RouteToDocs<br /><br /> -TextCascadeUseBtn<br /><br /> -TextMenuUseButton<br /><br /> -TextoCambia<br /><br /> -TextChangesButton<br /><br /> -TextContextUseButton<br /><br /> -TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly|  
|[Elemento de cadenas](../extensibility/strings-element.md)|Obligatorio. El elemento secundario [ButtonText elemento](../extensibility/buttontext-element.md) debe definirse.|  
|Anotación|Comentario opcional.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Elemento de botones](../extensibility/buttons-element.md)|Agrupa elementos de botón.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se define un botón en un archivo .vsct.  
  
 [!CODE [MenuText#02](../CodeSnippet/VS_Snippets_VSSDK/menutext#02)]  
  
## <a name="see-also"></a>Vea también  
 [Tabla de comandos de Visual Studio (. Archivos Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)