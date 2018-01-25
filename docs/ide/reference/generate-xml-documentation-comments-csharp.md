---
title: "Generación de comentarios de documentación XML: generación de código (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2025bd2-5984-4486-a61c-0a0933a735ea
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: b0a0ec1db54f57e14ddd412248f7a396336fe009
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
---
# <a name="generate-xml-documentation-comments-in-c"></a>Generación de comentarios de documentación XML en C# #
**Qué:** Le permite generar de inmediato el XML básico requerido para documentar el elemento seleccionado. 

**Cuándo:** Desea crear comentarios de documentos XML para su procesamiento posterior por una herramienta de documentación como Sandcastle.

**Por qué:** Podría crear manualmente todo el bloque de comentarios manualmente; sin embargo, este proceso ahorrará tiempo y mejorará la precisión mediante la generación de la plantilla base y elementos adicionales. 

**Cómo**:

1. Coloque el cursor de texto sobre el elemento que desea documentar; por ejemplo, un método.

   ![Método a documento](media/doc-highlight-cs.png)

1. A continuación, escriba **///** (3 barras diagonales) que crearán automáticamente la plantilla base y cualquier elemento adicional según sea necesario.  Por ejemplo, al comentar un método, se generarán las etiquetas **\<summary\>**, así como una etiqueta **\<param\>** para cada parámetro que se pase al método, y una etiqueta  **\<returns\>** para documentar lo que devuelve el método.

   ![Plantilla](media/doc-preview-cs.png)

1. Complete los comentarios y agregue cualquier información adicional que considere necesaria.

   ![Comentario completado](media/doc-result-cs.png)

## <a name="see-also"></a>Vea también

[Generación de código](../code-generation-in-visual-studio.md)  
[Comentarios de documentación XML (Guía de programación de C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
