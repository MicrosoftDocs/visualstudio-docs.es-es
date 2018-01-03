---
title: "Caracteres de codificación y salto de línea de Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8a472a09a4d4d67f59d7879d03b466932d1445e6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="encodings-and-line-breaks"></a>Codificaciones y saltos de línea
Los siguientes caracteres se interpretan como saltos de línea en Visual Studio:  
  
-   CR LF: Retorno de carro + avance de línea, caracteres Unicode 000D + 000A  
  
-   LF: Avance de línea, carácter Unicode 000A  
  
-   NEL: Línea siguiente, carácter Unicode 0085  
  
-   LS: Separador de líneas, carácter Unicode 2028  
  
-   PS: Separador de párrafo, carácter Unicode 2029  
  
El texto que se copia de otras aplicaciones mantiene la codificación original y los caracteres de salto de línea. Por ejemplo, cuando copia texto desde el Bloc de notas y lo pega en un archivo de texto en Visual Studio, el texto tiene la misma configuración que tenía en el Bloc de notas.  
  
Cuando abre un archivo que tiene caracteres de salto de línea diferentes, puede que vea un cuadro de diálogo que le pregunta si los caracteres de salto de línea incoherentes deben normalizarse y qué tipo de salto de línea quiere.

Puede usar el cuadro de diálogo **Archivo**, **Opciones avanzadas para guardar** para determinar el tipo de caracteres de salto de línea que quiere. También puede cambiar la codificación de un archivo con las mismas opciones.

![Cuadro de diálogo Opciones avanzadas para guardar](media/line_endings.png)
  
> [!NOTE]
>  Si no ve el cuadro de diálogo **Opciones avanzadas para guardar** en el menú **Archivo**, puede agregarlo. Elija **Herramientas**, **Personalizar…** y, después, elija la pestaña **Comandos**. En la lista desplegable **Barra de menús**, elija **Archivo** y seleccione el botón **Agregar comando…** En el cuadro de diálogo **Agregar comando**, en **Categorías**, elija **Archivo** y, en la lista **Comandos**, seleccione **Opciones avanzadas para guardar…** Seleccione **Aceptar** y después elija el botón **Bajar** para mover el comando a cualquier lugar del menú. Seleccione **Cerrar** para cerrar el cuadro de diálogo **Personalizar**. Para obtener más información, vea [Personalizar un menú o una barra de herramientas](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu).

Para tener acceso al cuadro de diálogo **Opciones avanzadas para guardar**, también puede elegir **Archivo**, **Guardar \<archivo\> como…** En el cuadro de diálogo **Guardar archivo como**, seleccione el triángulo de lista desplegable junto al botón **Guardar** y elija **Guardar con codificación…**

## <a name="see-also"></a>Vea también
[Escribir código en el editor](../ide/writing-code-in-the-code-and-text-editor.md)