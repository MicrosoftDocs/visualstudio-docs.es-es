---
title: T4 Directiva de salida | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e0eaa2d8e3fc257e14e04bad3cac706b8a3bc92a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576879"
---
# <a name="t4-output-directive"></a>Directiva de salida T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [directiva de salida T4](https://docs.microsoft.com/visualstudio/modeling/t4-output-directive).  
  
En las plantillas de texto de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], la directiva `output` sirve para definir la extensión de nombre de archivo y codificación del archivo transformado.  
  
 Por ejemplo, si su [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proyecto incluye un archivo de plantilla denominado **MyTemplate.tt** que contiene la siguiente directiva:  
  
 `<#@output extension=".cs"#>`  
  
 a continuación, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generará un archivo denominado **MyTemplate.cs**  
  
 La directiva de `output` no es necesaria en una plantilla de texto en tiempo de ejecución (preprocesada), ya que, en su lugar, la aplicación obtiene la cadena generada llamando a `TextTransform()`. Para obtener más información, consulte [generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## <a name="using-the-output-directive"></a>Uso de la directiva de salida  
  
```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 No debe haber más de una directiva de `output` en cada plantilla de texto.  
  
## <a name="extension-attribute"></a>atributo de extensión  
 Especifica la extensión de nombre del archivo de salida de texto generado.  
  
 El valor predeterminado es **.cs**  
  
 Ejemplos:  
 `<#@ output extension=".txt" #>`  
  
 `<#@ output extension=".htm" #>`  
  
 `<#@ output extension=".cs" #>`  
  
 `<#@ output extension=".vb" #>`  
  
 Valores aceptables:  
 Cualquier extensión de nombre de archivo válida.  
  
## <a name="encoding-attribute"></a>atributo de codificación  
 Especifica la codificación que se va a usar cuando el archivo de salida se genera. Por ejemplo:  
  
 `<#@ output encoding="utf-8"#>`  
  
 El valor predeterminado es la codificación que el archivo de plantilla de texto utiliza.  
  
 Valores aceptables:  
 `us-ascii`  
  
 `utf-16BE`  
  
 `utf-16`  
  
 `utf-8`  
  
 `utf-7`  
  
 `utf-32`  
  
 `0` (valor predeterminado del sistema)  
  
 Por lo general, se puede usar la cadena WebName o el número de CodePage de cualquiera de las codificaciones devueltas por <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.



