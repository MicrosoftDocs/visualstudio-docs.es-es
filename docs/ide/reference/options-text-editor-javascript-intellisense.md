---
title: Opciones, editor de texto, JavaScript, IntelliSense
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.References
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.IntelliSense.General
ms.assetid: b4a9816d-cf87-4dc6-a8d4-1591d6a48103
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7fad8ba4b41768246fcd14bd6c3aed8b31c1647b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54927679"
---
# <a name="options-text-editor-javascript-intellisense"></a>Opciones, editor de texto, JavaScript, IntelliSense
Utilice la página **IntelliSense** del cuadro de diálogo **Opciones** para modificar la configuración que afecta al comportamiento de IntelliSense para JavaScript. Puede acceder a la página **IntelliSense** en **Herramientas** > **Opciones**, en la barra de menús. Luego, amplíe **Editor de texto** > **JavaScript** > **IntelliSense**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

La página **IntelliSense** contiene las siguientes secciones:

## <a name="statement-completion"></a>Finalización de instrucciones
 Puede utilizar estas opciones para cambiar el comportamiento de la finalización de instrucciones de IntelliSense.

### <a name="uielement-list"></a>Lista de UIElement
 **Usar solo Tab o Entrar para confirmar**

 Cuando se activa esta casilla, el editor de código de JavaScript anexa instrucciones con elementos seleccionados en la lista de finalización únicamente después de elegir la tecla **Tab** o **Entrar**. Cuando se desactiva esta casilla, otros caracteres, como un punto, una coma, dos puntos, un paréntesis de apertura y una llave de apertura ({), también puede anexar instrucciones con los elementos seleccionados.

## <a name="references"></a>Referencias
 Puede utilizar estas opciones para especificar los tipos de archivos de IntelliSense .js que están incluidos en el ámbito para diferentes tipos de proyecto de JavaScript. Las referencias de IntelliSense se utilizan normalmente para proporcionar compatibilidad con IntelliSense a los objetos globales. También puede utilizar esta página para establecer el orden de carga de los scripts que se deben cargar en tiempo de ejecución y para agregar archivos de extensión de IntelliSense.

### <a name="uielement-list"></a>Lista de UIElement
 **Grupos de referencias**

 Esta opción especifica el tipo de grupo de referencias. Se admiten tres grupos de referencias:

 Puede usar los grupos de referencias predefinidos para especificar qué archivos concretos de IntelliSense .js se incluyen en el ámbito para proyectos diferentes de JavaScript. Hay cuatro grupos de referencias disponibles:

- Implícito ( *versión*de Windows), para aplicaciones de la [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] que usan JavaScript. Los archivos incluidos en este grupo pertenecen al ámbito de cada archivo .js abierto en el editor de código para las aplicaciones de [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] que usan JavaScript.

- Implícito (Web), para proyectos HTML5. Los archivos incluidos en este grupo están en el ámbito de cada archivo .js abierto en el Editor de código para estos tipos de proyecto.

- Grupos de referencia de trabajo dedicado, para trabajos web de HTML5. Los archivos especificados en este grupo están en el ámbito para los archivos .js que tienen una referencia explícita a un grupo de referencia de trabajo dedicado.

- Genérico, para otros tipos de proyectos JavaScript.

**Archivos incluidos**

Esta opción especifica el orden en que los archivos se cargan en el contexto del servicio de lenguaje. Puede configurar el orden utilizando los botones **Quitar**, **Subir**y **Bajar** . Para que IntelliSense funcione correctamente, un archivo que depende de otro se debe cargar después del otro archivo.

> [!CAUTION]
> Si un objeto se define incondicionalmente en dos o más referencias implícitas, la última referencia de esta lista se utilizará para definir el objeto.


**Agregar una referencia al grupo**

Esta opción permite agregar archivos adicionales de IntelliSense .js buscando los archivos correspondientes.

**Descargar referencias remotas (por ejemplo, http://) para los archivos del proyecto de archivos varios**

Cuando se activa esta casilla, y si tiene un archivo de JavaScript abierto fuera del contexto de un proyecto, Visual Studio descarga los archivos de JavaScript remotos a los que se hace referencia en el archivo con el fin de proporcionar información de IntelliSense. Si esta opción está seleccionada, los archivos se descargan cuando se incluyen como referencia en el archivo de JavaScript.

> [!NOTE]
> En los proyectos web, los archivos remotos a los que se hace referencia en el proyecto se descargan de forma predeterminada.



## <a name="see-also"></a>Vea también

- [IntelliSense para JavaScript](../../ide/javascript-intellisense.md)