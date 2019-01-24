---
title: ButtonText (elemento) | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 8edd12a2f37ea0de3a3c01f013adea64a08424f5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905590"
---
# <a name="buttontext-element"></a>ButtonText (elemento)
Este campo le permite especificar el texto que aparece en varios menús. De forma predeterminada, el `ButtonText` elemento aparece en los controladores de menú. El `ButtonText` elemento también es el valor predeterminado si los demás campos de texto están en blanco. El `ButtonText` elemento no puede estar en blanco, incluso si se especifican los demás campos de texto.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
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
 El valor de texto de la `ButtonText` elemento proporciona el texto que se muestra para los elementos de menú, cuadro combinado y otros elementos de interfaz de usuario con texto visible.  
  
## <a name="see-also"></a>Vea también  
 [Archivos visuales Studio comando table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)