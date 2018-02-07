---
title: "Generación de comentarios de documentación XML para Visual Basic | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 2f421553657dfafb265140e44e38a2c7722a7303
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2018
---
# <a name="generate-xml-documentation-comments-in-visual-basic"></a>Generación de comentarios de documentación XML en Visual Basic

**Qué:** Le permite generar de inmediato el XML básico requerido para documentar el elemento seleccionado. 

**Cuándo:** Desea crear comentarios de documentos XML para su procesamiento posterior por una herramienta de documentación como Sandcastle.

**Por qué:** Podría crear manualmente todo el bloque de comentarios manualmente; sin embargo, este proceso ahorrará tiempo y mejorará la precisión mediante la generación de la plantilla base y elementos adicionales. 

**Cómo**:

1. Coloque el cursor de texto sobre el elemento que desea documentar; por ejemplo, un método.

   ![Método a documento](media/doc-highlight-vb.png)

1. A continuación, escriba **'''** (3 comillas simples) que crearán automáticamente la plantilla base y cualquier elemento adicional según sea necesario.  Por ejemplo, al comentar un método, se generarán las etiquetas **\<summary\>**, así como una etiqueta **\<param\>** para cada parámetro que se pase al método, y una etiqueta  **\<returns\>** para documentar lo que devuelve el método.

   ![Plantilla](media/doc-preview-vb.png)

1. Complete los comentarios y agregue cualquier información adicional que considere necesaria.

   ![Comentario completado](media/doc-result-vb.png)

## <a name="see-also"></a>Vea también

[Documentar el código con XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml)  
[Generación de código](../code-generation-in-visual-studio.md)