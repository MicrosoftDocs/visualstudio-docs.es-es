---
title: "Elemento ButtonText | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Elemento ButtonText (esquema VSCT XML)"
  - "Elementos de esquema XML VSCT, ButtonText"
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# Elemento ButtonText
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este campo le permite especificar el texto que aparece en varios menús. De forma predeterminada, la `ButtonText` elemento aparece en los controladores de menú. El `ButtonText` elemento también es el valor predeterminado si los demás campos de texto están en blanco. El `ButtonText` elemento no puede estar en blanco, incluso si se especifican los demás campos de texto.  
  
## Sintaxis  
  
```  
<ButtonText>My Command</ButtonText>  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
 Ninguno.  
  
### Elementos secundarios  
 Ninguno.  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Elemento de cadenas](../extensibility/strings-element.md)|Agrupa los elementos de texto, como `ButtonText` y `CommandName`.|  
  
## Valor de texto  
 El valor de texto de la `ButtonText` elemento proporciona el texto que se muestra para los elementos de menú, combinaciones y otros elementos de interfaz de usuario con texto visible.  
  
## Vea también  
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)