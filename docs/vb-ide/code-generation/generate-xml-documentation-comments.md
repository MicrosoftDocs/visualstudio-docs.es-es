---
title: "Generar comentarios de documentación XML: generación de código (Visual Basic) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2025bd2-5984-4486-a61c-0a0933a735ea
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1291667c7acb47abe543d275549179abea0c8467
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="generate-xml-documentation-comments-in-visual-basic"></a>Generar comentarios de documentación XML en Visual Basic
**¿Qué:** permite generar inmediatamente la base de XML requerido para documentar el elemento seleccionado. 

**Cuándo:** desea crear comentarios de documentos XML para ser procesado posteriormente por una herramienta de documentación como Sandcastle.

**Por este motivo:** podría crear manualmente el bloque de comentario todo usted mismo, sin embargo, esto ahorra tiempo y mejorar la precisión mediante la generación de la plantilla base y elementos adicionales. 

**Cómo:**

1. Coloque el cursor de texto sobre el elemento de documento, por ejemplo, un método.

   ![Método al documento](media/doc_highlight.png)

1. A continuación, escriba **'''** (3 comillas simples) que creará automáticamente la plantilla base y cualquier elemento adicional según sea necesario.  Por ejemplo, cuando un método de comentarios, generará el  **\<resumen\>**  etiquetas, así como un  **\<param\>**  etiqueta para cada parámetro que es pasa al método y un  **\<devuelve\>**  etiqueta en el método que devuelve un documento.

   ![Plantilla](media/doc_preview.png)

1. Complete los comentarios y agregar cualquier información adicional que crees que es necesario.

   ![Comentario completada](media/doc_result.png)

## <a name="see-also"></a>Vea también
[Documentar el código con XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml)  
[Code Generation (Visual Basic)](../code-generation-vb.md) (Generación de código (Visual Basic)) 