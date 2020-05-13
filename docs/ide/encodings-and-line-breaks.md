---
title: Caracteres de codificación y salto de línea
ms.date: 11/04/2016
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6448b553c1da9e697bca3860cb8507727c99cc08
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588595"
---
# <a name="encodings-and-line-endings"></a>Codificaciones y finales de línea

Los siguientes caracteres se interpretan como saltos de línea en Visual Studio:

- CR LF: Retorno de carro + avance de línea, caracteres Unicode 000D + 000A

- LF: Avance de línea, carácter Unicode 000A

- NEL: Línea siguiente, carácter Unicode 0085

- LS: Separador de línea, carácter Unicode 2028

- PS: Separador de párrafo, carácter Unicode 2029

El texto que se copia de otras aplicaciones mantiene la codificación original y los caracteres de salto de línea. Por ejemplo, cuando copia texto desde el Bloc de notas y lo pega en un archivo de texto en Visual Studio, el texto tiene la misma configuración que tenía en el Bloc de notas.

Cuando abre un archivo que tiene caracteres de salto de línea diferentes, puede que vea un cuadro de diálogo que le pregunta si los caracteres de salto de línea incoherentes deben normalizarse y qué tipo de salto de línea quiere.

## <a name="advanced-save-options"></a>Opciones avanzadas para guardar

Puede usar el cuadro de diálogo **Archivo** > **Opciones avanzadas para guardar** para determinar el tipo de caracteres de salto de línea que quiere. También puede cambiar la codificación de un archivo con las mismas opciones.

![Cuadro de diálogo Opciones avanzadas para guardar](media/line_endings.png)

> [!NOTE]
> Si no ve el cuadro de diálogo **Opciones avanzadas para guardar** en el menú **Archivo**, puede agregarlo. Elija **Herramientas**, **Personalizar** y, después, elija la pestaña **Comandos**. En la lista desplegable **Barra de menús**, elija **Archivo** y haga clic en el botón **Agregar comando**. En el cuadro de diálogo **Agregar comando**, en **Categorías**, elija **Archivo** y, en la lista **Comandos**, seleccione **Opciones avanzadas para guardar**. Seleccione **Aceptar** y después elija el botón **Bajar** para mover el comando a cualquier lugar del menú. Seleccione **Cerrar** para cerrar el cuadro de diálogo **Personalizar**. Para obtener más información, vea [Personalizar un menú o una barra de herramientas](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu).
>
> Para tener acceso al cuadro de diálogo **Opciones avanzadas para guardar**, también puede elegir **Archivo** > **Guardar \<archivo\> como**. En el cuadro de diálogo **Guardar archivo como**, seleccione el triángulo de lista desplegable junto al botón **Guardar** y elija **Guardar con codificación**.

## <a name="see-also"></a>Vea también

- [Características del editor de código](../ide/writing-code-in-the-code-and-text-editor.md)
