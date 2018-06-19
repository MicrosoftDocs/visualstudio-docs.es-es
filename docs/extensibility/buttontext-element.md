---
title: Elemento ButtonText | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2fca0fbb22bf51353eeaa64f519face53bfb23c8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100184"
---
# <a name="buttontext-element"></a>Elemento ButtonText
Este campo le permite especificar el texto que aparece en varios menús. De forma predeterminada, la `ButtonText` elemento aparece en controladores de menús. El `ButtonText` elemento también es el valor predeterminado si los demás campos de texto están en blanco. El `ButtonText` elemento no puede estar en blanco, incluso si se especifican los demás campos de texto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<ButtonText>My Command</ButtonText>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
 Ninguno.  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Strings (Elemento)](../extensibility/strings-element.md)|Agrupa elementos de texto, como `ButtonText` y `CommandName`.|  
  
## <a name="text-value"></a>Valor de texto  
 El valor de texto de la `ButtonText` elemento proporciona el texto que se muestra para los elementos de menú, combinaciones y otros elementos de interfaz (UI) de usuario que tienen texto visible.  
  
## <a name="see-also"></a>Vea también  
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)