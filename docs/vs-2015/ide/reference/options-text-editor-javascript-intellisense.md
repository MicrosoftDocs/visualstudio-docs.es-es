---
title: Opciones, editor de texto, JavaScript, IntelliSense | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.References
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.General
ms.assetid: b4a9816d-cf87-4dc6-a8d4-1591d6a48103
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b3b17416902bac2bcc7ff03adc39e548e63fb229
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879367"
---
# <a name="options-text-editor-javascript-intellisense"></a>Opciones, editor de texto, JavaScript, IntelliSense
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [opciones, Editor de texto, JavaScript, IntelliSense](https://docs.microsoft.com/visualstudio/ide/reference/options-text-editor-javascript-intellisense).  
  
  
Utilice la página **IntelliSense** del cuadro de diálogo **Opciones** para modificar la configuración que afecta al comportamiento de IntelliSense para JavaScript. Puede tener acceso a la página **IntelliSense** eligiendo **Herramientas**, **Opciones** en la barra de menús, y expandiendo **Editor de texto**, **JavaScript**, **IntelliSense**.  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
 La página **IntelliSense** contiene las siguientes secciones:  
  
## <a name="validation"></a>Validación  
 Puede utilizar estas opciones para establecer preferencias sobre el modo en que el editor de JavaScript valida la sintaxis del documento.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Mostrar errores de sintaxis**  
 Si esta casilla no está activada, el editor de código JavaScript no muestra errores de sintaxis. Esto resulta útil si trabaja con código que no es suyo y no tiene intención de corregir los errores de sintaxis.  
  
 Con esta casilla activada, tiene la opción de activar la casilla **Mostrar errores como advertencias** .  
  
 **Mostrar errores como advertencias**  
 Cuando se activa esta casilla, los errores de JavaScript se muestran como advertencias en lugar de como errores en la lista de errores.  
  
 **Descargar referencias remotas (por ejemplo, http://) para los archivos del proyecto de archivos varios**  
 Cuando se activa esta casilla, y si tiene un archivo JavaScript abierto fuera del contexto de un proyecto, Visual Studio descargará los archivos JavaScript remotos a los que se hace referencia en el archivo con el fin de proporcionar la información de IntelliSense. Si se selecciona esta opción, los archivos se descargarán cuando se incluyan como referencia en el archivo JavaScript.  
  
> [!NOTE]
>  En los proyectos web, los archivos remotos a los que se hace referencia en el proyecto se descargan de forma predeterminada.  
  
## <a name="statement-completion"></a>Finalización de instrucciones  
 Puede utilizar estas opciones para cambiar el comportamiento de la finalización de instrucciones de IntelliSense.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Usar solo Tab o Entrar para confirmar**  
 Cuando se activa esta casilla, el editor de código JavaScript anexa las instrucciones con los elementos seleccionados a la lista de finalización únicamente después de elegir la tecla Tabulación o Entrar. Cuando esta casilla no está activada, otros caracteres, como un punto, coma, dos puntos, paréntesis de apertura y llave de apertura ({), también puede anexar instrucciones con los elementos seleccionados.  
  
## <a name="references"></a>Referencias  
 Puede utilizar estas opciones para especificar los tipos de archivos de IntelliSense .js que están incluidos en el ámbito para diferentes tipos de proyecto de JavaScript. Las referencias de IntelliSense se utilizan normalmente para proporcionar compatibilidad con IntelliSense a los objetos globales. También puede utilizar esta página para establecer el orden de carga de los scripts que se deben cargar en tiempo de ejecución y para agregar archivos de extensión de IntelliSense.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Grupos de referencias**  
 Esta opción especifica el tipo de grupo de referencias. Se admiten tres grupos de referencias:  
  
 Puede usar los grupos de referencias predefinidos para especificar qué archivos concretos de IntelliSense .js se incluyen en el ámbito para proyectos diferentes de JavaScript. Hay cuatro grupos de referencias disponibles:  
  
-   Implícito ( *versión*de Windows), para aplicaciones de la [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] que usan JavaScript. Los archivos incluidos en este grupo pertenecen al ámbito de cada archivo .js abierto en el editor de código para las aplicaciones de [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] que usan JavaScript.  
  
-   Implícito (Web), para proyectos HTML5. Los archivos incluidos en este grupo están en el ámbito de cada archivo .js abierto en el Editor de código para estos tipos de proyecto.  
  
-   Grupos de referencia de trabajo dedicado, para trabajos web de HTML5. Los archivos especificados en este grupo están en el ámbito para los archivos .js que tienen una referencia explícita a un grupo de referencia de trabajo dedicado.  
  
-   Genérico, para otros tipos de proyectos JavaScript.  
  
 **Archivos incluidos**  
 Esta opción especifica el orden en que los archivos se cargan en el contexto del servicio de lenguaje. Puede configurar el orden utilizando los botones **Quitar**, **Subir**y **Bajar** . Para que IntelliSense funcione correctamente, un archivo que depende de otro se debe cargar después del otro archivo.  
  
> [!CAUTION]
>  Si un objeto se define incondicionalmente en dos o más referencias implícitas, la última referencia de esta lista se utilizará para definir el objeto.  
  
 **Agregar una referencia al grupo**  
 Esta opción permite agregar archivos adicionales de IntelliSense .js buscando los archivos correspondientes.  
  
## <a name="see-also"></a>Vea también  
 [IntelliSense para JavaScript](../../ide/javascript-intellisense.md)



