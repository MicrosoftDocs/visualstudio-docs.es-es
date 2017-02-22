---
title: "Elemento de cadenas | Microsoft Docs"
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
  - "Elemento de cadenas (esquema VSCT XML)"
  - "Elementos de esquema XML VSCT, cadenas"
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento de cadenas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El elemento de cadenas debe contener al menos un **ButtonText** elemento secundario. Todos los demás elementos secundarios son opcionales. XML no válido, como los caracteres '&' y ' \<' se deben codificar como entidades \('& amp;' y '& lt;' y así sucesivamente\).  
  
 Una y comercial en la cadena de texto especifica el método abreviado de teclado para el comando.  
  
## Sintaxis  
  
```  
<Strings>  
  <ButtonText>... </ButtonText>  
  <CommandName>... </CommandName>  
</Strings>  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|lenguaje|Opcional. Language \= ".".|  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|ButtonText|Este campo y los siguientes cinco de los campos de texto en una definición de comando permiten especificar el texto que aparece en varios menús. De forma predeterminada, la `ButtonText` campo aparece en los controladores de menú. El `ButtonText` campo también se convierte en el predeterminado si los demás campos de texto están en blanco. El `ButtonText` campo no puede estar en blanco, incluso si se especifican los demás campos de texto.|  
|ToolTipText|El `ToolTipText` campo especifica el texto que aparece en la información sobre herramientas para un elemento de menú.<br /><br /> Si el `ToolTipText` campo está en blanco, el `ButtonText` se utiliza el campo.|  
|MenuText|El `MenuText` campo especifica el texto que se muestra para un comando si se encuentra en el menú principal, una barra de herramientas, en un menú contextual o en un submenú. Si el `MenuText` campo está en blanco, el entorno de desarrollo integrado \(IDE\) utiliza el `ButtonText` campo. El `MenuText` campo también se puede utilizar para la localización.<br /><br /> Menús contextuales, la `MenuText` campo es el nombre que se muestra en la barra de herramientas menús contextuales, que habilita la personalización de los menús contextuales en el IDE. Por lo tanto, ser específica de nombre el menú contextual; Por ejemplo, use "Widget paquete acceso directo" en lugar de "Acceso directo".<br /><br /> Si el `MenuText` campo no se especifica, el `ButtonText` se utiliza el campo.|  
|CommandName|El `CommandName` campo especifica el texto que aparece en la categoría de teclado en el **comandos** ficha en el **Personalizar** cuadro de diálogo \(disponible haciendo clic en **Personalizar** en el **herramientas** menú\).|  
|CanonicalName|Inglés `CanonicalName` campo especifica el nombre del comando de texto en inglés que puede escribirse en el **comando** ventana para ejecutar el elemento de menú. El IDE elimina todos los caracteres que no son letras, números, caracteres de subrayado o puntos. Este texto, a continuación, se concatena con el `ButtonText` campo para definir el comando. Por ejemplo, **nuevo proyecto** en el **archivo** menú se convierte en el comando File.NewProject.<br /><br /> Si el inglés `CanonicalName` campo no se especifica, el IDE utiliza la `ButtonText` campo y estropea todo excepto letras, dígitos, caracteres de subrayado y puntos. Por ejemplo, el texto del botón "& definir comandos..." se convierte en DefineCommands, que se quitan la y comercial, el espacio y los puntos suspensivos.<br /><br /> Si el `TextChanges` marca se especifica y se cambia el texto del comando, el comando correspondiente que reconoce el **comando** ventana no cambia; sigue siendo la forma canónica del original `ButtonText` o inglés `CanonicalName` campos.|  
|LocCanonicalName|El `LocCanonicalName` campo se comporta de forma idéntica a inglés `CanonicalName` campo pero permite texto de comando localizado que se especifique. Se pueden especificar ambos campos canónicos. Dado que el IDE solo analiza el texto escrito en el **comando** ventana y asocia con un comando, inglés y texto distinto del inglés puede estar asociado con el mismo comando.|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Elemento Button](../extensibility/button-element.md)|Define un elemento que el usuario puede interactuar con.|  
|[Elemento de menú](../extensibility/menu-element.md)|Define un solo elemento de menú.|  
|[Elemento de cuadro combinado](../extensibility/combo-element.md)|Define los comandos que aparecen en un cuadro combinado.|  
  
## Vea también  
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)