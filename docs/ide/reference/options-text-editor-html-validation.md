---
title: Opciones, Editor, HTML (formularios Web Forms), validación
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Validation
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ede4600cb1fa1df118b4635a193d8bff348d5119
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568287"
---
# <a name="options-text-editor-html-web-forms-validation"></a>Opciones, Editor, HTML (formularios Web Forms), validación

Use la página de opciones **Validación** para establecer preferencias en el modo en que el editor HTML comprueba la sintaxis del marcado HTML de un documento. Para acceder a esta página, en la barra de menús elija **Herramientas** > **Opciones** y expanda **Editor de texto** > **HTML (formularios Web Forms)**  > **Validación**.

## <a name="validation"></a>Validación

- **Usar doctype para la detección del esquema de validación**

   Un esquema determina qué elementos, atributos y uso de mayúsculas son válidos en ese esquema. También determina las etiquetas y los atributos que están disponibles en IntelliSense.

   Seleccione esta opción si desea que Visual Studio use el contenido de la declaración **<!DOCTYPE>** y el elemento **html** de la página para determinar el esquema. Por ejemplo, si selecciona esta opción y la página tiene la declaración `<!DOCTYPE html>`, Visual Studio usa el esquema HTML5. Sin embargo, si la etiqueta **html** tiene un atributo **xmlns**, como `<html>`, Visual Studio usa el esquema XHTML5.

- **Destino cuando no se encontró ningún DOCTYPE**

   Elija el esquema con el que se va a validar cuando no haya ninguna declaración **<!DOCTYPE>** en la página.

  - **Mostrar errores**

     Active la casilla para habilitar la validación. Si no se activa la casilla, el editor no marca los errores de validación.

     Las otras casillas permiten ajustar la validación con mayor precisión, especificando los tipos de errores individuales que quiere que marque el editor.

     > [!NOTE]
     > Algunos esquemas no ofrecen opciones para marcar tipos concretos de errores. Por ejemplo, si elige **XHTML 1.1** como el esquema de destino, se deshabilitan todas las casillas de opciones. En esta instancia, se marcan todos los tipos de errores.

## <a name="see-also"></a>Vea también

- [General, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md)
