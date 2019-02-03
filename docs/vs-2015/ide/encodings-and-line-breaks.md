---
title: Codificaciones y saltos de línea | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 88f04720610bad5064f7f9d7a43beef2410b045f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54787471"
---
# <a name="encodings-and-line-breaks"></a>Codificaciones y saltos de línea
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En Visual Studio puede usar la configuración **Opciones avanzadas para guardar/de archivo** para determinar el tipo de caracteres de salto de línea que quiere. También puede cambiar la codificación de un archivo con las mismas opciones.  
  
> [!NOTE]
>  Si tiene tipos determinados de opciones de desarrollo (Visual Basic, F#, desarrollo de Web), puede que no vea **Opciones avanzadas para guardar** en el menú. Para cambiar su configuración (por ejemplo, a General), abra **Herramientas / Importar y exportar configuraciones**. Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 En Visual Studio, los siguientes caracteres se interpretan como saltos de línea:  
  
- CRLF: Retorno de carro + avance de línea, caracteres Unicode 000D + 000A  
  
- LF: Avance de línea, carácter Unicode 000A  
  
- NEL: Línea siguiente, carácter Unicode 0085  
  
- LS: Separador de línea, carácter Unicode 2028  
  
- PS: Separador de párrafo, carácter Unicode 2029  
  
  El texto que se copia de otras aplicaciones mantiene la codificación original y los caracteres de salto de línea. Por ejemplo, cuando copia texto desde el Bloc de notas y lo pega en un archivo de texto en Visual Studio, el texto tiene la misma configuración que tenía en el Bloc de notas.  
  
  Cuando abre un archivo que tiene caracteres de salto de línea diferentes, puede que vea un cuadro de diálogo que le pregunta si los caracteres de salto de línea incoherentes deben normalizarse y qué tipo de salto de línea quiere.
