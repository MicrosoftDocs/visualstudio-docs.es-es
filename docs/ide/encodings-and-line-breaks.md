---
title: "Codificaciones y saltos de línea | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 34c400c280096acb7e0ce272fa717cbc2f8f0d8a
ms.contentlocale: es-es
ms.lasthandoff: 05/24/2017

---
# <a name="encodings-and-line-breaks"></a>Codificaciones y saltos de línea
En Visual Studio puede usar la configuración **Opciones avanzadas para guardar/de archivo** para determinar el tipo de caracteres de salto de línea que quiere. También puede cambiar la codificación de un archivo con las mismas opciones.  
  
> [!NOTE]
>  Si tiene tipos determinados de opciones de desarrollo (Visual Basic, F#, desarrollo de Web), puede que no vea **Opciones avanzadas para guardar** en el menú. Para cambiar su configuración (por ejemplo, a General), abra **Herramientas / Importar y exportar configuraciones**. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 En Visual Studio, los siguientes caracteres se interpretan como saltos de línea:  
  
-   CRLF: Retorno de carro + avance de línea, caracteres Unicode 000D + 000A  
  
-   LF: Avance de línea, carácter Unicode 000A  
  
-   NEL: Línea siguiente, carácter Unicode 0085  
  
-   LS: Separador de líneas, carácter Unicode 2028  
  
-   PS: Separador de párrafo, carácter Unicode 2029  
  
 El texto que se copia de otras aplicaciones mantiene la codificación original y los caracteres de salto de línea. Por ejemplo, cuando copia texto desde el Bloc de notas y lo pega en un archivo de texto en Visual Studio, el texto tiene la misma configuración que tenía en el Bloc de notas.  
  
 Cuando abre un archivo que tiene caracteres de salto de línea diferentes, puede que vea un cuadro de diálogo que le pregunta si los caracteres de salto de línea incoherentes deben normalizarse y qué tipo de salto de línea quiere.
