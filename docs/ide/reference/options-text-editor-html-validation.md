---
title: Opciones, Editor, HTML (formularios Web Forms), validación
ms.date: 1/15/2019
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Validation
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f629a0b8d9f149ee10f7a35c75e351a6c3abfd3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031778"
---
# <a name="options-text-editor-html-web-forms-validation"></a>Opciones, Editor, HTML (formularios Web Forms), validación

Use la página de opciones **Validación** para establecer preferencias en el modo en que el editor HTML comprueba la sintaxis del marcado HTML de un documento. Para acceder a esta página, en la barra de menús elija **Herramientas** > **Opciones** y expanda **Editor de texto** > **HTML (formularios Web Forms)** > **Validación**.

## <a name="validation"></a>Validación

- **Usar doctype para la detección del esquema de validación**

   Un esquema determina qué elementos, atributos y uso de mayúsculas son válidos en ese esquema. También determina las etiquetas y los atributos que están disponibles en IntelliSense.

   Seleccione esta opción si desea que Visual Studio use el contenido de la declaración **<!DOCTYPE>** y el elemento **html** de la página para determinar el esquema. Por ejemplo, si selecciona esta opción y la página tiene la declaración `<!DOCTYPE html>`, Visual Studio usa el esquema HTML5. Sin embargo, si la etiqueta **html** tiene un atributo **xmlns**, como `<html xmlns="http://www.w3.org/1999/xhtml">`, Visual Studio usa el esquema XHTML5.

- **Destino cuando no se encontró ningún DOCTYPE**

   Elija el esquema con el que se va a validar cuando no haya ninguna declaración **<!DOCTYPE>** en la página.

  - **Mostrar errores**

     Active la casilla para habilitar la validación. Si no se activa la casilla, el editor no marca los errores de validación.

     Las otras casillas permiten ajustar la validación con mayor precisión, especificando los tipos de errores individuales que quiere que marque el editor.

     > [!NOTE]
     > Algunos esquemas no ofrecen opciones para marcar tipos concretos de errores. Por ejemplo, si elige **XHTML 1.1** como el esquema de destino, se deshabilitan todas las casillas de opciones. En esta instancia, se marcan todos los tipos de errores.

## <a name="see-also"></a>Vea también

- [General, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md)